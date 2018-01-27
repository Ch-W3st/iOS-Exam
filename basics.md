# Basics

## Types

Value Types:
* Int, Float, Double
* Bool
* String, Character
* Collections: Array, Dictionary, Set
* Structures, Enumerations

Reference Types:
* Class

## Konstanten und Variablen

Swift ist stark typisiert, jede Variable/Konstante hat einen festen Typ, der bei der Definition festgelegt wird.

`let` ist eine Konstante, `var` ist eine Variable

**Type Inference:**
Typ ergibt sich aus dem Kontext: `let i = 42`


**Type Annotation:** 
Typ wird explizit angegeben: `let i: String`

### Casten
Explizite Konvertierung durch <Typ>(<Typ>)

```swift
let i = 2
let d = 2.0 

let d2 = Double(i) // -> 2.0
let i2 = Int(d) // -> 2

let di = d + i // -> Error, Int und Double nicht verrechenbar
```

## Loops
Closed range
```swift
for i in 1...5 {
  print(i) // 1, 2, 3, 4, 5
}
```
Half open range
```swift
for i in 1..<5 {
  print(i) // 1, 2, 3, 4
}
```
One sided range
```swift 
for i in 1... {
  print(i)
  if i < 4 {break}
}
```

## Overflow
Überlauf führt zu Fehler
```swift
let cannot: UInt = -1 // compile time error  

var i: UInt8 = UInt8.max 
i += 1 // runtime error 
``` 

**Operators:**
&+ &- &\*
var i = UInt8.max // 255 
i = i &+ 1 // i wird 0

## Strings
String Methoden: 
```swift
append
```
```swift
insert("x", at: welcome.endIndex)
```
```swift
insert(contentsOf: " hey" at: welcome.index(before: welcome.endIndex))
```

```swift
s3.hasPrefix("hello)
s3.hasSuffix("ing")
```

String interpolation `\()`


### Substring
Not a string, just a reference to part of a different string. Can be converted into a string 
```swift
let greeting = "Hello, world!"
let index = greeting.index(of: ",") ?? greeting.endIndex 
let beginning = greeting[..<index] // Substring "Hello"
```

