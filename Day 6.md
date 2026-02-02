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


<p align="right"><a href="#top">back to top</a></p>
