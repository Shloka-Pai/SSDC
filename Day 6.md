<!-- TOP ANCHOR -->
<a id="top"></a>

<!-- PROJECT HEADER -->

<div align="left">

  <h1>Day 6 - Dino Game Completed!!! </h1>

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
  <li> <a href="#update">Complete Your Dino Game</a></li>
</ul>

---

<!-- Day 6 Code Updates -->
<a id="update"></a>
<h2>🔹 Day 6 Codes</h2>

<strong>📄 SwiftDinoRunApp</strong>

```swift
import SwiftUI

@main
struct SwiftDinoRunApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

<strong>📄 GameAssets</strong>

```swift
struct GameAssets {
    
    // Dino
    static let runSheet = "dino_run_sheet"
    static let jumpSheet = "dino_jump_sheet"
    
    // Obstacle
    static let cactus = "cactus"   // single png
    
    // Environment
    static let background = "background"
    static let ground = "ground"
}
```

<strong>📄 GameViewModel</strong>

```swift
import SwiftUI

class GameViewModel: ObservableObject {
    
    // Dino
    @Published var dinoY: CGFloat = 0
    @Published var isJumping = false
    private var velocity: CGFloat = 0
    
    // Background
    @Published var bgX: CGFloat = 0
    @Published var groundX: CGFloat = 0
    
    // MARK: - Cactus (MULTIPLE)
    @Published var cactusXs: [CGFloat] = []
    
    // Game State
    @Published var score = 0
    @Published var gameOver = false
    @Published var hasStarted = false
    
    // Physics
    private let gravity: CGFloat = 1.4
    private let jumpForce: CGFloat = -22
    
    private let worldSpeed: CGFloat = 6
    
    // Cactus Config
    private let cactusWidth: CGFloat = 60
    private let minCactusGap: CGFloat = 210
    private let maxCactusGap: CGFloat = 600
    private let maxCactusOnScreen = 3
    
    // Timer
    let timer = Timer.publish(every: 0.016, on: .main, in: .common).autoconnect()
    
    // Update Loop
    func update() {
        guard hasStarted && !gameOver else { return }
        
        // Dino physics
        velocity += gravity
        dinoY += velocity
        
        if dinoY > 0 {
            dinoY = 0
            velocity = 0
            isJumping = false
        }
        
        let speedMultiplier = 1 + CGFloat(score) * 0.05
        
        // Background
        bgX -= worldSpeed * speedMultiplier
        if bgX <= -UIScreen.main.bounds.width {
            bgX += UIScreen.main.bounds.width
        }
        
        // Ground
        groundX -= worldSpeed * speedMultiplier
        if groundX <= -UIScreen.main.bounds.width {
            groundX += UIScreen.main.bounds.width
        }
        
        // Move existing cactus
        for i in cactusXs.indices {
            cactusXs[i] -= 7 * speedMultiplier
        }
        
        // Remove cactus that fully left screen
        cactusXs.removeAll { $0 < -cactusWidth * 10 }
        
        // Spawn new cactus BEFORE old leaves screen
        if cactusXs.count < maxCactusOnScreen {
            if cactusXs.isEmpty ||
                cactusXs.last! < UIScreen.main.bounds.width - randomCactusGap() {
                
                cactusXs.append(UIScreen.main.bounds.width + cactusWidth)
                score += 1
            }
        }
        
        // Collision
        for cactusX in cactusXs {
            if cactusX < -110 && cactusX > -150 && dinoY > -30 {
                gameOver = true
                SoundManager.shared.play("hit")
            }
        }
    }
    
    // Jump
    func jump() {
        if !hasStarted {
            hasStarted = true
            cactusXs = [UIScreen.main.bounds.width + 150]
        }
        
        if !isJumping && !gameOver {
            velocity = jumpForce
            isJumping = true
            SoundManager.shared.play("jump")
        }
    }
    
    // Reset
    func reset() {
        dinoY = 0
        velocity = 0
        cactusXs.removeAll()
        score = 0
        gameOver = false
        hasStarted = false
    }
    
    // Random Cactus Spawn Helper
    private func randomCactusGap() -> CGFloat {
        CGFloat.random(in: minCactusGap...maxCactusGap)
    }
}
```


<strong>📄 ContentView</strong>

```swift
import SwiftUI

struct ContentView: View {
    
    @StateObject private var game = GameViewModel()
    
    var body: some View {
        ZStack {
            
            BackgroundView(image: GameAssets.background, offsetX: game.bgX)
                .ignoresSafeArea()
            
            VStack {
                
                Text("Score: \(game.score)")
                    .font(.title)
                    .fontWeight(.bold)
                    .padding()
                
                Spacer()
                
                ZStack {
                    DinoView(isJumping: game.isJumping)
                        .offset(x: -120, y: game.dinoY)
                    
                    ForEach(game.cactusXs, id: \.self) { x in
                        CactusView(x: x)
                    }
                }
                
                BackgroundView(image: GameAssets.ground, offsetX: game.groundX)
                    .frame(height: 90)
            }
            
            if !game.hasStarted {
                Text("Tap to Start")
                    .font(.largeTitle)
                    .fontWeight(.bold)
            }
            
            if game.gameOver {
                VStack(spacing: 20) {
                    Text("Game Over")
                        .font(.largeTitle)
                        .fontWeight(.bold)
                    
                    Button("Restart") {
                        game.reset()
                    }
                    .padding()
                    .background(Color.black)
                    .foregroundColor(.white)
                    .cornerRadius(12)
                }
            }
        }
        .onTapGesture {
            game.jump()
        }
        .onReceive(game.timer) { _ in
            game.update()
        }
    }
}
```

<strong>📄 BackgroundView</strong>

```swift
import SwiftUI

struct BackgroundView: View {
    
    let image: String
    let offsetX: CGFloat
    
    var body: some View {
        GeometryReader { geo in
            HStack(spacing: 0) {
                ForEach(0..<3) { _ in
                    Image(image)
                        .resizable()
                        .scaledToFill()
                        .frame(width: geo.size.width)
                }
            }
            .offset(x: offsetX)
        }
    }
}
```
<strong>📄 DinoView</strong>

```swift
import SwiftUI

struct DinoView: View {
    
    let isJumping: Bool
    
    var body: some View {
        if isJumping {
            SpriteSheetView(
                imageName: GameAssets.jumpSheet,
                columns: 4,
                rows: 1,
                frameSize: CGSize(width: 80, height: 80),
                frameIndex: 1,   // static jump pose
                speed: nil
            )
        } else {
            SpriteSheetView(
                imageName: GameAssets.runSheet,
                columns: 6,
                rows: 1,
                frameSize: CGSize(width: 80, height: 80),
                frameIndex: 0,
                speed: 0.12
            )
        }
    }
}
```

<strong>📄 CactusView</strong>

```swift
import SwiftUI

struct CactusView: View {
    
    let x: CGFloat
    
    var body: some View {
        Image(GameAssets.cactus)
            .resizable()
            .scaledToFit()
            .frame(width: 60, height: 80)   // tweak if needed
            .offset(x: x, y: 10)            // aligns to ground
    }
}
```

<strong>📄 CactusView</strong>

```swift
import SwiftUI

struct CactusView: View {
    
    let x: CGFloat
    
    var body: some View {
        Image(GameAssets.cactus)
            .resizable()
            .scaledToFit()
            .frame(width: 60, height: 80)   // tweak if needed
            .offset(x: x, y: 10)            // aligns to ground
    }
}
```


<p align="right"><a href="#top">back to top</a></p>
