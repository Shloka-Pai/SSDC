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
<!--CLASSES -->
<a id="classes"></a>
<h2>🔹 Classes</h2>

<p><strong>Class</strong> - blueprint / user-defined data-type.</p>

- For Understanding : think of class as a remote, and the buttons are functions.

```swift
class chai {
    var cups = 2

    func drink() {
        cups -= 1
    }
}

let myOrder = chai()
myOrder.drink()
print(myOrder.cups)

```
<p>Output</p>

```swift
1
```

---

<!--HStack, VStack & ZStack -->
<a id="stacks"></a>
<h2>🔹 HStack, VStack & ZStack</h2>

1. <strong>HStack</strong> - puts things side by side.

```swift
HStack {
    Text("Text 1")
    Text("Text 2")
    Text("Text 3")
}
```

<p>Output</p>

```swift
Text 1  Text 2  Text 3
```

2. <strong>VStack</strong> - stacks things top to bottom.

```swift
VStack {
    Text("Bread")
    Text("Cheese")
    Text("Bread")
}
```

<p>Output</p>

```swift
Bread
Cheese
Bread
```

3. <strong>ZStack</strong> - stacks things top to bottom.

```swift
ZStack {
    Text("Background")
    Text("Foreground")
}
```

<p>Output</p>

```swift
Foreground
---------
Background
```

---
