# Collections 
- [Array](#array)
- [Dictionary](#dictionary)
- [Tupel](#tupel)
- [Enums](#enums)
- [Suchen in Collections](#suchen-in-collections)

## Array
```swift
// append 
names.append("Anna")
names += ["Tim"] 

// insert 
names.insert("Sven", at: 2)   

// remove 
names.remove(at: 0)  names.removeLast() 
 
// replace 
names[1] = "Isabelle"  names[2...3] = ["Lukas", "Simone"]

// iterate 
for name in names {  
  print(name) 
}   
for (i, name) in names.enumerated() {  
  print("Item \(i) is \(name)") 
} 

// initialize empty array 
var arr = [String]()

// sort 
names.sort { (s1, s2) -> Bool in 
  s1 < s2  
} 
        
// map 
let lengthes = names.map { (name) -> Int in 
  name.count  
} 
```

## Dictionary
```swift
var airports = ["TXL": "Tegel", "SFX": "Schönefeld"] 

// access 
if let airportName = airports["TXL"] { // airports["TXL"] ist ein Optional vom Typ String?
  print("TXL is \(airportName)") 
}

let potentialName = airports["AFX", default: "unknown"] // -> unknown

// add 
airports["LHR"] = "London"

// remove
airports["LHR"] = nil 

// iterate 
for (airportCode, airportName) in airports {  
  print("\(airportCode): \(airportName)") 
}

// create arrays 
let airportCodes = [String](airports.keys) 

// initialize empty dictionary 
var namesOfIntegers = [Int: String]()

// create from arrays 
let colorKeys = ["red", "green", "blue"]
let argbValues = [0xffff0000, 0xff00ff00, 0xff0000ff]
 
let tuples = zip(colorKeys, argbValues)
let colorDict = Dictionary(uniqueKeysWithValues: tuples)
```

## Tupel
```swift
let tupel = (1, '404')
let number = tupel.0
let string = tupel.1
let (i, x) = tupel // i = 1, x = '404'
let (i, _) = tupel // i = 1

// or

let tupel = (num: 404, name: 'Not Found')
let number = tupel.num
let string = tupel.name
```

## Enums
* Type Inference
* Verschiedene Typen möglich (auch Tupel)
* Mit Switch abfragen
```swift
enum CompassPoint {
    case North, South, East, West
}

var direction = CompassPoint.South

if direction == .South {
    print("Watch out for penguins!")
}
```

## Suchen in Collections
```swift
let index = arr.index(of: “Anna")  // -> Optional Int
if let _index = index { 
    print("Anna found at index \(_index)")  
} 
``` 
