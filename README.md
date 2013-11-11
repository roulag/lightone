midterm-lightone
================

int ledPin = 9;
int lightSensor1 = A0;
int lightSensor2 = A1;
int speaker = 3;
int sensorValue1;
int sensorValue2;

void setup (){
  // first set led and speaker as output
  pinMode (speaker, OUTPUT);
  pinMode (ledPin, OUTPUT);
  
 //start serial connection
 Serial.begin (9600);
  

}


void loop () {
  
  //put the sensorValue into a variable
  sensorValue1 = analogRead(lightSensor1);
  sensorValue2 = analogRead(lightSensor2);
  
  //show on Serial Monitor 
  Serial.print(sensorValue1);
  // use the comma to make a space
  Serial.print(", ");
  //use the ln to make a new line for the next reading
  Serial.println(sensorValue2);
  
  //a tone is between 20 and 20000 but for arduino is better from 200 to 2000
  //tone(speaker, 1500);
  
  //connect the lightSensor with the speaker
  //change the lightsensor value into the speaker value 
  tone(speaker, map (sensorValue1, 0, 1000, 200,3000));

  
  int mappedSensor2 = map (sensorValue2, 0, 1000, 3000, 20);
 // change the sensorlight value to a brightness value 
  int brightness = map (sensorValue1, 0, 1000, 10, 255);
//  digitalWrite(ledPin, HIGH);

//use analogWrite to have a range
 analogWrite (ledPin, brightness);
  
  
  
 delay(mappedSensor2);
 
 noTone(speaker);
 analogWrite(ledPin, 0);

 
 
 
 
 delay(mappedSensor2);
 


  



}
