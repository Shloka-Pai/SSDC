<!-- TOP ANCHOR -->
<a id="top"></a>

<!-- PROJECT HEADER -->

<div align="left">

  <h1>Day 4 - Cactus and Collision Detecion</h1>

  <p align="left">
    Learn Swift from scratch and build real iOS apps and games using SwiftUI.
    <br />
    A beginner-friendly, hands-on learning journey designed for students and developers.
    <br />
    <br />
    <strong>From zero Swift knowledge → fully functional app 🚀</strong>
  </p>

</div>

---

<!-- CONTENT -->
<h2>What You’ll Learn Today</h2>

<ul>
  <li> <a href="#update">Add Cactus & Collision Detection</a></li>
</ul>

---

<!-- Day 3 Code Updates -->
<a id="update"></a>
<h2>🔹 Day 4 Codes</h2>

<strong>📄 ContentView - Updated</strong>

```swift
import SwiftUI
import CoreGraphics

struct ContentView: View {
    
    // DAY 1 STATE
    @State private var groundX: CGFloat = 0
    
    // DAY 2 STATE (Dino)
    @State private var dinoY: CGFloat = 0
    @State private var velocity: CGFloat = 0
    @State private var isJumping: Bool = false
    
    // DAY 3 NEW STATE (Cactus + Game)
    @State private var cactusX: CGFloat = UIScreen.main.bounds.width + 100
    @State private var gameOver: Bool = false
    
    var body: some View {
        ZStack {
            
            // Background
            Image("background")
                .resizable()
                .scaledToFill()
                .ignoresSafeArea()
            
            VStack {
                Spacer()
                
                ZStack {
                    // Ground FIRST (back)
                    BackgroundView(
                        image: "ground",
                        offsetX: groundX
                    )
                    .frame(height: 110)
                    
                    // Cactus (middle)
                    Image("cactus")
                        .resizable()
                        .scaledToFit()
                        .frame(width: 60, height: 80)
                        .offset(x: cactusX, y: -60)
                    
                    // Dino LAST (front)
                    Image("dino_run")
                        .resizable()
                        .scaledToFit()
                        .frame(width: 100, height: 100)
                        .offset(y: dinoY-55)
                }
            }
            
            // GAME OVER TEXT (NEW)
            if gameOver {
                Text("Game Over")
                    .font(.largeTitle)
                    .fontWeight(.bold)
            }
        }
        
        // GAME LOOP
        .onReceive(
            Timer.publish(every: 0.016, on: .main, in: .common).autoconnect()
        ) { _ in
            // Stop everything if game is over
            if gameOver { return }
            
            // Ground movement (same as Day 1)
            groundX -= 6
            if groundX <= -UIScreen.main.bounds.width {
                groundX += UIScreen.main.bounds.width
            }
            
            // Dino physics (same as Day 2)
            velocity += 1.4
            dinoY += velocity
            
            if dinoY > 0 {
                dinoY = 0
                velocity = 0
                isJumping = false
            }
            
            // Cactus movement (NEW)
            cactusX -= 7
            
            // Respawn cactus after it leaves screen
            if cactusX < -300 {
                cactusX = UIScreen.main.bounds.width + 100
            }
            
            // COLLISION DETECTION (NEW)
            if cactusX < 20 && cactusX > -20 && dinoY > -30 {
                gameOver = true
            }
        }
        // TAP TO JUMP (same as Day 2)
        .onTapGesture {
            if !isJumping && !gameOver {
                velocity = -22
                isJumping = true
            }
        }
    }
}
```


<p align="right"><a href="#top">back to top</a></p>
