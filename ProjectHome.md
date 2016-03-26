NOTE: THIS REPOSITORY IS OLD. ITS CONTENTS HAVE MOVED TO THE GITHUB REPOS:

  * https://github.com/todbot/BlinkM-Examples
  * https://github.com/todbot/BlinkMuino
  * https://github.com/todbot/ReflashBlinkM
  * https://github.com/todbot/FreeM
  * https://github.com/todbot/CtrlM
  * https://github.com/todbot/SoftI2CMaster

Projects using BlinkM Smart LEDs, usually with Arduino and Processing.

[![](http://blinkm-projects.googlecode.com/svn/trunk/blinkm_imgs.jpg)](http://blinkm.thingm.com/)

### BlinkM as a Small Arduino ###

See the BlinkMuino page for more details.


### TweetM ###
The code and design docs for <a href='http://tweetm.thingm.com/'>TweetM</a> gadget as seen on <a href='http://www.colbertnation.com/the-colbert-report-videos/311944/june-08-2010/mark-frauenfelder'>The Colbert Report</a> live here.

There will be more coming, but for now you can check out the <a href='http://code.google.com/p/blinkm-projects/source/browse/#svn/trunk/blinkm_examples/arduino/TweetM'>TweetM</a> Arduino sketch code.

Also see the <a href='http://code.google.com/p/linkm/'>LinkM project</a> for the TwitterBlinkM example.


### BlinkM Example Code ###
Different examples in many different languages (Arduino, Processing/Java, Basic Stamp, Max/MSP) showing how to control BlinkMs.

Examples include:
  * BlinkMSensor0 -- possibly the smallest Arduino sketch showing how to control a BlinkM
  * BlinkMCylon -- multi-colored Cylon effect using many BlinkMs
  * BlinkMTester -- general BlinkM testing sketch for Arduino
  * BlinkMSequencer -- drum-machine + color mixer Processing sketch for Arduino+BlinkM
  * BlinkMScriptTool -- Processing sketch to upload/download BlinkM light scripts for Arduino+BlinkM

If you're looking for examples using <a href='http://linkm.thingm.com/'>LinkM</a>, see the <a href='http://code.google.com/p/linkm/'>LinkM Googlecode project</a>.

### SoftI2CMaster & BlinkM\_funcs\_soft.h ###
The normal "BlinkM\_funcs.h" library used in Arduino sketches to talk to BlinkM requires the standard Arduino Wire library.  The Wire library has some issues that can impact you if you have long I2C cables or run at 3.3V.  The [SoftI2CMaster](https://github.com/todbot/SoftI2CMaster) library lets you use any two I/O pins as I2C pins.  Included in SoftI2CMaster is a simple [BlinkM\_funcs\_soft.h](https://github.com/todbot/SoftI2CMaster/tree/master/examples/BlinkMSoftI2CDemo) library demonstrating its use with a BlinkM.

### ReflashBlinkM ###
All BlinkM-family devices can have their firmware updated. This makes them great for tiny development boards for ATtiny processors. ReflashBlinkM is an application that makes it easy to put back the original firmware or update a BlinkM to the latest firmware.

Get pre-built versions of the app, or build the Processing app yourself:
  * [ReflashBlinkM for Windows](http://blinkm-projects.googlecode.com/files/ReflashBlinkM-macosx.zip)
  * [ReflashBlinkM for Mac OS X](http://blinkm-projects.googlecode.com/files/ReflashBlinkM-macosx.zip)
  * [ReflashBlinkM source in SVN](http://code.google.com/p/blinkm-projects/source/browse/#svn/trunk/blinkm_examples/processing/ReflashBlinkM)



### FreeM Kit (aka BlinkM Battery Remote) ###

FreeM is a 9V battery topper that provides a 5V power supply for BlinkM and also gives it an infrared (IR) remote control.

The complete firmware and schematics for the FreeM Kit are available here:
http://code.google.com/p/blinkm-projects/source/browse/#svn/trunk/freem
