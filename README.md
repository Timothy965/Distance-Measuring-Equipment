# Distance-Measuring-Equipment

1)Introduction:

1.1)Sound is a vibration that typically propagates as an audible wave of pressure, through a transmission medium such as a gas, liquid or solid. Humans can only hear sound waves as distinct pitches when the frequency lies between about 20Hz and 20kHz. Sound above 20kHz is ultrasound and is not perceptible by humans. Sound waves below 20Hz are known as infrasound. The sound energy travels by causing disturbance in the medium it is travelling and this is called propagation of sound waves. Under normal conditions, the velocity of the sound is 330m/s.

1.2)Ultrasound is used in many different fields. Ultrasonic devices are used to detect objects and measure distances. Ultrasound imaging or sonography is often used in medicine. In the non-destructive testing of products and structures, ultrasound is used to detect invisible flaws. Industrially, ultrasound is used for cleaning, mixing, and to accelerate chemical processes. Animals such as bats and porpoises use ultrasound for locating prey and obstacles.

1.3)In this Project, we are going to develop a Distance Measuring Equipment, which can measure the distance of an object, with Ultrasonic Sensors, LCD and Arduino.

2)Aim:
The main Aim of this project is to implement Object measurement and its distance from our source (Ultrasonic sensor), with any contact to the device. 

3)Hardware/Components Required:

    *Arduino Uno
    *Ultrasonic Sensor (HC-SR04)
    *LCD Display (16x2)
    *Breadboard
    *10KΩ Potentiometer
    *Jumper Wires 

4)Working:

4.1)Ultrasonic ranging module is the utmost important component in this project. Ultrasonic ranging module provides 2cm-300cm, non-contact measurement function. The modules includes ultrasonic transmitters, receiver and control circuit.

4.2)We only need to supply a short 10µS pulse to the trigger input to start the ranging, and then the module will send out an 8 cycle burst of ultrasound at 40 kHz and raise its echo. The Echo is a distance object that is pulse width and the range in proportion. The Echo is also high from the moment of sending the signal and receiving it.

4.3)This duration for which the Echo signal is high, is being calculated by Arduino as per the code we have created, and is converted to distance in centimetres. The same data is displayed on the LCD.

4.4)Here, Arduino continuously sends the Trig signal and the distance of the target can be measured continuously without any delay.

5)Connection/Wiring:

5.1)Ultrasonic Sensor

    *Vcc- +5V
    *Trig- Pin 11 Of Arduino
    *Echo- Pin 10 Of Arduino
    *GND- GND
    
5.2)LCD Display

    *Pin 1- GND
    *Pin 2- +5V
    *Pin 3- Potentiometer common Terminal
    *Pin 4- Pin 7 Of Arduino
    *Pin 5- GND
    *Pin 6- Pin 6 Of Arduino
    *Pin 11- Pin 5 Of Arduino
    *Pin 12- Pin 4 Of Arduino
    *Pin 13- Pin 3 Of Arduino
    *Pin 14- Pin 2 Of Arduino
    *Pin 15- +5V
    *Pin 16- GND
    
5.3) For more information of connection, look in Fig 1.1

6)Program/Code:

    #include <LiquidCrystal.h>
    LiquidCrystal lcd(7, 6, 5, 4, 3, 2);
    const int trigPin = 11;
    const int echoPin = 10;
    const int led = 13;


    void setup() 
    {
    pinMode(trigPin, OUTPUT);
    pinMode(echoPin, INPUT);
    pinMode(led, OUTPUT);
    lcd.begin(16, 2);
    lcd.print ("Ultrasonic ");
    lcd.setCursor(0, 1);
    lcd.print ("Range Meter");
    delay (5000);
    
    }
    long duration, r;
    float distance;

    void loop()
    {
    lcd.clear();
    lcd.print("Distance in cm");
    
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);

    duration = pulseIn(echoPin, HIGH);
    long r = 3.4 * duration / 2;     
    float distance = r / 100.00;
  
    lcd.setCursor(0, 1);
    lcd.print(distance);
    delay (300);

  
 
    if(distance<10)
    {
    digitalWrite(led,HIGH);
    }
    else
    {
    digitalWrite(led,LOW);
    }
  
    delay(300);
    }
    
6.1) The Code can be found in top, and is used in Arduino IDE Software

6.2)Upload the Code, and you will see the distance printed in LCD.



     
       
 

   
