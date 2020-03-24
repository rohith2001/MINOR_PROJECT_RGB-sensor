# MINOR_PROJECT_RGB-sensor_code

AIM : To design and develop the LDR(Light Dependent Resistor) based Color_Sensor.
APPARATUS:
1.LDR (1)
2. 320ohm resistor(2)
3.RGB LED(2)
4.Jumper wires.

PRINCIPLE: The LDR exhibits photoconductivity and changes its resistance depending on the light intensity falling on it.
The resistance of the LDR increases when the intensity of the light decreases.

PROCEDURE:
  Here in this project,the LEDs(light emitting diodes) are used to emit red,blue and green colored light whereas the LDRs(light dependent resistors) are used to sense the intensity of the reflected light from the object.The output of the sensor is analyzed and intepreted by an arduino UNO and the result is displayed in serial monitor.
  Generally,minimal light intensity from the green and blue LEDs is reflected to the LDR,while a maximum light intensity is reflected from the red LED.Hence the LDR will have a larger resistance for the green and the blue light scanning, while it has a minimum resistance for red light scanning.
 
CODE:(for RGB_Sensor)

## initializing the led_terminals to the digital pins : red_led, green_led, blue_led terminals for digital pins 2,3 and 4.
int redled=2;
int greenled=3;
int blueled=4;

int value=A0 ## initializing the value to the analog pin-A0
int red;
int blue;
int green;

int redvalue;
int bluevalue;
int bluevalue;

int redout=8;
int greenout=9;
int blueout=10;

void setup() {
pinMode(redled,OUTPUT);
pinMode(greenled,OUTPUT);
pinMode(blueled,OUTPUT);
pinMode(value,INPUT);
pinMode(redout,OUTPUT);
pinMode(greenout,OUTPUT);
pinMode(blueout,OUTPUT);
Serial.begin(9600);
}

void loop(){
digitalWrite(redled,HIGH);
delay(30);
red=analogRead(value); ## It will store the red intensity value.
delay(10);
Serial.print("R=");
Serial.println(red);
digitalWrite(redled,LOW);

digitalWrite(greenled,HIGH);
delay(30);
green=analogRead(value); ## It will store the green intensity value.
delay(10);
Serial.print("G=");
Serial.println(green);
digitalWrite(greenled,LOW);

digitalWrite(blueled,HIGH);
delay(30);
blue=analogRead(value);## It will store the blue intensity value.
delay(10);
Serial.print("B=");
Serial.println(blue);
digitalWrite(blueled,LOW);

if(red>green && red>blue)
{
redvalue=HIGH;
}else
redvalue=LOW;
if(green>red && green>blue)
{
greenvalue=HIGH;
}else
greenvalue=LOW;
if(blue>red && blue>green)
{
bluevalue=HIGH;
}else
bluevalue=LOW;
digitalWrite(redout,redvalue);
digitalWrite(greenout,greenvalue);
digitalWrite(blueout,bluevalue);
