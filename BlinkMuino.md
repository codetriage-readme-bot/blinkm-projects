Did you know you can run <a href='http://arduino.cc'>Arduino</a> programs on tiny <a href='http://blinkm.thingm.com'>BlinkM</a> Smart LEDs?  It might make BlinkM the smallest Arduino so far.  To use a BlinkM as an Arduino, all you need is the free Arduino software, a low-cost AVR programmer (which could be a regular Arduino), some wire, and a BlinkM.

Here's a quick video showing how it all works.

<a href='http://www.youtube.com/watch?feature=player_embedded&v=tXbxfsceAEM' target='_blank'><img src='http://img.youtube.com/vi/tXbxfsceAEM/0.jpg' width='425' height=344 /></a>

<h4> BlinkM Capabilities as an Arduino </h4>

BlinkM, BlinkM MinM, and BlinkM MaxM can all be used as tiny Arduinos.  BlinkM and MinM have an ATtiny85 (or ATtiny45) chip, while the BlinkM MaxM has an ATtiny84 chip.

BlinkM boards don't have nearly the I/O pins and other features of a real Arduino board.  But it is very tiny.  Here are its capabilities:
  * 0.4" square (MinM), or 0.6" square (BlinkM)
  * 8MHz clock speed
  * 8k bytes Flash ROM (4kB on ATtiny45)
  * 512 bytes RAM      (256 bytes on ATtiny45)
  * 512 bytes EEPROM   (256 bytes on ATtiny45)
  * 5 I/O lines total, partitioned as:
  * 3 high-brightness LEDs in RGB package
  * 2 digital I/O lines
  * 1 analog I/O line  (shared with digital)

And if you snip off the RGB LED, the three I/O lines used by it can be used as analog or digital inputs.

Most libraries will probably not work without some modifications.  You don't get a hardware serial port either, but SoftwareSerial works.

<h4> Software Setup </h4>

To enable the Arduino software to program BlinkMs, you'll need to teach Arduino about new "Boards".  This is done via a set of config files and AVR core code.  This work has been done by the <a href='http://hlt.media.mit.edu/?p=1695'>High-Low Tech group at MIT</a>.  A <a href='http://hlt.media.mit.edu/wiki/pmwiki.php?n=Main.ArduinoATtiny4585'>pre-Arduino 1.0 version is here</a> and based on work by <a href='http://sites.google.com/site/elettronicaarduinoesperimenti/Home/arduino-ide-and-attiny45'>Alessandro Saporetti</a>.

The <a href='http://blinkm-projects.googlecode.com/files/BlinkMuino.zip'>BlinkMuino.zip</a> zip file contains everything you need, including some examples to get you started.  This zip file works for Mac OS X, Windows, and Linux.

Unzip the BlinkMuino.zip file, and copy the resulting "hardware" folder into your Arduino sketchbook folder.  You can find the location of your sketchbook by opening the Arduino preferences and looking at the "Sketchbook location" field.

Restart the Arduino software and the "Tools" -> "Board" menu should now have entries for BlinkMs. There are three different entries, depending on the type of BlinkM you have.

If you are using an Arduino as the programmer, upload the ArduinoISP sketch (found under File->Examples) to your Arduino.  Be sure to check out the <a href='http://arduino.cc/en/Tutorial/ArduinoISP'>ArduinoISP documentation</a> as there might be some gotchas depending on your Arduino type.

If you are using a normal AVR-ISP programmer, choose its type under the Tools->Programmers menu.

<a href='http://www.flickr.com/photos/todbot/5548882381/' title='BlinkMuino Arduino IDE'><img src='http://farm6.static.flickr.com/5013/5548882381_51cb227b32.jpg' alt='BlinkMuino Arduino IDE' /></a>


<h4> Hardware Setup </h4>

You will need an AVR-ISP programmer to program the BlinkM boards.  An Arduino board running the ArduinoISP sketch turns the Arduino into an AVR-ISP programmer.  Or you can use a regular AVR-ISP programmer.  These are fairly low-cost: the <a href='http://search.digikey.com/scripts/DkSearch/dksus.dll?Cat=2621880&k=avrisp'>Atmel AVRISPmkII</a> is 35 USD, while the <a href='http://www.adafruit.com/index.php?main_page=product_info&cPath=16&products_id=46'>Adafruit's USBtinyISP</a> is 22 USD.

With a programmer acquired, wire up the BlinkM to it.  If using a regular AVR-ISP programmer, it should be wired up like below.  The intro video shows a practical method of using a breadboard and jumper wires to convert the 6-pin AVR-ISP connector to something a BlinkM can use.  Note that some programmers do not supply power to the BlinkM, so you may need to run power too.

<a href='http://www.flickr.com/photos/todbot/5549460078/' title='BlinkMuino AVRISP'><img src='http://farm6.static.flickr.com/5254/5549460078_4c6d088a97_m.jpg' alt='BlinkMuino AVRISP' /></a>

If using AruinoISP, the hookup is as below.  See the diagrams and photos on the <a href='http://code.google.com/p/blinkm-projects/wiki/ReflashBlinkM'>ReflashBlinkM page</a> for details.

<a href='http://www.flickr.com/photos/todbot/5189406314/' title='ReflashBlinkM: Updating BlinkM firmware'><img src='http://farm5.static.flickr.com/4112/5189406314_f79bab3814_m.jpg' alt='ReflashBlinkM: Updating BlinkM firmware' /></a><a href='http://www.flickr.com/photos/todbot/5189406458/' title='ReflashBlinkM: Updating BlinkM firmware'><img src='http://farm5.static.flickr.com/4151/5189406458_01cc5c19f7_m.jpg' alt='ReflashBlinkM: Updating BlinkM firmware' /></a>


<h4> Using BlinkM as an Arduino </h4>

Now load up one of the example sketches located in the "<a href='http://code.google.com/p/blinkm-projects/source/browse/#svn%2Ftrunk%2FBlinkMuino%2Fhardware%2Fblinkm%2Fexamples'>hardware/blinkm/examples</a>" folder of your Arduino sketchbook.

When you press the "Upload" button, the Arduino software will use send your program to the AVR-ISP programmer you've hooked up and it will program the BlinkM.

While the BlinkM is being programmed, its blue LED will flash. Once it stops flashing, the BlinkM starts running the Arduino sketch. At this point you can disconnect the BlinkM from the programmer and use it however you like.  It runs stand-alone, no computer or Arduino board required, just power.

As an example, below is the "<a href='http://code.google.com/p/blinkm-projects/source/browse/trunk/BlinkMuino/hardware/blinkm/examples/BlinkMuinoServoKnob/BlinkMuinoServoKnob.pde'>BlinkMuinoServoKnob.pde</a>" sketch shown in the video.  It assumes it is hooked up to a potentiometer knob and a hobby servo as in this diagram:

<a href='http://www.flickr.com/photos/todbot/5549460276/' title='BlinkMuino ServoKnob'><img src='http://farm6.static.flickr.com/5053/5549460276_e6bb77dd32.jpg' alt='BlinkMuino ServoKnob' /></a>

```
/*
 * BlinkMuinoServoKnob -- Control a servo with a knob 
 * 2011 - Tod E. Kurt - http://todbot.com/blog/ - http://thingm.com/
 */

// BlinkM / BlinkM MinM pins
const int redPin = 3;  // 
const int grnPin = 4;  //
const int bluPin = 1;  // PWM, will blink when programming
const int sdaPin = 0;  // PWM, 'd' pin, can be digital I/O
const int sclPin = 2;  // A/D, 'c' pin, can be digital I/O, or analog input

const int servoPin = sdaPin;
const int knobPin  = sclPin;

int pos;
int pulseWidth;

void setup() {
  pinMode(redPin, OUTPUT);
  pinMode(grnPin, OUTPUT);
  pinMode(bluPin, OUTPUT);

  pinMode(servoPin, OUTPUT);
  pinMode(knobPin, INPUT);
  
  digitalWrite(grnPin, HIGH);     // do a little "hello there" intro
  delay(100);
  digitalWrite(grnPin, LOW); 
}

void loop() {
  digitalWrite(redPin, HIGH);     // say we're doing something
  pos = analogRead( knobPin ); // ranges from 0-1024
  analogWrite( bluPin, pos/4 );
  pulseWidth = pos + 1000;    // convert to microseconds pulsewidth

  digitalWrite(servoPin, HIGH);   // make servo pulse
  delayMicroseconds(pulseWidth);
  digitalWrite(servoPin, LOW);

  digitalWrite(redPin, LOW);      // say we're done
  delay(20);
}
```

<h4> Getting BlinkM back to Factory Firmware </h4>

Programming a BlinkM board with Arduino sketches erases the normal BlinkM firmware.  If you want that functionality back, there is a collection of BlinkM factory firmware files and an application to program them called <a href='http://code.google.com/p/blinkm-projects/wiki/ReflashBlinkM'>ReflashBlinkM</a>.  Use this to get your BlinkM back to factory-fresh conditions.

<a href='http://www.flickr.com/photos/todbot/5189904937/' title='ReflashBlinkM: Updating BlinkM firmware'><img src='http://farm5.static.flickr.com/4154/5189904937_e216d9a503.jpg' alt='ReflashBlinkM: Updating BlinkM firmware' /></a>

<h4> Have Fun! </h4>
Using the BlinkM board as a general purpose microcontroller board is a real blast.  It's astounding being able to reprogram something so small with the easy-to-use Arduino software.  If you develop something neat with a BlinkMuino, let me know in the comments.