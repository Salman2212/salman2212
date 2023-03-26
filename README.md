PROJECT TITLE: An Arduino Uno Based Line Following Robot

Line Following Robot: in this project, we will see how a line following robot works. it is a robot which uses ir sesnor to detect the white line on black surface or a black line on a white surface and based on this the robot will move forward, right, left and stop.

Applications of Line following robot: it can be used in warehouses and manafacturing organizations to transport material/goods from one place to other place, this is the major application of line following robot

Parts Used in this Project: 1. ARDUINO UNO- 1QTY, 2. MOTOR DRIVER- 1 QTY (TO DRIVE THE MOTORS (L293D)), 3. IR SENSORS- 2 QTY ( ONE ONE LEFT SIDE AND ONE ON RIGHT SIDE), 4. 6-12 VOLT BATTERY- WE ARE USING 9V BATTERY- 1 QTY, 5. BATTERY OPERATED DC MOTOR- 2 QTY (LEFT HAND SIDE AND RIGHT HAND SIDE), 6. WHEELS - 2QTY, 7. CHASSIS

L293D MOTOR DRIVER MODULE- ![images](https://user-images.githubusercontent.com/117999346/226346395-a5c774fd-ed46-4036-a907-17c5353883e9.jpg)

METHOD: TO ENABLE THE MOTOR WE ARE CONNECTING PIN 1 AND 9 (INOUT PINS) TO 5V INPUT. PIN 2 (INPUT 1) PIN 7 (INPUT 2) PIN 8 (INPUT 3) PIN 9 (INPUT 4) ARE THE CONTROL PINS. PIN 3, PIN 6, PIN 11, PIN 14 ARE THE MOTOR CONNECTING PINS.

PIN CONNECTION OF ARDUINO ARE AS FOLLOWS: ENABLEMOTOR1 - ARDUINO PIN 5, INPUTMOTOR1A - ARDUINO PIN6, INPUTMOTOR1B- ARDUINO PIN7, ENABLEMOTOR2 - ARDUINO PIN8, INPUTMOTOR2A - ARDUINO PIN9, INPUTMOTOR2B - ARDUINO PIN10, RIGHTHANDSENSOR - ARDUINO PIN2, LEFTHANDSENSOR - ARDUINO PIN4, VCC PINS- 5 VOLT, GROUND PINS- GROUND.

HERE WE NEED TO KEEP THE TORQUE HIGH WITH LOW RPM IN ORDER TO CARRY THE WEIGHT OF THE ROBOT. WE ARE USING TWO 60 RPM 6V BATTERY OPERATED DC MOTORS.
(USING ARDUINO UNO BOARD)

FIRST STEP IS TO ASSIGN EVERY ARDUINO PIN THAT WE WILL BE USING IN OUR PROJECT.

#DEFINE EN_MOTOR1 5 //ENABLE1 PIN L293 PIN EN1
#DEFINE EN_MOTOR2 8 //ENABLE2 PIN L293 PIN EN2
#DEFINE INPUT_1 6 //MOTOR1 L293 PIN IN1
#DEFINE INPUT_2 7 //MOTOR1 L293 PIN IN1
#DEFINE INPUT_3 9 //MOTOR2 L293 PIN IN1
#DEFINE INPUT_4 10 //MOTOR2 L293 PIN IN1
#DEFINE RIGHT_SENSOR 4 //RIGHT HAND SENSOR
#DEFINE LEFT_SENSOR 2 //LEFT HAND SENSOR

IN THE LOOP SECTION, WE WILL DECLARE THE PIN MODES OF EACH PIN. IN ORDER TO MOVE THE MOTORS WE ARE PULLING THE ENABLE PIN TO HIGH. WE ARE DEFINING BOTH THE SENSORS AS INPUT BY GETTING THE OUTPUTS FROM BOTH THE SENSORS ( WHETHER IT IS DETECTING BLACK LINE OR WHITE SURFACE). IN ORDER TO ROTATE THE  MOTORS WHICH IS TO BE DONE BY USING ARDUINBO UNO , WE HAVE TO DEFINE MOTORS AS OUTPUT.

pinMode (RIGHT_SENSOR, INPUT);
pinMode (LEFT_SENSOR, INPUT);
pinMode (EN_MOTOR1, OUTPUT);
pinMode (EN_MOTOR2, OUTPUT);
pinMode (INPUT_1, OUTPUT);
pinMode (INPUT_2, OUTPUT);
pinMode (INPUT_3, OUTPUT);
pinMode (INPUT_4, OUTPUT);
digitalWrite (EN_, HIGH);
digitalWrite (EN_B, HIGH);
delay(1000);

MOVING FORWARD: IN ORDER TO MOVE THE ROBOT IN FORWARD DIRECTION, RIGHT HAND SENSOR AND LEFT HAND SENSOR SHOULD BE ON TOP OF THE WHITE SURFACE THEN THE ROBOT WILL MOVE IN FORWARD DIRECTION.
if ((digitalRead(RIGHT_SENSOR==0)&&(digitalRead(LEFT_SENSOR==0))
{forward();}
AS THE SENSORS DETECT THE WHITE SURFACE , HENCE 0 INDICATES A HIGH IR SENSOR.

MOVING TOWARDS RIGHT DIRECTION: IN ORDER TO MOVE THE ROBOT IN RIGHT HAND SIDE DIRECTION, RIGHT HAND SENSOR WILL DETECT BLACK AND LEFT HAND SENSOR WILL NOT DETECT BLACK LINE.
if ((digitalRead(RIGHT_SENSOR==1)&&(digitalRead(LEFT_SENSOR==0))
{turnrightSide();}
AS THE RIGHT HAND SENSOR DETECTS THE BLACK LINE, HENCE 1 INDICATES A LOW IR SENSOR AND HENCE IT WILL INITIATE TOWARDS THE RIGHT HAND SIDE DIRECTION.

MOVING TOWARDS LEFT DIRECTION: IN ORDER TO MOVE THE ROBOT IN LEFT HAND SIDE DIRECTION, LEFT HAND SENSOR WILL DETECT BLACK AND RIGHT HAND SENSOR WILL NOT DETECT BLACK LINE.
if ((digitalRead(RIGHT_SENSOR==0)&&(digitalRead(LEFT_SENSOR==1))
{turnleftSide();}
AS THE LEFT HAND SENSOR DETECTS THE BLACK LINE, HENCE 1 INDICATES A LOW IR SENSOR AND HENCE IT WILL INITIATE TOWARDS THE LEFT HAND SIDE DIRECTION.

TO STOP THE ROBOT: IF THE ROBOT DETECTS: THIS FUNCTION WILL BE INITIATED IF BOTH THE SENSORS WILL DETECT THE BLACK LINE. THE ROBOT WILL THEN COME TO A COMPLETE STOP.
if ((digitalRead(RIGHT_SENSOR==1)&&(digitalRead(LEFT_SENSOR==1))
{stop();}

THIS IS THE CODE NEEDED TO CARRY OUT THE ABOVE FUNCTIONS:
FORWARD DIRECTION:
digitalWrite(INPUT_1, HIGH); //RIGHTHANDSIDE MOTOR FORWARD PIN
digitalWrite(INPUT_2, LOW); //RIGHTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_3, LOW); //LEFTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_4, HIGH); //LEFTHANDSIDE MOTOR FORWARD PIN

rightSide:
digitalWrite(INPUT_1, LOW); //RIGHTHANDSIDE MOTOR FORWARD PIN
digitalWrite(INPUT_2, HIGH); //RIGHTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_3, LOW); //LEFTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_4, HIGH); //LEFTHANDSIDE MOTOR FORWARD PIN

leftSide:
digitalWrite(INPUT_1, HIGH); //RIGHTHANDSIDE MOTOR FORWARD PIN
digitalWrite(INPUT_2, LOW); //RIGHTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_3, HIGH); //LEFTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_4, LOW); //LEFTHANDSIDE MOTOR FORWARD PIN

TOSTOP:
digitalWrite(INPUT_1, LOW); //RIGHTHANDSIDE MOTOR FORWARD PIN
digitalWrite(INPUT_2, LOW); //RIGHTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_3, LOW); //LEFTHANDSIDE MOTOR BACKWORD PIN
digitalWrite(INPUT_4, LOW); //LEFTHANDSIDE MOTOR FORWARD PIN


