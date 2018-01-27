- [Klassen](#klassen)
  - [Inheritance](#inheritance)
    - [Ableiten](#ableiten)
    - [Überladen](#%C3%BCberladen)
    - [Type Checking](#type-checking)
    - [Type Casting](#type-casting)
  - [Protocols](#protocols)
    - [Requirements](#requirements)
  - [Suchen in eigenen Klassen](#suchen-in-eigenen-klassen)
  - [Any](#any)
  - [Unwichtige Informationen](#unwichtige-informationen)
- [Structures](#structures)
  - [Klassen](#klassen)
    - [Inheritance](#inheritance)
      - [Ableiten](#ableiten)
      - [Überladen](#%C3%BCberladen)
      - [Type Checking](#type-checking)
      - [Type Casting](#type-casting)
    - [Protocols](#protocols)
      - [Requirements](#requirements)
    - [Suchen in eigenen Klassen](#suchen-in-eigenen-klassen)
    - [Any](#any)
    - [Unwichtige Informationen](#unwichtige-informationen)
  - [Structures](#structures)
- [Property Types](#property-types)
    - [Stored Property](#stored-property)
    - [Computed Properties](#computed-properties)
    - [Property Observers](#property-observers)
    - [Static Properties](#static-properties)
  - [Methoden](#methoden)
  - [Subscripts](#subscripts)
  - [Initialization](#initialization)
    - [Default Wert](#default-wert)
    - [Automatischer Initializer](#automatischer-initializer)
    - [Definierter Initializer](#definierter-initializer)
    - [Optional Properties](#optional-properties)
    - [Failable Initializer](#failable-initializer)
    - [Deinitializer](#deinitializer)

## Klassen

```swift
class Vector { 
  var x = 0.0 
  var y = 0.0 
  init() { } 
  init(x: Double, y: Double) { 
    self.x = x 
    self.y = y  } 
  func inc(by amount: Int) { 
    x += amount  
  } 
}

let v1 = Vector() 
let v2 = Vector(x: 2, y: 3)
v2.inc(by: 2)
```

### Inheritance 
Nur für Klassen haben Inheritance, Structures und Enummerations nicht. 

```swift
// Basis Klasse
class Vehicle { 
  var curSpeed = 0.0  
  var description: String { 
    return "traveling at \(curSpeed) km/h"  
  } 
  func makeNoise() {  
    // ...
  }  
}
```
#### Ableiten
Beim ableiten können neue Methoden und Properties hinzugefügt werden
```swift
class Car: Vehicle {  
  var gear = 1 
  func accelerate(by amount: Double) {  
    curSpeed += amount 
  }  
} 
 
let car = Car()  
car.curSpeed = 25.0  
car.accelerate(by: 5.0)  
print(car.description) // -> traveling at 30.0 km/h
```
#### Überladen

Methoden und Properties überladen mit `override` und `super`. Ein Überladen lässt sich durch Deklaration mit dem Schlüsselwort `final` in der Basisklasse verhindern.

```swift
class Car: Vehicle {  
  var gear = 1 
  func accelerate(by amount: Double) {  
    curSpeed += amount 
  } 
  override func makeNoise() { 
    print("brrrrrr") 
  } 
  override var description: String { 
    return super.desc + " in gear \(gear)"  
  } 
}
```

#### Type Checking 
Type checking mit dem Schlüsselwort `is`

#### Type Casting
Type casting mit dem Schlüsselwort `as`

```swift
var vehi: Vehicle = Car()   

// compiler error: 
let car: Car = vehi 
 
// dangerous: 
let car: Car = vehi as! Car  
 
// run time error: 
let auto: AutomaticCar = vehi as! AutomaticCar   

// safe
if let auto = vehi as? AutomaticCar {  
  print("vehi is an automatic car") 
}
```

### Protocols
Definiert Anforderungen (Requirements) für Klassen, Strukturen oder Enumeration. Anforderungen an Properties, Methoden, Initializer.

```swift
protocol SomeProtocol { 
// protocol definition goes here 
}   
 

 class SomeClass: SomeSuperclass, FirstProtocol,   AnotherProtocol { 
// class definition goes here 
}
```

#### Requirements
1. Property Requirements: 
    Verlangen, dass eine Klasse eine Property mit Getter (und Setter) hat
2. Method Requirements: 
    Liste zu implementierender Methoden
3. Initializer Requirements:
    Einen Initializer verlangen - Schlüsselwort `required`

```swift
protocol Named { 
  // Initializer Requirements
  init(someParameter: Int) 

  // Property Requirements
  var lastName: String { get set }  
  var firstName: String { get set }  
  var name: String { get } 

  // Method Requirements
  func limit(val: Int) -> Int  
}
```
Eine Klasse, die die Anforderungen erfüllt
```swift
class Person: Named { 
  
  var lastName = ""  
  var firstName = ""  
  var name: String { 
    return firstName + " " + lastName  
  } 
  required init(someParameter: Int) { 
    // initializer implementation goes here 
  } 

  func limit(val: Int) -> Int {  
    if val < 0 { return0 } 
    if val > 255 { return 255 } 
      return val  
    } 
  class func globalLimit() -> Int {  
    return 255 
  } 
}   
```

### Suchen in eigenen Klassen
Zu suchende Objekte müssen das Protokoll Equatable unterstützen und die Funktion `func ==` implementieren.

### Any
Bezeichner für beliebe Objekt Typen 
```swift
var objects = [AnyObject]() 
```

Für Typen, die keine Objekte sind, einfach `[Any]`

### Unwichtige Informationen
Anwendungsbereiche:
* Module: Eine App oder ein Framework
* Source File: Eine einzelne Quellcode Datei

Rechte (unwichtig):
* **open & public:** Voller Zugriff überall
* **internal:** Voller Zugriff innerhalb eines Moduls, aber nicht aus anderen Modulen
* **fileprivate:** Zugriff nur innerhalb der Datei
* **private:** Zugriff nur im Bereich der Deklaration und derer Extensions (in der gleichen Datei)

Bsp: `private func something() {}`

**-> Default ist internal**


## Structures

```swift
struct Resolution {  
  var width = 0 
  var height = 0  
} 
   
let res = Resolution() 
var vga = Resolution(width: 640, height: 480) // Automatisch erzeugter Initializer 
```

Structure verweden, wenn:
* wenige, einfache Datenwerte
* datenwerte selbst Value Type sind
* keine Vererbung notwendig ist

Arrays, Dictionaries und Strings sind als Structure implementiert.

# Property Types

* Stored Property 
* Computed Property 

### Stored Property

```swift
class Vector {  
  var x = 0  
  var y = 0 
  let dimension = 2 
}   
```
In Swift gibt es keine „Instanzvariablen“. Diese sind Properties, die automatisch „Getter“ und „Setter“ erzeugen, die man mittels „Punkt-Notation“ aufruft, z.B. v.x = 42
```swift
var v = Vector() 

v.x = 42    // "Setter" 
let x = v.x // "Getter" 
```

### Computed Properties

```swift
class Vector { 
  var x = 0; var y = 0  
  var halfX: Int { // Dies ist keine Methode!
    get { 
      return x/2  
    } 
    set(newHalfX) { // Kurzschreibweise -> (newHalfX) weglassen
      x = 2 * newHalfX 
    }   
  } 
} 

let v = Vector()
v.halfX = 21 // "Setter“ 
print(v.x) // v.x is 42

```

### Property Observers
Ähnlich wie LifeCycle Methods. Die `willset` Methode hat `newValue` als defualt Parameter mit dem zu setzenden Wert. Genauso hat `didSet`den default Parameter `oldValue`

```swift
class Vector {  
  var x = 0 { 
    willSet { 
      print("About to change x to \(newValue)") 
    }  
    didSet { 
      if x > 100 {  
        x = 100 
      } 
      print("Changed x by dx = \(x - oldValue)")  } 
    } 
  var y = 0  
}

let v = Vector() 
v.x = 123 
print(v.x) // v.x is 100
```

### Static Properties
Eigenschaften, die über alle Objekte hinweg den selben Wert haben 

```swift
class Counter { 
  static var max = 100  
  var cnt: Int = 0 { 
    didSet { 
      if cnt > Counter.max { 
        cnt = Counter.max  
      } 
    }  
  } 
}   
Counter.max = 256  
let c = Counter()  
c.cnt = 300  
print(c.cnt) // -> 256
```

## Methoden 
Klassen, Strukturen und Enummerations können Methoden haben. Es gibt zwei Arten von Methoden: 
* **Instance methods:** der Normalfall, diese Methoden kennen wir schon
* **Type Methods:** wie static methods in Java. Werden deklariert durch  `class func` und können dann durch `ClassName.function()` aufgerufen werden.

```swift
class Vector { 
  var x = 0 
  var y = 0 
  class func maxDim() -> Int { 
    return 100  
  } 
}  

let abc = Vector.maxDim() 
```

## Subscripts
Ermöglicht es, durch `[]` auf ein Element zuzugreifen. Arrays haben diese FUnktionalität beispielsweise auch implementiert.

```swift
class ThreeTimes {  
  subscript(index: Int) -> Int { 
    return 3 * index  
  } 
}   
let mul = ThreeTimes()  
let a = mul[2] // a is 6  
let b = mul[7] // b is 21
```

## Initialization 
Das Ziel beim Initialisieren ist es, eine neue Instanz vorzubereiten. **Alle** Werte müssen initialisiert werden. Dies kann durch default Werte, oder den `init` umgesetzt werden. 

### Default Wert
```swift
class Celsius { 
  var temp = 20.0  
}
```

### Automatischer Initializer
Benötigt keine Parameter
```swift
class Celsius { 
  var temp: Double
  init() { 
    temp = 20.0  
  } 
}
```

### Definierter Initializer
Benötigt Prameter
```swift
class Celsius { 
  var temp = 20.0
  init(temp: Double) { 
    self.temp = temp 
  } 
}
let t = Celsius(temp: 20)
```

### Optional Properties
Kein Initializer nötig, da `nil` erlaubt
```swift
class Celsius { 
  var temp = 20.0
  var description: String?
  init(temp: Double) { 
    self.temp = temp 
  } 
  init(temp: Double, description: String) { 
    self.description = description 
  } 
}
let t = Celsius(temp: 20)
```

### Failable Initializer
Initializer können auch fehlschlagen. 

```swift
class Font { 
  var name = "" 
  init?(name: String, size: Float) { 
    if name == "Helvetica" || name == "Times" { 
      self.name = name  
    } 
    else { 
      return nil  
    } 
  } 
}   

if let font = Font(name: "Times", size: 12) {  
  print(font.name) 
}
```

### Deinitializer
Falls Aufräumarbeiten bei der Vernichtung der Instanz notwendig sind:

```swift
class Font { 
  init () { 
    // ...
  } 
  deinit () {
    // release used system resources 
    // e.g. close the open file 
  }
}   
```


