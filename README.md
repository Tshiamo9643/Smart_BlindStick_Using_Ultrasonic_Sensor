# Smart_BlindStick_Using_Ultrasonic_Sensor
Using Ultrasonic Sensor with Buzzer and LED

//WE USED ARDUINO IDE AND ARDUINO UNO R3
//Define pins
const int trigPin = 9;
const int echoPin = 10;
const int buzzer = 11;
const int LED = 13;

long dur;
int distance, safeDist;


void setup() 
{
  // put your setup code here, to run once:
  
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(LED, OUTPUT);
  Serial.begin(9600);
   
}
void loop() {
  // put your main code here, to run repeatedly:
  //WE ARE CLEARING TRIG PIN
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2000);
  //WE ARE SETTING THE TRIG PIN
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(1000);
  digitalWrite(trigPin, LOW);
  //READS THE ECHO PIN AND RETURNS THE SOUNDWAVE
  dur = pulseIn(echoPin, HIGH);

//CAL DISTANCE//
  distance = dur * 0.34 * 2;
  safeDist = distance;
  if(safeDist <= 30)
  {
    digitalWrite(buzzer, HIGH);
    digitalWrite(LED, HIGH);          
  }
  else{
    digitalWrite(buzzer, LOW);
    digitalWrite(LED, LOW); 
  }
  Serial.print("DISTANCE :");
  Serial.println(distance);
    
}

