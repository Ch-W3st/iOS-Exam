# Cocoa Touch
### Framework
* Cocoa -> Application Kit Framework
* Cocoa Touch -> UIKit Framework

### Main components of a project

* AppDelegate (helper class)
* ViewController (controller for the only view in the app)
* Main.storyboard (storyboard for the design)
* Launchscreen.storyboard 
* Test.swift

:dart: iOS Deployment target --> set the minimum version target e.g. 8.1 

### App delegate

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




