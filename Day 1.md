<!-- README TOP ANCHOR -->
<a id="day1-top"></a>

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
<h2>What You’ll Learn Today</h2>

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
<h2>🔹 Variables &amp; Constants</h2>

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
<a id="data-types"></a>
<h2>🔹 Data Types </h2>

1. <p><strong>Int</strong> - whole numbers (e.g., −10, 0, 42)</p>

```swift
var score: Int = 10
```

2. <p><strong>Float</strong> - decimal numbers (e.g., 3.14))</p>

```swift
var score: Float = 9.6
```

3. <p><strong>Double</strong> - decimal numbers but with more precision</p>

```swift
var score: Double = 6.9696969696
```

4. <p><strong>String</strong> - used to store text.</p>

```swift
var fact: String = "Samyak is a good teacher"
```

5. <p><strong>Bool</strong> - true or false</p>

```swift
var isUnderstood: Bool = true
```

6. <p><strong>Character</strong> - a single character</p>

```swift
var charr: Character = 'x'
```

7. <p><strong>Optional(?)</strong> - value can be present or nil (nil by default)</p>

```swift
var username: String?
print(username)
```

<p>Output</p>

```swift
nil
```

- Assign value later -

```swift
var username: String?
username = "Samyak"
print(username)
```

<p>Output</p>

```swift
Optional("Samyak")
```

- To remove the wrapping "Optional("Samyak")", use:

```swift
print(username!)
```

<p>Output</p>

```swift
Samyak
```

8. <p><strong>Arrays</strong> - stores an ordered list of values</p>

```swift
var fruits = ["Apple", "Banana", "Orange"]
print(fruits)
```

<p>Output</p>

```swift
["Apple", "Banana", "Orange"]
```

- Accessing a value using index

```swift
print(fruits[0])
```

<p>Output</p>

```swift
Apple
```

9. <p><strong>Dictionary</strong> - stores key–value pairs.</p>

```swift
var scores = ["Alex": 90, "Sam": 85, "John": 88]
print(scores)
```

<p>Output</p>

```swift
["Alex": 90, "Sam": 85, "John": 88]
```

- Accessing a value using a key

```swift
print(scores["Alex"]!)
```

<p>Output</p>

```swift
90
```

10. <p><strong>Set</strong> - stores unique values (no duplicates)</p>

```swift
var numbers: Set<Int> = [1, 2, 3, 3, 4]
print(numbers)
```

<p>Output</p>

```swift
[1, 2, 3, 4]
```

<p>Duplicate values (3) are automatically removed.</p>

---

<!-- IF ELSE STATEMENTS -->
<a id="if-else"></a>
<h3>🔹 If–Else Statements</h3>

<p><strong>If–Else</strong> is used to make decisions based on a condition.</p>

```swift
let isUnderstood = false

if isUnderstood == true {
    print("Samyak is a good teacher!")
}
else {
    print("Shloka is a bad teacher!")
}
```

Output

```swift
Shloka is a bad teacher!
```

- <strong>If–Else with else if</strong>

```swift
let age = 19

if age >= 25 {
    print("we can drink!")
}
else if age >= 21 {
    print("we can drink but only mild drinks!")
}
else{
    print("We cannot, but we still!")
}
```

Output

```swift
We cannot, but we still!
```

---

<!-- FOR LOOP -->
<a id="for-loops"></a>
<h3>🔹 For Loop</h3>

<p><strong>For loop</strong> is used when we want to repeat something a fixed number of times.</p>

```swift
for day in 1...5 {
    print("Day \(day): I will start coding seriously today 😤")
}
```

Output

```swift
Day 1: I will start coding seriously today 😤
Day 2: I will start coding seriously today 😤
Day 3: I will start coding seriously today 😤
Day 4: I will start coding seriously today 😤
Day 5: I will start coding seriously today 😤
```

---

<!-- WHILE LOOP -->
<a id="while-loops"></a>
<h3>🔹 While Loop (Fun Example 😄)</h3>

<p><strong>While loop</strong> keeps running as long as a condition is true.</p>

```swift
var motivation = 5

while motivation > 0 {
    print("We are still motivated to code 😤")
    motivation = motivation - 1
}
```

Output
```swift
We are still motivated to code 😤
We are still motivated to code 😤
We are still motivated to code 😤
We are still motivated to code 😤
We are still motivated to code 😤
```

---

<!-- COMPARISON & LOGICAL OPERATORS -->
<a id="operators"></a>
<h3>🔹 Comparison & Logical Operators</h3>

- <p><strong>== (Equal to)</strong> – checks if two values are the same.</p>
- <p><strong> or < (Greater than or Less than)</strong> – checks if one value is bigger/smaller than another.</p>

```swift
let tuck_ki_chai = 2

if tuck_ki_chai == 2 {
    print("Perfect amount of chai ☕")
}
else if tuck_ki_chai < 2 {
    print("Moreeeeeeee")
}
else if tuck_ki_chai > 2 {
    print("Probably you are tired and you need it.")
}

```

Output
```swift
Perfect amount of chai ☕
```

- <p><strong>&& (AND)</strong> – both conditions must be true.</p>

```swift
let chai: Bool = false
let coffee: Bool = true

if chai==true && coffee==true {
    print("Not a great combo!")
}
else if chai==true && coffee==false {
    print("Good choice!")
}
else if chai==false && coffee==true {
    print("Bad Choice!")
}
```

Output
```swift
Bad Choice!
```

- <p><strong>|| (OR)</strong> – at least one condition must be true.</p>

```swift
let understood: Bool = false
let notUnderstood: Bool = true

if understood || notUnderstood {
    print("Samyak is a good teacher!")
}
```

Output
```swift
Samyak is a good teacher!
```
  
<p align="right"><a href="#day1-top">back to top</a></p>

