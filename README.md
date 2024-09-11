# kogo-tvs-ios

**_NOTE:_** All features of the app are to be checked on on iOS Device Only

### What is this repository for? ###
Development SDK for KOGO OEM framework and KOGO App

* Quick summary & initialization guide
* Version : 3.0.1

### How do I get set up? ###

### Follow these steps to add the SDK to your project –
*Step-1: Add the following lines of code in your podfile

```
  pod 'KogoTvs', :git => 'https://github.com/parikshith-kogo/kogo-tvs-ios.git'
```

Add below code at the very end of your podfile
```
post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
        end
    end
end
```

*Step-2: Add the following in your plist
```
    <key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
    <string>Your location is used to personalize content.</string>
    <key>NSMotionUsageDescription</key>
    <string>KOGO needs device motion access for accuracy in tracking your trip when started</string>
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
import KogoTvs
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
import KogoTvs
```

Step-2: Goto `ViewController Class` where you want to open `KogoTvs`.
Add the following code. Below code takes `UINavigationController` as argument.
```
DispatchQueue.main.async {
     Kogo.openCommunityViewIn(self.navigationController, with: "YOUR_JWT_TOKEN_HERE", onCompletion: {
            print("On Back clicked")
        })
}
```

### Who do I talk to? ###

* Repo owner

