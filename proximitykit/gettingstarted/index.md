---
layout: proximitykit
---

# Getting started with Proximity Kit

This guide should get your app working with Geofencing and the Proximity Kit service.

## Download and Install

If you have not downloaded the Proximity Kit framework and added it to your project you should [go do that first](http://proximitykit.com/download).

Note: Users of the Proximity Kit client library agree to abide by the license terms as
 specified for [iOS](proximity-kit-ios-license.txt) and [Android](proximity-kit-android-license.txt).

## Creating a Location Manager

Proximity Kit adds a wrapper around the standard Core Location Manager. This allows for automatic registering of fences and iBeacons, but should give your app all the power and control it needs to use location data.

First, we need to create an instance of the `PKManager`. Each app should have only one instance of this object. For simple applications we recommend this to be a property on your Application Delegate. However, this works just fine on any class as long as the object is around for the lifetime of the application. For simplicity's sake this document will describe setting up the `AppDelegate` class to work with the `PKManager` instance.

In `AppDelegate.h` add the protocol for `PKManagerDelegate` and a property to store an instance of the manager:

```objective-c
#import <UIKit/UIKit.h>
#import <ProximityKit/ProximityKit.h>

@interface AppDelegate : UIResponder <UIApplicationDelegate, PKManagerDelegate>

@property (strong, nonatomic) UIWindow *window;
@property (strong, nonatomic) PKManager *proximityKitManager;

@end
```

In `AppDelegate.m` allocate the manager and assign the delegate:

```objective-c
- (BOOL)application:(UIApplication *)application
        didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    // create and start to sync the manager with the Proximity Kit backend
    self.proximityKitManager = [PKManager managerWithDelegate:self];
    [self.proximityKitManager start];

    return YES;
}
```

There is more to the `PKManager` API, take a look in `PKManager.h` in the Proximity Kit framework for the full listing.

## Create the delegate methods

Within your AppDelegate class you can define either the enter or exit region methods, which will be called when the app enters or exits a fence.

```objective-c
#pragma mark -
#pragma mark ProximityKit delegate methods

- (void)proximityKit:(PKManager *)manager didEnter:(PKRegion *)region {
    NSLog(@"entered %@", region);
}
- (void)proximityKit:(PKManager *)manager didExit:(PKRegion *)region {
    NSLog(@"exited %@", region);
}
```

There are a number of other delegate methods, take a look in `PKManagerDelegate.h` in the Proximity Kit framework for the full listing.

## Simulating Geofences

In the iPhone simulator you can change the location in the menu "Debug -> Location -> Custom Location...".

From there you will have a form where you can enter GPS coordinates of your location.

Note: If the location is set to coordinates within your fence when the simulator is launched you may have to set it out side of the fance and back inside again.

## Simulating iBeacons

While you can't yet simulate an iBeacon in the iPhone Simulator, you can use [MacBeacon](http://www.radiusnetworks.com/macbeacon-app.html). It makes testing iBeacon functionality easy, particularly since your Mac can broadcast as an iBeacon while running your app directly from Xcode. This is a great way to explore how the beacon behaves while in the Xcode debugger.



