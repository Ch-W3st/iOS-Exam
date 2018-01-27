## Strong & Weak References Basics (not relevant)

weak references - work only for optionals (weak var (no `const` allowed!))
strong references - set by default (used from parent to child (linear hierarchy))

## Optional Chaining

Def.: chains of things which all can be nil

### Accessing Properties
**check if a property could be set**
```swift
if (john.residence?.address = someAddress) != nil {  
print("Address has been set.") 
} else { 
print("Address has not been set.") 
}
```

### Calling Methods
**call a method on an instance returns an optional**
```swift
John.residence = Residence()   
if john.residence?.printNumberOfRooms() != nil {  
print("Number of rooms printed.") 
} else { 
print("Number of rooms not printed.") 
}
```

### Chaining
**more „?“ in a chain**
```swift
if let street = john.residence?.address?.street {  
print("John's street name is \(street).") 
} else { 
print("Unable to retrieve the street.") 
}
```
## Class Extensions

extend classes without derive using:
* protocols
* computed properties
* initializers
* methods

### Syntax

```swift
extension SomeType { 
// new functionality to add to SomeType 
}   
```
#### Protocols

```swift
extension SomeType: SomeProtocol, AnotherProtocol {  
// implementation of protocol requirements 
}
```
#### Computed properties

```swift
extension Double {  
var mm: Double { return self / 1_000.0 }
} 
let oneInch = 25.4.mm
```

#### Initializers (convenience only)

```swift
class Square {  
var size = 0.0 
init(size: Double) {  
self.size = size 
} 
var area: Double { return size * size }  } 
extension Square { 
  convenience init(area: Double) { 
self.init(size: sqrt(area))  } 
} 
```

#### Methods

```swift
extension Int { 
  func repetitions(task: () -> ()) { 
    for _ in 0..<self {  task() 
    }  
  } 
}   
3.repetitions { print("Hello!") }
```





