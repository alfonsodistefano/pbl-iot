# pbl-iot
//PSEUDO CODE
// Library for temp and humidity sensor and OLED
// Initialize the humidity and temperature sensors input 
// Initialize the Oled output
// Initialize Web function of esp-32

// read the sensors analog input and convert them to Celcius a g/m3 and convert pressure 
  //Analog read the values and then convert them to Celcius g/m3 and pascals
// Set threshhold through Web app
  //A web controlled variable (LAB8)
// Check if values are exceding certain threshhold
  // An if condition that is checked with web variable
// Turn Led Red if temp too high and Blue if HUmidity too high if they are both too high green
  // Result of the if condition
// Print the values to the OLED monitor And the Web page
  // Lab8 Html printing and Printing to OLED






#define LED_GREEN 27
#define LED_RED 25
#define BUTTON_PIN 14 // button pin

float TEPM_MAX = 20;
float HUM_MAX = 20;
float PRES_MAX = 20;

void setColor(int red, int green){
analogWrite(LED_RED, red);
analogWrite(LED_GREEN, green);
}

void setup(){
pinMode(LED_GREEN, OUTPUT);
pinMode(LED_RED, OUTPUT);
pinMode(BUTTON_PIN, INPUT_PULLUP); // pullup
Serial.begin(115200);

setColor(0, 0);
}

void loop(){
int buttonState = digitalRead(BUTTON_PIN);

if (buttonState == LOW) {
Serial.println("Button Pressed!");
setColor(255, 0); // Red
} else {
setColor(0, 255); // Green
}

delay(50);
}
