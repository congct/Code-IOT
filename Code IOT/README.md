# Code-Asm
# Code-IOT
/*************************************************************
  Download latest Blynk library here:
    https://github.com/blynkkk/blynk-library/releases/latest

  Blynk is a platform with iOS and Android apps to control
  Arduino, Raspberry Pi and the likes over the Internet.
  You can easily build graphic interfaces for all your
  projects by simply dragging and dropping widgets.

    Downloads, docs, tutorials: http://www.blynk.cc
    Sketch generator:           http://examples.blynk.cc
    Blynk community:            http://community.blynk.cc
    Follow us:                  http://www.fb.com/blynkapp
                                http://twitter.com/blynk_app

  Blynk library is licensed under MIT license
  This example code is in public domain.

 *************************************************************
  This example runs directly on ESP8266 chip.

  Note: This requires ESP8266 support package:
    https://github.com/esp8266/Arduino

  Please be sure to select the right ESP8266 module
  in the Tools -> Board menu!

  Change WiFi ssid, pass, and Blynk auth token to run :)
  Feel free to apply it to any other example. It's simple!
 *************************************************************/

/* Comment this out to disable prints and save space */
#define BLYNK_PRINT Serial

/* Fill-in your Template ID (only if using Blynk.Cloud) */
#define BLYNK_TEMPLATE_ID "TMPLu-CrZcho"
#define BLYNK_DEVICE_NAME "RedLight"
#define BLYNK_AUTH_TOKEN "c1UFIR5dJsy7BAVc3gdNCStSzZs3AFZI"
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

// You should get Auth Token in the Blynk App.
// Go to the Project Settings (nut icon).
char auth[] = "c1UFIR5dJsy7BAVc3gdNCStSzZs3AFZI";
// Your WiFi credentials.
// Set password to "" for open networks.
char ssid[] = "iPhone";
char pass[] = "Thanhcong2001!";
#define analogPin A0
#define led D2
int value;
int phantram;
void setup()
{
  Serial.begin(9600);
  Blynk.begin(auth, ssid, pass);
  pinMode(led, OUTPUT);
}
void loop()
{
  Blynk.run();
  value = analogRead(analogPin); // doc gia tri cam bien 0-1023
  phantram = map(value, 0, 1023, 100, 0);
  Blynk.virtualWrite(V2,phantram);
  if (phantram <= 10) {
    digitalWrite(led, LOW);
  }
  else { //nguoc lai
    digitalWrite(led, HIGH);
  }
}


