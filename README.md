# kogo-oem-ios-dev

**_NOTE:_** App will run on iOS Device Only

### What is this repository for? ###
Development SDK for KOGO OEM framework

* Quick summary
* Version
    : KOGO-TVS 1.5

# Release Notes # 
* Version 0.0.1 - Initial deployment

### How do I get set up? ###

### Follow these steps to add the SDK to your project –
*Step-1: Add the following command in your podfile

For Dev envorinment

```
  pod 'KogoForOem', :git => 'https://github.com/parikshith-kogo/kogo-oem-ios-dev.git'
```

*Step-2: Add the following in your plist
```
    <key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
    <string>Your location is used to personalize content.</string>
    <key>NSLocationAlwaysUsageDescription</key>
    <string>We need your location information to provide information of nearby known location and create your logs for creating timeline at Web portal.</string>
    <key>NSLocationWhenInUseUsageDescription</key>
    <string>We need your location information to provide information of nearby known location and create your logs for creating timeline at Web portal.</string>
```

# For generating JWT_TOKEN

(Optional) Mandatory fields to generate JWT_TOKEN:
```
{
  user_unique_id: String(Mandatory),
  first_name: String(Mandatory),
  last_name : String(Optional),
  mobile: String(Mandatory),
  email: String(Mandatory),
  profile: String(Optional),
  age: String(Optional),
  gender: String(Optional),
  vehile: Array(Optional)
}
```

# Initialize the SDK
Add below code to initialize in AppDelegate.swift

step-1: Import header
```
import KogoForOem
```

Step-2: Goto `didFinishLaunchingWithOptions` and add the following code `Kogo.shared.configureWith("YOUR_JWT_TOKEN_HERE")`

After adding code your `didFinishLaunchingWithOptions` method will be as below.
```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    Kogo.shared.configureWith("YOUR_JWT_TOKEN_HERE")
}

```

# Open KogoForOem from your application #
From the place you want to open `KogoForOem`, add the following code.

step-1: Import header
```
import KogoForOem
```

Step-2: Goto `ViewController Class` where you want to open `KogoForOem`.
Add the following code. Below code takes `UINavigationController` as argument.
```
DispatchQueue.main.async {
    Kogo.shared.openCommunityViewIn(self.navigationController)
}
```

### Who do I talk to? ###

* Repo owner

