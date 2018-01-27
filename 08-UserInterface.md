# User Interface Classes: UIView

| Controls      | DataViews     | Windows & Bars  | 
| ------------- |:-------------:| -----:|
| UILabel       | UITableView   | UIView |
| UIButton      | UIImageView   | UISearchBar |
| UITextField   | UITextView    | UIToolBar |

### UIControllerView

*  UIViewController
*  UINavigationController
*  UITableViewController

### User interactions

```swift
// alert
@IBAction func askUserConfirmation(_ sender: AnyObject) {  
  let cont = UIAlertController(title: "Confirmation",  
  message: "Are you sure?", preferredStyle: .alert) 

// cancel 
cont.addAction(UIAlertAction(title: "NO", style: .cancel,  
 handler: { (action: UIAlertAction) -> Void in  print("Clicked button NO") 
})) 
// delete
cont.addAction(UIAlertAction(title: "YES", style: .default,  
handler: { (action: UIAlertAction) -> Void in  print("Clicked button YES") 
})) 
 
self.present(cont, animated: true, completion: nil)  }
```

