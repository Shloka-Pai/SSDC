<!-- README TOP ANCHOR -->
<a id="readme-top"></a>

<!-- PROJECT HEADER -->

<div align="left">

  <h1>Day 1 - Swift Fundamentals</h1>

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
<h2>🎯 What You’ll Learn Today</h2>

<ul>
  <li> <a href="#variables-constants">Variables & Constants</a></li>
  <li> <a href="#data-types">Data Types in Swift</a></li>
  <li> <a href="#if-else">If–Else Conditions</a></li>
  <li> <a href="#for-loops">For Loops</a></li>
  <li> <a href="#while-loops">While Loops</a></li>
  <li> <a href="#operators">Comparison &amp; Logical Operators</a></li>
</ul>


---

<!-- VARIABLES & CONSTANTS -->
<a id="variables-constants"></a>
<h3>🔹 Variables &amp; Constants</h3>

<p><strong>Variables</strong> - store values that can change.</p>

```swift
var score = 10
score = 20
print(score)
```
<p>Output</p>

```swift
20
```

<p><strong>Constants</strong> - store values that do not change.</p>

```swift
let score = 10
score = 20
print(score)
```

<p>Output</p>

```swift
10
```

---

<!-- DATA TYPES -->
<a id="variables-constants"></a>
<h3>🔹 Data Types </h3>

<p><strong>Int</strong> - whole numbers (e.g., −10, 0, 42)</p>

```swift
var score: Int = 10
```

<p><strong>Float</strong> - decimal numbers (e.g., 3.14))</p>

```swift
var score: Float = 9.6
```

<p><strong>Double</strong> - decimal numbers but with more precision</p>

```swift
var score: Double = 6.9696969696
```

<p><strong>String</strong> - whole numbers (e.g., −10, 0, 42)</p>

```swift
var score: String = "Samyak is a good teacher"
```

<p><strong>Bool</strong> - true or false</p>

```swift
var isGood: Bool = false
```

<p><strong>Character</strong> - a single character</p>

```swift
var score: Character = 'x'
```

<p><strong>Optional(?)</strong> - value can be present or nil</p>

```swift
var username: String?
print(username)
```

<p>Output</p>

```swift
nil
```

```swift
var username: String?
username = "Samyak"
print(username)
```

<p>Output</p>

```swift
Optional("Samyak")
```

<p>To remove the wrapping "Optional("Samyak")", use:</p>

```swift
print(username!)
```

<p>Output</p>

```swift
Samyak
```
  
<p align="right">(<a href="readme-top">back to top</a>)</p>

