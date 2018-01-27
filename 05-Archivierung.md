# Archivierung

Many programming tasks involve sending data over a network connection, saving data to disk, or submitting data to APIs and services. These tasks often require data to be encoded and decoded to and from an intermediate format while the data is being transferred.

### Motivation
* Serialisierung von Objekten
* Abspeichern in Dateien
* Einlesen aus Dateien
* Speicherung erfolgt bei allen als **Komprimierte XML-Daten (Binärdatei)**

**Archivieren - alle enthaltene Objekte müssen Codable sein**

```swift
class Coordinate: Codable { 
var latitude = 0.0
var longitude = 0.0
}
```
### Archivierung 

* Property List & JSON
* NSKeyedArchiver
* Core Data

### Archivieren

```swift
let landmark = Landmark() 
landmark.metadata["version"] = "test"
// file for saving data
let path = "data.plist"
let url = URL(fileURLWithPath: path)
// encode and save
let encoder = PropertyListEncoder()
if let data = try? encoder.encode(landmark) {
try? data.write(to: url) }
```

### Dearchivieren

```swift
// read and decode
if let data = try? Data(contentsOf: url) { 
let decoder = PropertyListDecoder()
if let landmark = 
 try? decoder.decode(Landmark.self, from: data) { 
  print(landmark)
 } 
}
```

-----

### JSON

**wie vorher, nur ersetze:**
* PropertyListEncoder() --> JSONEncoder()
* PropertyListDecoder() --> JSONDecoder()

### Archivierung nur bestimmter Properties

```swift
class Coordinate: Codable { 
  var latitude = 0.0
  var longitude = 0.0
  var cachedData = ""

  enum CodingKeys: String, CodingKey { 
    case latitude
    case longitude 
    }
}
```

-------

### NSKeyedArchiver

**Situation:**
*  Klasse wird um neue Properties erweitert
*  Programm versucht alte Dateiversion zu lesen

**Konsequenz:**
*  Daten lassen sich nicht mehr einlesen

**Lösung ist umständlich**
*  Klasse auf manuelles Encode/Decode umstellen 
*  Zusatzdaten in einem nested Container codieren

**Alternative:**
*  NSKeyedArchiver benutzen

**Funktion**
* Alle archivierten Objekte bekommen einen Namen (key) zur Identifikation
* Einlesen von Archiven aus älteren Programm- versionen ohne Auswand möglich

---------

### Eigenes Encoding

**Methoden zur Unterstützung `NSCoding`**
* Kodieren (abspeichern): encode(with coder:...) 
* Dekodieren (einlesen): init(coder:...)

**Übergebener Encoder / Decoder wird zum Schreiben / Lesen der Klassenelemente benutzt**
* coder.encode(<Object>, forKey: <Key>) 
* decoder.decodeObject(forKey: <Key>)


### Beispiel NSCoding bei Ableitung

```swift

class Employer: Person { 
  var department = "" 
  
  init(name: String, dep: String) { 
  super.init(name: name) 
  department = dep  
} 
required init(coder: NSCoder) { 
  super.init(coder: coder) 
  if let str = coder.decodeObject(forKey: "dep") as? String { 
    department = str  
  } 
}   
override func encode(with coder: NSCoder) {  
  super.encode(with: coder)  
  coder.encode(department, forKey: "dep") 
  }  
}
```

