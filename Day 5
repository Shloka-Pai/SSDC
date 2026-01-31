<!-- TOP ANCHOR -->
<a id="top"></a>

<!-- PROJECT HEADER -->

<div align="left">

  <h1>Day 5 - More Closer to the App </h1>

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
  <li> <a href="#update">Restart Button and Difficulty Level</a></li>
</ul>

---

<!-- Day 5 Code Updates -->
<a id="update"></a>
<h2>🔹 Day 5 Codes</h2>

<strong>📄 ContentView - Updated</strong>

```swift
import SwiftUI
import CoreGraphics

struct ContentView: View {

    // DAY 1 STATE (Ground)
    @State private var groundX: CGFloat = 0
    
    // DAY 2 STATE (Dino)
    @State private var dinoY: CGFloat = 0
    @State private var velocity: CGFloat = 0
    @State private var isJumping: Bool = false
    
    // DAY 3 STATE (Cactus + Game)
    @State private var cactusX: CGFloat = UIScreen.main.bounds.width + 100
    @State private var gameOver: Bool = false
    
    // DAY 4 NEW STATE
    @State private var score: Int = 0          // Player score
    @State private var gameSpeed: CGFloat = 1  // Difficulty multiplier
    
    var body: some View {
        ZStack {
            
            // Background
            Image("background")
                .resizable()
                .scaledToFill()
                .ignoresSafeArea()
            
            VStack {
                // SCORE DISPLAY (NEW – DAY 4)
                Text("Score: \(score)")
                    .font(.title)
                    .fontWeight(.bold)
                    .padding(.top)
                
                Spacer()
                
                ZStack {
                    // Ground (BACK)
                    BackgroundView(
                        image: "ground",
                        offsetX: groundX
                    )
                    .frame(height: 110)
                    
                    // Cactus (MIDDLE)
                    Image("cactus")
                        .resizable()
                        .scaledToFit()
                        .frame(width: 60, height: 80)
                        .offset(x: cactusX, y: -60)
                    
                    // Dino (FRONT)
                    Image("dino_run")
                        .resizable()
                        .scaledToFit()
                        .frame(width: 100, height: 100)
                        .offset(y: dinoY - 55)
                }
            }
            
            // GAME OVER OVERLAY (UPDATED DAY 4)
            if gameOver {
                VStack(spacing: 16) {
                    Text("Game Over")
                        .font(.largeTitle)
                        .fontWeight(.bold)
                    
                    // RESTART BUTTON (NEW)
                    Button("Restart") {
                        restartGame()
                    }
                    .padding()
                    .background(Color.black)
                    .foregroundColor(.white)
                    .cornerRadius(8)
                }
            }
        }

        // GAME LOOP
        .onReceive(
            Timer.publish(every: 0.016, on: .main, in: .common).autoconnect()
        ) { _ in
            
            // Stop everything if game is over
            if gameOver { return }
            
            // Ground movement (UPDATED – speed scales)
            groundX -= 6 * gameSpeed
            if groundX <= -UIScreen.main.bounds.width {
                groundX += UIScreen.main.bounds.width
            }
            
            // Dino physics (unchanged from Day 2)
            velocity += 1.4
            dinoY += velocity
            
            if dinoY > 0 {
                dinoY = 0
                velocity = 0
                isJumping = false
            }
            
            // Cactus movement (UPDATED – speed scales)
            cactusX -= 7 * gameSpeed
            
            // Respawn cactus
            if cactusX < -190 {
                cactusX = UIScreen.main.bounds.width + 100
                
                // Increase score when cactus is avoided (NEW)
                score += 1
                
                // Increase difficulty every 5 points (NEW)
                if score % 5 == 0 {
                    gameSpeed += 0.2
                }
            }
            
            // COLLISION DETECTION (USING YOUR VALUES)
            if cactusX < 10 && cactusX > -20 && dinoY > -50 {
                gameOver = true
            }
        }
        
        // TAP TO JUMP
        .onTapGesture {
            if !isJumping && !gameOver {
                velocity = -22
                isJumping = true
            }
        }
    }
    
    // RESTART LOGIC (DAY 4 NEW)
    private func restartGame() {
        groundX = 0
        dinoY = 0
        velocity = 0
        cactusX = UIScreen.main.bounds.width + 100
        score = 0
        gameSpeed = 1
        gameOver = false
    }
}
```


<p align="right"><a href="#top">back to top</a></p>
