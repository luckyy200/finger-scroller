# finger-scroller
title: Finger Scroller

author: gaya

description: it’s a finger glove that connects to a device and when reading a book/manga you fold your finger and it scrolls down and when the finger is straight it stops.

created_at: 30/09/2026 (day/month/year)

 - - -

 # september 30 : designed the project

 its my first real project on hack club so forgive me for any mistake i make:,)
(and english isn't my first language so sorry about any mistake there)

 came up with the idea a while ago while i was reading an online manga i wanted to put my phone aside and do something while still reading, then i thought about this.
 today i started designing the idea and turning it into my first project!
i designed on paper how it would look, how it'd work and it's features.

features:
* connects through bluetooth to a device like a phone/computor
* when the finger is folded the book/manga scrolls down
* when the finger is straight it/s stops
* you could change the speed of the scroll

 <img width="1468" height="2048" alt="image" src="https://github.com/user-attachments/assets/7a5758cc-d50e-4981-b4ac-bfa37e84041a" />

**Total time spent: 1 hour**

- - -
# October 01 : researched flex sensor

i spend the day researching the flex sensor, how it works through sites like 'last minute engineers' & youtube, then played a bit with a circuit simulation on tinkercad.

<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/3a52fe58-f8a9-4726-b165-e148fa2c244a" />

<img width="2557" height="1126" alt="image" src="https://github.com/user-attachments/assets/45bc4dd6-b6e6-4bbd-962f-de28cd881f92" />

<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/264241b5-3a6e-4b29-93bf-7bcefc8895b2" />




**Total time spent: 2 hour**

# October 02 : reaserch & code
i studied the bluetooth protocol, how it works, the code to connecting the microcontroller and the device, using random nerd turtorials site.
worked on the code for the flex sensor: when its a specific dagree it would send "0" or "1", so that in the future code it would send this information to the device. 
current code:

const int flex = A1;

int scroll = 0;

const float VCC = 5;			// voltage at Ardunio 5V line

const float R_DIV = 47000.0;	// resistor used to create a voltage divider

const float flatResistance = 25000.0;	// resistance when flat

const float bendResistance = 100000.0;	// resistance at 90 deg

void setup() {

	Serial.begin(9600);
	
	pinMode(flex, INPUT);

}

void loop() {	
	
	int ADCflex = analogRead(flex);
	
	float Vflex = ADCflex * VCC / 1023.0;
	
	float Rflex = R_DIV * (VCC / Vflex - 1.0);
	
	Serial.println("Resistance: " + String(Rflex) + " ohms");

 float angle = map(Rflex, flatResistance, bendResistance, 0, 90.0);
	
	Serial.println("Bend: " + String(angle) + " degrees");
	
	Serial.println();
	
	delay(500);
	
  if (30 < angle && angle < 180){
  
  scroll = 1;
  
  Serial.println(scroll);
  
  }
  
  if (0 < angle && angle < 30 ){
  
  scroll = 0;
  
	Serial.println(scroll);

}

}


<img width="2465" height="936" alt="image" src="https://github.com/user-attachments/assets/292a45b7-4a7b-4c09-818d-aa550b5af9e0" />

**Total time spent: 4 hour**
