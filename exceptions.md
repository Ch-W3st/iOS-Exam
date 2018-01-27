# Exceptions

- [Exceptions](#exceptions)
    - [Enummeration + Klasse:](#enummeration-klasse)
    - [Try Catch](#try-catch)
    - [Optionals](#optionals)

Vieles lässt sich mit Optionals regeln, so kann man im Fehlerfall `nil` zurückgeben. 

Was kann geworfen werden? 
* Instanzen von Typen, die das Protokoll Error unterstützen
* Häufig: `enum`

## Enummeration + Klasse:
Error Enummeration
```swift
enum PaymentError: Error {
    case invalid
    case tooHigh(max: Int)
}
```
Findet verwendung in der Klasse:
```swift
class Account { 
    var credit = 100 
    
    // cannot thow an error  
    func welcome() -> String {         
         return "Welcome!" 
    }   
    
    // Methode kann Exceptions werfen
    func check(amount: Int) throws {  
        if amount < 0 { 
            throw PaymentError.invalid  
        } 
} 
```

## Try Catch

```swift
let acc = Account()  

do {
    print(acc.welcome())
    let amountToPay = 120
    try acc.check(amount: amountToPay)
    let message = try acc.pay(amount: amountToPay) 
    print(message)
} catch PaymentError.invalid { 
    print("Invalid amount“)
} catch PaymentError.tooHigh(let maxVal) {
    print("Only \(maxVal) left to pay“)
} catch {
    print("Unspecified error") 
}
```

## Optionals
```swift
func fetchDataFromServer() throws -> Data {  
    if conntectedToServer() { 
        return downloadedData()  
    } else { 
        throw ServerError.cannotConnect  
    } 
}

func fetchData() -> Data? { 
    let possibleData = try? fetchDataFromServer()  
    return possibleData 
} 
// Rückgabetyp wird Optional, nil wenn Exception
```

