# Closures

Closures kapseln ein Stück Source Code zum wiederverwenden. Sie können als Parameter an Methoden übergeben werden und müssen keinen Namen haben. 

### Aufbau:
```swift
{ ( <parameters> ) -> <return type> in 
  <statements>  
}
```

### Beispiel Array sortieren:
```swift
var names = ["Hans", "Anna", "Tom", "Susanne"]   

names.sort(by: { (s1: String, s2: String) -> Bool in 
  return s1 < s2 
}) 
```

### Inferring Type from Context:
Parameter muss nicht angegeben werden
```swift
names.sort(by: { s1, s2 in return s1 < s2 } ) 
```
Der Typ der Closure `(String, String) -> Bool` muss nicht angegeben werden, weil er sich aus dem Typ des Parameters von `sort()` ergibt.

### Implicit Return
Falls die Closure nur aus einem return statement besteht, kann man das `return` auch weglassen
```swift
names.sort(by: { s1, s2 in s1 < s2 } ) 
```

### Shorthand Argument Names
Swift kann mit `$` auch automatisch Namen zuweisen. So braucht man keine Parameterliste mehr.
```swift
names.sort(by: { s1, s2 in s1 < s2 } ) 
```

### Operator Functions
 „<“ ist der Name eines Operators vom Typ (String, String) -> Bool 
```swift
names.sort(by: <) 
```

### Trailing Closure
Falls die Closure sehr lang ist, kann }) irritieren. Deshalb kann die Closure, wenn sie das letzte Argument ist, auch dahinter geschrieben werden. Ist es das einzige Argument, kann `()`
```swift
names.sort { s1, s2 in 
  var isLess = false 
  // ... 
  return isLess 
} 
```
