# Structs and Classes Lab - 2


## Question 1

Using the Room struct below, write code that demonstrates that it is a value type.

```swift
struct Room {
     let maxOccupancy: Int
     let length: Double
     let width: Double
}

var room1 = Room(maxOccupancy: 25, length: 200, width: 200)
print(room1)
If this was a reference type, the above code would print something like "__lldb_expr_(a number).Room", but because it is a value type, it prints out the values of the parameters of room1 instead.
```

## Question 2

Using the Bike class below, write code that demonstrates that it is a reference type.

```swift
class Bike {
    var wheelNumber = 2
    var hasBell = false
}

print(bike1)
If this was a value type, it would print out the values of the parameters of bike2, but because it is a reference type, it prints out the location of the information it is referencing instead. (__lldb_expr_1.Bike)


```

## Question 3

a. Given the Animal class below, create a Bird subclass with a new `canFly` property.

```swift
class Animal {
    var name: String = ""
    var printDescription() {
        print("I am an animal named \(name)")
    }
}
answer on B
```

b. Override the printDescription method to have the instance of the Bird object print out its name and whether it can fly
```
class Animal {
var name: String = ""
func printDescription() {
print("I am an animal named \(name)")
}
}
class Bird: Animal {
var canFly: Bool
init(canFly:Bool) {
self.canFly = canFly
}
override func printDescription() {
if canFly == true {
print("I am a bird named \(name), and I can fly!")
} else {
print("I am a bird named \(name), and I can't fly. :(")
}
}
}
```
## Question 4

```swift
class Bike {
  let wheelNumber = 2
  let wheelWidth = 1.3
  var hasBell = true
  func ringBell() {
    if hasBell {
      print("Ring!")
    }
  }
}
```


a. Create a `LoudBike` subclass of Bike.  When you call `ringBell` it should ring the bell in all caps.

b. Give `LoudBike` a new method called `ringBell(times:)` that rings the bell a given number of times

```
class Bike {
let wheelNumber = 2
let wheelWidth = 1.3
var hasBell = true
func ringBell() {
if hasBell {
print("Ring!")
}
}
}
class LoudBike: Bike {
override func ringBell() {
if hasBell {
print("RING!!!")
}
}
func ringBellWhateverTimes(numberOfRings: Int) {
for _ in 1...numberOfRings {
print("RING!!!")
}
}
}
var bike3 = LoudBike()
bike3.ringBellWhateverTimes(numberOfRings: 5)
Collapse




Message Input
```
## Question 5

```swift
class Shape {
    var name: String { return "This is a generic shape" }
    var area: Double { fatalError("Subclasses must override the area") }
    var perimeter: Double { fatalError("Subclasses must override the perimeter") }
}
```

a. Given the `Shape` object above, create a subclass `Square` with a property `sideLength` with a default value of 5.

b. Override the `area` and `perimeter` computed values so the return the area/perimeter of the square as appropriate

c. Override the `name` property of `Square` so that it returns a String containing its name ("Square") and its area and perimeter

d. Create a class `Rectangle` that subclasses from `Shape`.  Give it a `width` property with a default value of 6 and a `height` property with a default value of 4

e. Override the `name` property of `Rectangle` so that it returns a String containing its name ("Rectangle") and its area and perimeter.
```
class Shape {
var name: String { return "This is a generic shape" }
var area: Double { fatalError("Subclasses must override the area") }
var perimeter: Double { fatalError("Subclasses must override the perimeter") }
}
class Square: Shape {
var sideLength:Double = 5.0

override var area: Double {
return Double(sideLength * sideLength)
}
override var perimeter: Double {
return Double(sideLength * 4)
}
override var name: String {
return String("Name: \(self) | Perimeter: \(perimeter) | Area: \(area)")
}
}
class Rectangle: Shape {
var width = 6
var height = 4

override var area: Double {
return Double(width * height)
}
override var perimeter: Double {
return Double((width + height) * 2)
}
override var name: String {
return String("Name: \(self) | Perimeter: \(perimeter) | Area: \(area)")
}
```
f. (BONUS) What happens when you run the code below?  Explain why.

```swift
var myShapes = [Shape]()

myShapes.append(Square())
myShapes.append(Rectangle())

for shape in myShapes {
    print("This is a \(shape.name) with an area of \(shape.area) and a perimeter of \(shape.perimeter)")
}
```

## Question 6

a. Given the Point object below, complete the `distance` method so that it returns the distance between a given point.

The equation for the distance formula can be found [here](https://www.mathsisfun.com/algebra/distance-2-points.html) and is give by:

```swift
let horizontalDistance = pointOneXValue - pointTwoXValue
let verticalDistance = pointOneYValue - pointTwoYValue
let distanceBetweenTwoPoints = sqrt(horizontalDistance * horizontalDistance + verticalDistance * verticalDistance)
```

`sqrt` is a method in Swift that gives the square root.  Make sure to have `import Foundation` or `import UIKit` to use this method.

```swift
struct Point {
    let x: Double
    let y: Double
    func distance(to point: Point) -> Double {
      //Code in your answer here
    }
}

let pointOne = Point(x: 0, y: 0)
let pointTwo = Point(x: 10, y: 10)

print(pointOne.distance(to: pointTwo)) //Prints 14.142135623730951
```


b. Given the above Point object, and Circle object below, add a `contains` method that returns whether or not a given point is on the circle

```swift
struct Circle {
    let radius: Double
    let center: Point
}

let pointOne = Point(x: 0, y: 0)
let circleOne = Circle(radius: 5, center: pointOne)
let pointTwo = Point(x: 5, y: 0)
let pointThree = Point(x: 4, y: 0)
let pointFour = Point(x: sqrt(12.5), y: sqrt(12.5))
circleOne.contains(pointTwo) //true
circleOne.contains(pointThree) // false
circleOne.contains(pointFour) //true
```

c. Add another method to `Circle` that returns a random point on the circle

Hint: Given the radius of a circle and the x value of a point on the circle, the y value of the point is defined by:

```
√(r^2) - (x^2)
```

```swift
circleOne.contains(circleOne.getRandomPoint()) //Should always be true
```


## Question 7

a. Create a struct called HangmanModel with 3 properties `targetWord: String`, `numberOfIncorrectGuesses: Int` and `guessedLetters: [Character]`.

b. Add a method called `playerWon` that returns whether all of the characters in `targetWord` are in `guessedLetters`

```swift
var model = HangmanModel()
model.targetWord = "hello"
model.guessedLetters = ["h","e","o","l"]
model.playerWon //true
```

c. Add a method called `printDisplayVersionOfWord` that prints the `targetWord` replacing characters that are not in `guessedLetters` with "\_"

```
var model = HangmanModel()
model.targetWord = "hello"
model.guessedLetters = ["h","l"]
model.printDisplayVersionOfWord
//prints h_ll_
```

d. Add a method called `guess(_:)` that takes in a character as input, and updates `guessedLetters` and `numberOfIncorrectGuesses` as appropriate.

```swift
var model = HangmanModel()
model.targetWord = "hello"
model.guess("h")
model.guess("a")
model.guessedLetters // ["h", "a"]
model.numberOfIncorrectGuesses // 1
```

e. Have `guess(_:)` also print out the current display version of the word, the number of incorrect guesses and if the player has won.
