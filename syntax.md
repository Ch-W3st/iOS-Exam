# Syntax

- [Syntax](#syntax)
  - [Basics](#basics)
    - [Print](#print)
    - [String concatenation](#string-concatenation)
  - [Switch](#switch)
  - [Optionals](#optionals)
    - [Optional Binding](#optional-binding)
    - [Implicitly Unwrapped Optionals](#implicitly-unwrapped-optionals)
    - [Nil-Coalescing Operator](#nil-coalescing-operator)

## Basics

### Print

```swift
print("hello, wolrd!")
```

### String concatenation

```swift
let str = "\(variable_a) is not \(variable_b)"
```

## Switch
* Keine Breaks
* Mehrere Cases durch Komma getrennt
* Viele Typen möglich
* Kein Fall-Through
* Muss exhaustive sein = *alle* Fälle abdecken (deswegen default)

```swift
let name = "Hans" 
switch name { 
  case "Hans", "Hänschen": 
  print("congratulations")  default: 
  print("sorry")  
}
```

Value Binding:
```swift
let anotherPoint = (2, 0)  
switch anotherPoint {  
  case (let x, 0): 
    print("on the x-axis with x = \(x)")  
  case (0, let y): 
    print("on the y-axis with y = \(y)")  
  case let (x, y): 
    print("somewhere else at (\(x), \(y))")  `
}
```

Conditional
```swift
let yetAnotherPoint = (1, -1)  
switch yetAnotherPoint { 
  case let (x, y) where x == y: 
    print("(\(x), \(y)) is on the line x == y")  
  case let (x, y) where x == -y: 
    print("(\(x), \(y)) is on the line x == -y")  
  case let (x, y): 
    print("(\(x), \(y)) is just some other point")  
}
```



## Optionals
Jeder Typ kann auch optional sein. Optional bedeutet, die Variable **hat** einen Wert, oder sie **hat** keinen Wert. Jeder Typ kann auch optional sein.

```swift
let possible: String? = "Hello"  // -> optionOptional<String>
```


### Optional Binding
```swift
// best practice
if let actual = possible { 
  print(actual)  
}
```

**Example:**
```swift
let inputLine = readLine() // -> String? 
 
let input1 = "3.14" 
let value1 = Double(input1) // -> Double? w/ value 3.14   
let input2 = "3x14" 
let value2 = Double(input2) // -> Double? w/ value nil 
```

### Implicitly Unwrapped Optionals
Wenn man davon ausgehen kann, dass der optional nicht `nil` ist, sondern einen Wert hat, kann man ihn auch **implicitly unwrappen**
```swift
if possible != nil { 
  let forced: String = possible! // -> String

  let assumed: String! = possible // -> ImplicitlyUnwrappedOptional<String> 
  let implicit: String = assumed // -> String
}
```
Wenn ein implicitly unwrapped optional `nil` ist, wirft es einen Runtime Error

### Nil-Coalescing Operator

Der `??` ist eine wenn dann Abfrage um optionals zu unwrappen, wenn nicht nil. 
Beispielsweise ist `??` das selbe wie `a != nil ? a! : b`

```swift
let defaultColorName = "red" 
var userColorName: String? // defaults to nil 
 
var colorNameToUse = userColorName ?? defaultColorName  // colorNameToUse is set to "red" 
```


