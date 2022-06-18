Experiment--08-Design-and-control-of-Mobile-robot-motion-
AIM:
To Design a wheel base for mobile robot and control the motion using forward and reverse motion

COMPONENTS REQUIRED:
Patch cables
L293D motor shield
Arduino Uno
USB Interfacing cable
Connecting wires
Wheels
DC motor
THEORY:
We can control the speed of the DC motor by simply controlling the input voltage to the motor and the most common method of doing that is by using PWM signal.

DC Motor Speed Control Input Voltage PWM DC Motor Control PWM, or pulse width modulation is a technique which allows us to adjust the average value of the voltage that’s going to the electronic device by turning on and off the power at a fast rate. The average voltage depends on the duty cycle, or the amount of time the signal is ON versus the amount of time the signal is OFF in a single period of time.

PWM Working Principle - Pulse Width Modulation How It Works

image

image

PROCEDURE:
Connect the circuit as per the circuit diagram
Connect the board to your computer via the USB cable.
If needed, install the drivers.
Launch the Arduino IDE.
Select the board (If you the board is arduino uno, select accordingly).
Select your serial port, accordingly ( E.g. COM5 )
Open the file of the program and verify the error , clear if any errors that are existing
Upload the program and check for the physical working.
Ensure safety before powering up the device
Plot the graph for the output voltage vs the resistance
PROGRAM
#include <AFMotor.h>

AF_DCMotor motor(4);// number of motor connected with shield

void setup() {
 Serial.begin(9600);           // set up Serial library at 9600 bps
 Serial.println("Motor test!");

 // turn on motor
 motor.setSpeed(200);

 motor.run(RELEASE);
}

void loop() {
 uint8_t i;
 
 Serial.print("tick");
 
 motor.run(FORWARD);
 for (i=0; i<255; i++) {
   motor.setSpeed(i);  
   delay(10);
}

 for (i=255; i!=0; i--) {
   motor.setSpeed(i);  
   delay(10);
}
 
 Serial.print("tock");

 motor.run(BACKWARD);
 for (i=0; i<255; i++) {
   motor.setSpeed(i);  
   delay(10);
}

 for (i=255; i!=0; i--) {
   motor.setSpeed(i);  
   delay(10);
}
 

 Serial.print("tech");
 motor.run(RELEASE);
 delay(1000);
}
OUTPUT:
WhatsApp Image 2022-06-18 at 8 43 18 AM

WhatsApp Image 2022-06-18 at 8 43 17 AM (1)

WhatsApp Image 2022-06-18 at 8 43 17 AM

RESULTS : Arduino uno is interfaced with FSR and output values are indicated on a graph.
