# Authsafe-iOS

**Description :-**
AuthSafe sdk helps us to detect suspicious activities in real time and provides device fingerprinting, behavioral analysis, and client-side event monitoring.

**Configuretion Requirements:-**

iOS 9.0+
Xcode 9.0+

**Installation:-**

Authsafe iOS SDK is available through CocoaPods.

```
pod "Authsafe", "1.0.0"
```

**Manually**
```
Download the zip file from the github release, unzip and drag Authsafe.xcframework to the Frameworks, Libraries and Embedded Content section of the target. They should all be set to Embed & Sign.
```

**Implementation Steps**

**Objective-C**

```
[Authsafe configure:@"Your secret key"];
```
The AuthSafe SDK collects device fingerprints from the device and sends this data directly to Authsafe Dashboard.

Application Event: - In the application event Authsafe track your application lifecycle.

```
- (void)applicationDidBecomeActive:(UIApplication *)application{
	[Authsafe trackAppEvent:@"active"];
}

- (void)applicationWillResignActive:(UIApplication *)application{
	[Authsafe trackAppEvent:@"inactive"];
}

- (void)applicationDidEnterBackground:(UIApplication *)application{
	[Authsafe trackAppEvent:@"background"];
}

- (void)applicationWillEnterForeground:(UIApplication *)application{
	[Authsafe trackAppEvent:@"foreground"];
}

- (void)applicationWillTerminate:(UIApplication *)application{
	[Authsafe trackAppEvent:@"terminate"];
}

```
Click Events: - In the click events Authsafe sdk is tracking your every click event. Authsafe will handle the whole functionality and working itself like gyroscope cord., screen orientation with screen X Y coordinates you just need to call the methods.
There are two main parts of click events.

1. Gyroscope X Y Z coordinates
2. Screen X Y coordinates with screen orientation

```
  UITouch *touch = [[UITouch alloc]init];
  [Authsafe trackClickEvent:@"ProfileViewController" screenOrientation:self.supportedInterfaceOrientations view:self.view touch:touch];
```

Location Event: -This event useful for fast geo track location.
In this event you need to get permission from the user, then you need call the below method.
Authsafe needs two permission  ACCESS_FINE_LOCATION,ACCESS_COARSE_LOCATION
If permission is already granted the call the below method

```
//Location object
AuthSafe.trackLocation(location);
```


Login Event: -For tracking login event you need to send the authafe token in your login request.

```
//For form body
key = "request_token"
value = AuthSafe.getRequestToken());

//For raw data
jsonObject.addProperty("request_token", AuthSafe.getRequestToken());

```

Thank you!
Copyright@Authsafe.ai


