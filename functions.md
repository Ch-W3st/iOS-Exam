# Funtionen

```swift
var i = 0

// Kein Parameter, kein Rückgabewert
func increment() {
  i += 1
}

// Parameter, kein Rückgabewert
func increment(val: Int) {
  i += val
}

// 2 Parameter, Rückgabewert
func add(val1: Int, val2: Int) -> Int {
  return val1 + val2
}

// Argument label
func increment(by val: Int) {
  i += val
}
increment(by: 5)

// Mehrere Rückgabewerte
func multiply(by val: Int) -> (dbl: Int, half: Double) {
  return (val * 2, Double(val) * 0.5) 
}
let res = multiples(of: 5) 
let doubleVal = res.dbl
let halfVal = res.half 

// Default Parameterwerte
func multiples(of val: Int = 1) -> (dbl: Int, half: Double) {  
  return (val * 2, Double(val) * 0.5) 
} 

// Komplizierter Shit
func add(a: Int, b: Int) -> Int {  
  return a + b 
} 

func print(function: (Int, Int) -> Int, a: Int,   b: Int) { 
	print(function(a, b))  
} 

print(function: add, a: 2, b: 3) // -> 5

// Funktionen returnen
func getFunc(useAdd: Bool) -> (Int, Int) -> Int {  
  if useAdd { return add } 
  return mul 
}   
let mathFunc = getFunc(useAdd: true)  
let c = mathFunc(2, 3) // 2 + 3 = 5 
```
