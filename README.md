# Authsafe-iOS

**Description :-**

AuthSafe sdk helps us to detect suspicious activities in real time and provides device fingerprinting, behavioral analysis, and client-side event monitoring. 

**Configuretion Requirements:-**

minSdk version = 21 

Internet permission 
Location permission (optional) 

ACCESS_FINE_LOCATION, ACCESS_COARSE_LOCATION  

**Getting Start:-**

**Step 1 >**  Add the JitPack repository to your build file

```gradle

allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
  ```
**Step 2 >** Add the dependency

```gradle
dependencies {
	        implementation 'com.github.Ashishchidhava:Library-Task:Tag'
	}
  ```
  
**Step 3 >** Add secret key in your manifest file
  ```
  <meta-data 
    android:name="auth_safe_secret_key" 
    android:value="@string/auth_secret" /> 
  ```
  
  Java Implementation 
  
  // Place the below in your application class onCreate method 

```
AuthSafe.configure(this) 
```
The AuthSafe SDK collects device fingerprints from the device and sends this data directly to Authsafe Dashboard.  

Screen Change Event: - In the screen change event Authsafe track your every screen transaction between screen open to close. 

For Activity: - Once you initialize the Authsafe in application oncreate method the Activity tracking automatically will start. 
We are tracking the whole lifecycle of activity. 

For Fragment:-For fragment tracking you need to call a method in your root fragment activity. 

```

AuthSafeFragmentLifecycleCallbacks.trackFragmentChange(this); 

//It's required higher Sdk version 8 (Orio) 

if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) { 
    AuthSafeFragmentLifecycleCallbacks.trackFragmentChange(this); 
} 

```
Click Events: - In the click events Authsafe sdk is tracking your every click event. Authsafe will handle the whole functionality and working itself like gyroscope cord., screen orientation with screen X Y coordinates you just need to call the methods. 
There are two main parts of click events. 

1. Gyroscope X Y Z coordinates 
2. Screen X Y coordinates with screen orientation 
For Activity:-You have to override the method below. 

```
@Override 

public boolean onTouchEvent(MotionEvent event) { 
    AuthSafe.trackClickEvent(event); 
    return true; 
} 

```

For Fragment:-

```
AuthSafe.trackClickEvent(view.getRoot()); 
```

For View (Button, Image, etc..):- On view click you need call below method. 

```
AuthSafe.trackClickEvent(); 
```

For Recyclerview:- 

```
AuthSafe.trackClickEvent(holder.itemView); 
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



