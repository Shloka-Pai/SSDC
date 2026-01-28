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
  <li> <a href="#functions">Functions</a></li>
  <li> <a href="#classes">Classes</a></li>
  <li> <a href="#stacks">HStack, VStack & ZStack </a></li>
  <li> <a href="#code">Day 2 Codes</a></li>
</ul>

---
<!-- FUNCTIONS -->
<a id="functions"></a>
<h2>🔹 Functions</h2>

<p>A <strong>Function is an action</strong> - something that does work.</p>

```swift
func jump() {
    print("Dino Jumped")
}

jump()
```
<p>Output</p>

```swift
Dino Jumped
```

- You give the function some input, <br>
it does work, <br>
and gives you output.

- There are two ways of passing inputs - Named Arguments & Positional Arguments. <br><br>
  <strong>1. Named Arguemnts </strong>
  ```swift
  func printInfo(name: String, age: Int){
    print("My name is \(name) and my age is \(age).")
  }

  printInfo(name: "Samyak", age: 20)
  ```

  Output
  
  ```swift
  My name is Samyak and my age is 20.
  ```

  <strong>2. Positional Arguemnts </strong>
  ```swift
  func printInfo(_ name: String, _ age: Int){
    print("My name is \(name) and my age is \(age).")
  }

  printInfo("Samyak", 20)
  ```

  Output
  
  ```swift
  My name is Samyak and my age is 20.
  ```

---
