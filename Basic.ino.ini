#include <WiFiManager.h> 

String myString1;
String myString2;
String myString3;

void setup() {
  Serial.begin(9600);
  WiFiManager wm; // WiFiManager, Local initialization

  wm.setDebugOutput(false);
  wm.resetSettings(); // reset settings - wipe stored credentials for testing

  // Create parameters for user input
  WiFiManagerParameter custom_text_box1("my_text1", "Enter your first string", "default string 1", 50);
  WiFiManagerParameter custom_text_box2("my_text2", "Enter your second string", "default string 2", 50);
  WiFiManagerParameter custom_text_box3("my_text3", "Enter your third string", "default string 3", 50);

  // Add parameters to WiFiManager
  wm.addParameter(&custom_text_box1);
  wm.addParameter(&custom_text_box2);
  wm.addParameter(&custom_text_box3);

  // Attempt to connect to WiFi
  if (!wm.autoConnect("AutoConnectAP", "password")) {
    Serial.println("Failed to connect and hit timeout");
    delay(3000);
    ESP.restart();
    delay(5000);
  }

  // Now that we are connected, we can read the parameters
  myString1 = custom_text_box1.getValue();
  myString2 = custom_text_box2.getValue();
  myString3 = custom_text_box3.getValue();
}

void loop() {
  Serial.println("String 1: " + myString1);
  Serial.println("String 2: " + myString2);
  Serial.println("String 3: " + myString3);
  delay(1000);
}
