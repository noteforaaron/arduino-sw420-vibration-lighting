# arduino-sw420-vibration-lighting
Using arduino uno with sw420 vibration motion sensor engage different lighting based on detected vibration level.
int led = 13;
int vs =9; // vibration sensor
 
void setup(){
  pinMode(led, OUTPUT);
  pinMode(vs, INPUT);
  Serial.begin(9600); 
 
}
void loop(){
  long measurement =vibration();
  delay(50);
  Serial.println(measurement);
  if (measurement > 1000){
    digitalWrite(led, HIGH);
  }
  else{
    digitalWrite(led, LOW); 
  }
}
 
long vibration(){
  long measurement=pulseIn (vs, HIGH);  //wait for the pin to get HIGH and returns measurement
  return measurement;
}        
