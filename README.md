# GCM-SDK-New-Doc

# PREREQUISITES:
1] Get GCM Sender Id and API Key from Google Developer console.

2] Get App Id and Smartech GCM SDK from Smartech Panel.

# SDK Integration Steps (mandatory):
STEP1:

Add Netcore SDK (i.e. SmartechGCMSDK.aar file) in libs directory.

STEP2:

Modify build.gradle file as follows -

1] Add below code at the bottom of build.gradle file:

```java
repositories{
   flatDir { dirs 'libs' }
}
```

2] Add below code in Dependencies (not in child dependencies):

```java
compile(name:'SmartechGCMSDK', ext:'aar')
compile 'com.google.code.gson:gson:2.8.0'
compile "com.google.android.gms:play-services:9.6.0"
```

# Integration Steps for Push Notifications
STEP1:

Add below code in LAUNCHER activity under onCreate method and above the super.onCreate.line:

```java
NetcoreSDK.register(getApplication(),”<Smartech app Id>”, ”<GCM senderId>”, "<User identity>");
```
   
> **NOTE:**

1] User Identity can either be ""(blank) OR **Primary Key** of the user defined on Smartech panel.

2] With the above code, Smartech SDK will start sending **App Launch** and **First Launch** activities by default.
  
# Integration Steps for App Activity Tracking

For Login Activity:

```java
NetcoreSDK.login( context, <"User identity"> );
```

For Logout Activity:

```java
NetcoreSDK.logout( context, <"User identity"> );
```

# For Any Other Custom Activity Tracking: (ex. - AddtoCart, Checkout, Searched, etc.)

```java
NetcoreSDK.track( context, <"User identity">,<"eventId">,<"payload">);
```

**NOTE:**

Ready-to-use Custom Activity tracking code is available on Smartech panel for every created activity.
