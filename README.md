# Simple Twitter Direct Messaging app

I chose scenario A: Coach a junior

# Getting Started

This App do NOT use external libraries/frameworks. 

* Please open Mercari.xcodeproj.

## Folder Structure

```
├── Network                 
├── Utils                  
├── Controllers            
├── Models                 
├── Views 
├── Storyboard                  
└── SupportFiles
```

### Network

In this folder there is a function to call API POST/GET

Example:

```
let auth = "Bearer \(accessToken)"

request.requestGET(endpoint: Constant.urlGetFollowersList, parameter: "grant_type=client_credentials", authorization: auth, success: {
    (data) in
    
    DispatchQueue.main.async {
        
        let userArray: NSArray  = data["users"] as! NSArray
        
        for x in 0...userArray.count-1 {
            // call initializer of Enemy
            var userData: [String : Any] = userArray[x] as! [String : Any]
            self.users.append(Followers(
                id: userData["id"] as! Int,
                name: userData["name"] as! String,
                screen_name: userData["screen_name"] as! String,
                location: userData["location"] as! String,
                bio: userData["description"] as! String,
                profile_image_url: userData["profile_image_url_https"] as! String)
            )
        }
        
        print(self.users)
        
        self.tableView.reloadData()
    }
    
}) { (errorMessage) in
    Global.showAlert(vc: self, title: "", action: "Dismiss", message: errorMessage)
}
```

### Utils

In this folder there is a global function and constant

Example:

```
Constant.urlGetToken
```

```
Global.showAlert(vc: self, title: "Error", action: "Dismiss", message: "Something Wrong")
```

### Controllers

In this folder there is a controller from the entire app


### Models

In this folder there is a models from the entire app

### Views

In this folder there is a reusable views like UIView, UITableviewCell etc

### Storyboard

In this folder there is a your storyboard

### SupportFiles

In this folder there is another support file like AppDelegate, Assets etc