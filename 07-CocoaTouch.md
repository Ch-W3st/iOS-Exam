# Cocoa Touch
### Framework
* Cocoa -> Application Kit Framework
* Cocoa Touch -> UIKit Framework

### Datastructure

restricted access to iOS data system (sandbox for each app)

| Directory       | Access          | Usage |
| ------------- |:-------------:| -----:|
| <Application_Home>/ AppName.app | Bundle.main | Bilder, Texte, etc. (1) (E) |
| <Application_Home>/ Documents/  | urls(for: .documentDirectory, in: .userDomainMask) | Benutzerdaten, Dokumente (2) (E) |                                           
| <Application_Home>/ Library/Preferences     | UserDefaults() | Voreinstellungen (2) (E)  |
| <Application_Home>/ Library/Caches  | urls(for: .cachesDirectory, in: .userDomainMask)  | Temporäre Dateien (3) (E) Verlust bei Reset |
|  <Application_Home>/ tmp/      | NSTemporaryDirectory() | Temporäre Dateien (3) (N) |


  
* (1)  kein Backup, aber mit Applikation gespeichert 
* (2)  Backup durch iTunes
* (3)  kein Backup durch iTunes
* (E) Daten bleiben zwischen Programmstarts erhalten
* (N) Daten bleiben nicht erhalten

### Main components of a project

* AppDelegate (helper class)
* ViewController (controller for the only view in the app)
* Main.storyboard (storyboard for the design)
* Launchscreen.storyboard 
* Test.swift

:dart: iOS Deployment target --> set the minimum version target e.g. 8.1 

### AppDelegate.swift

could be a place for a model e.g. address book

* Q: How to safe a file before closing app?
* A: The app is an instance of UIApplication. Customize UIApplication!

#### Status of an app could be 
* active / inactive
* foreground / background

#### Methods
*  application(_:didFinishLaunchingWithOptions:)  --> load data while opening
*  applicationWillTerminate(_:) --> safe data before app quits
*  applicationDidBecomeActive(_:) 
*  applicationWillResignActive(_:) 
*  applicationWillEnterForeground(_:) 
*  applicationDidEnterBackground(_:)

### Storyboard
* all views in `Main.storyboard`
* set transitions between views

#### Interface builder
`First Responder` in `View Controller Scene`
* proxy for an object which reacts first on messages e.g. `Touch events`
* starts with the view which is on top of the list in the `ViewController`
* if a message could not be handled -> it will take the next one

![View Controller Scene](http://swiftbook.ru/sites/default/files/images/tuts/tut-2/5.png)

### Naming
| Nr.       | Name           |   |
| ------------- |:-------------:| -----:|
| 1      | Project Navigator | 
| 2      | Interface Builder |   
| 3      | Storyboard |   
| 4      | Device & Orientation | 
| 5      | View Controllers Responders| 
| 6      | - | 
| 7      | File Inspector |
| 8      | Object Library | 

#### Nr. 7 
-> from left to right
* File inspector (properties of the storyboard)
* Quik Help
* Identity Inspector
* Attributes Inspector
* Size Inspector
* Connections Inspector

---------

![MVC](https://koenig-media.raywenderlich.com/uploads/2013/07/mvc0.png)

**Model** 
* represents the data which manipulates the app (dtata & logic)
* no direct access from the user perspective

**View** 
* visualization of the model 
* consists of reusable objects e.g. buttons, views, text fields

**Controller** 
* transfer of data and actions 

-------

### Actions & Outlets

#### Actions

Def.: an action is a method which can be combined with `Controls`
* use action: drag and drop while holding `ctrl`
* keyword: `@IBAction func ...`
**is used for an event to trigger**

#### Outlets

Def.: is a property which has a reference to the object
* use action: drag and drop while holding `ctrl`
* keyword: `@IBOutlet func ...`
***used for change the way sth. looks*




