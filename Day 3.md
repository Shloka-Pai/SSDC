<!-- TOP ANCHOR -->
<a id="day1-top"></a>

<!-- PROJECT HEADER -->

<div align="left">

  <h1>Day 2 - SwiftUI Fundamentals</h1>

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
  <li> <a href="#update">Make Dino Jump</a></li>
</ul>

---

<!-- Day 3 Code Updates -->
<a id="update"></a>
<h2>🔹 Day 2 Codes</h2>

<strong>📄 ContentView - Updated</strong>

```swift
import SwiftUI
import CoreGraphics

struct ContentView: View {

    // DAY 1 STATE (unchanged)
    @State private var groundX: CGFloat = 0

    //  DAY 2 NEW STATE (Dino)
    @State private var dinoY: CGFloat = 0        // Dino vertical position
    @State private var velocity: CGFloat = 0     // How fast Dino moves up/down
    @State private var isJumping: Bool = false   // Prevent double jump

    var body: some View {
        ZStack {

            // Background (same as Day 1)
            Image("background")
                .resizable()
                .scaledToFill()
                .ignoresSafeArea()

            VStack {
                Spacer()

                ZStack {
                    // 🦖 DINO (NEW)
                    Image("dino_run")
                        .resizable()
                        .scaledToFit()
                        .frame(width: 80, height: 80)
                        .offset(y: dinoY)                // Move Dino UP & DOWN

                    // Ground (same as Day 1)
                    BackgroundView(
                        image: "ground",
                        offsetX: groundX
                    )
                    .frame(height: 90)
                }
            }
        }
        // 🕒 GAME LOOP (same timer as Day 1)
        .onReceive(
            Timer.publish(every: 0.016, on: .main, in: .common).autoconnect()
        ) { _ in

            // 🌍 Ground movement (unchanged)
            groundX -= 6
            if groundX <= -UIScreen.main.bounds.width {
                groundX += UIScreen.main.bounds.width
            }

            // 🦖 DINO PHYSICS (NEW)
            velocity += 1.4                           // Gravity pulls Dino down
            dinoY += velocity                         // Apply movement

            // Stop Dino at ground level
            if dinoY > 0 {
                dinoY = 0
                velocity = 0
                isJumping = false
            }
        }
        // 👆 TAP TO JUMP (NEW)
        .onTapGesture {
            if !isJumping {
                velocity = -22                        // Jump force (upwards)
                isJumping = true
            }
        }
    }
}
```
