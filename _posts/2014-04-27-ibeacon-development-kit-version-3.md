---
layout: post
title: Announcing Beacon Development Kit Version 3.0
author: James Nebeker
---

We’re thrilled to announce a major update to the [Beacon Development Kit](http://www.radiusnetworks.com/ibeacon/ibeacon-dev-kit.html), now with the ability to scan for nearby beacons!  

# iBeacon Scanning

The Beacon Development Kit has always been a powerful tool in developing iBeacon compatible apps, with the ability to broadcast as a beacon with custom identifiers and broadcast frequency.  Now with the power to sense other beacons, the development kit is the ultimate proximity beacon utility.   The Raspberry Pi has output pins that can be used to control external devices.  Combining this with iBeacon scanning, you can control physical devices when a particular beacon is detected.   We’ve show a simple example in [this blog post](/2014/04/27/how-to-make-a-raspberry-pi-turn-on-a-lamp-with-an-ibeacon.html), using the development kit to turn on a light when a particular beacon is detected.  Following this example, you can integrate iBeacon proximity technology with the physical world, even with limited programming knowledge.   There are countless other more creative uses for this new feature and we’re excited to see what great ideas everyone can come up with.  

# Download the Update

If you have a previous version of the Beacon Development Kit, we’ve made the latest version available to download [here](http://developer.radiusnetworks.com/ibeacon/beacon-dev-kit-update.html), just follow the instructions and you’ll be up to date in no time. 

<div style="font-weight: bold;">Note:</div> You may experience some instability when using the new scan feature for extended periods of time in high-traffic areas due to an error where the bluetooth adapter enters a bad state.  The only way to recover from this state is to power cycle the adapter or reboot the machine.  We are continuing to work to minimize this issue and will be providing additional updates.   
