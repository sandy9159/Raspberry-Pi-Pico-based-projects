# Raspberry-Pi-Pico-based-projects

# 1 Stopwatch Using Raspberry Pi Pico

![image](https://user-images.githubusercontent.com/19898602/143274179-129ec1d5-6f41-4d7c-9731-ea7f5dc6376b.png)

Hello,

In this article , we are going to make stopwatch using Raspberry Pi Pico and tm1637 4 digit 7 segment display module.

Here, I used tm1637 4 digit 7 segment display module as a display to show real-time counting.

Let’s make this.

If you are new to Raspberry Pi Pico and wants to get started then click here, it is all about getting started with Raspberry Pi Pico.

# Required Components

> Raspberry Pi Pico

> Breadboard

> Jumper Wires

> 2 Push buttons

> 1K Ohm resistor

# Schematic Diagram

Follow this schematic diagram and make connections.

![image](https://user-images.githubusercontent.com/19898602/143274327-7f91d4e8-8dff-4abf-9339-e8ae24205b61.png)


> Connect CLK pin of tm1637 with GP1 pin of pico.

> Connect DIO pin of tm1637 with GP0 pin of pico.

> Connect ground pin of tm1637 with ground pin of pico.

> Connect Vcc ground pi of tm1637 with Vbus pin of pico that is 5volt pin

> Connect push button as shown in figure.

There are two push buttons, One is for start counting and another is to reset pico.



# Coding

To write and upload program here i used Thonny IDE. You can download from here.

Here i write code in micropython.

`````
from machine import Pin
import time
import tm1637

tm = tm1637.TM1637(clk=Pin(1), dio=Pin(0))
Button = Pin(2, Pin.IN)

a = 0
b = 0

tm.numbers(a,b)

while True:
    if Button.value() == 1:
        while True:
            tm.numbers(a,b)
            b = b+1
            if b > 59:
                b = 0
                a = a+1
            time.sleep(1)
            
            
``````

Save this code in Raspberry Pi Pico and and name it main.py


Before moving fuurther I would like to tell you something about PCB

Yes PCB are the heart of the electronics based project usually we hesitate to try custom PCB and opt to homemade solutions

like breadboard or Zero PCB earlier I also was in the same boat, I hesitate to try custom PCB my belief was they are much expensive.

but then I came to know about [JLCPCB.COM](https://jlcpcb.com/IAT) and I was totally surprised how low price PCB's are they offering 

there PCB quality is best in market, now I always go with PCB for my project and [JLCPCB.COM](https://jlcpcb.com/IAT) is my trusted 

PCB manufacturer, you can also try there PCB service for more details you can visit their website [JLCPCB.COM](https://jlcpcb.com/IAT)
You can also try there new purple colour for PCB without any extra cost.
If new user signup today from this link [JLCPCB](https://jlcpcb.com/IAT ) you will get 30$ coupon from [JLCPCB](https://jlcpcb.com/IAT ).
![image](https://user-images.githubusercontent.com/19898602/134336832-cb9953e9-02a6-4ff7-9d27-2caad10fe7c7.png)
![image](https://user-images.githubusercontent.com/19898602/130722577-c30b7b43-ea89-4847-9c6b-058f9fabeda3.png)![image](https://user-images.githubusercontent.com/19898602/130722585-b5268db1-5f17-428f-ba60-b823140f2a70.png)



# 2 Interfacing PIR Motion Sensor with Raspberry Pi Pico

![image](https://user-images.githubusercontent.com/19898602/143274751-64f8c386-c289-4cbe-81e7-f37108585383.png)


Hello,

In this article we are going to interface Raspberry Pi Pico with PIR sensor module and make Anti-Theft Alarm.

If someone enter in room or anywhere sensor is place, sensor will detect human and trigger alarm.

Here, we used buzzer as alarm. If PIR sensor module detect human or animal body it will give signal to Raspberry Pi Pico and pico will turn on the alarm.

Let’s make this.

If you are new to Raspberry Pi Pico and wants to get started then click here, it is all about getting started with Raspberry Pi Pico.

# Required Components

List of required components is given below.

> Raspberry Pi Pico

> PIR Sensor Module

> Buzzer

> Jumper Wires

> Bread Board


# Schematic Diagram

Follow this schematic diagram and make connections.

![image](https://user-images.githubusercontent.com/19898602/143274907-9b9f9f26-0f0e-4cdd-99f1-dae97a16c15d.png)


> Connect Vcc of PIR sensor with 5V of Pico.

> Connect Dout pin of PIR with GP28 pin of Pico.

> Connect GND of PIR with GND of Pico.

> Connect anode pin of buzzer with GP15 Pin of Pico.

> Connect Cathode pin of buzzer with GND pin of Pico.

# Coding

To write and upload program here i used Thonny IDE. You can download from here.

Here i write code in micropython.

```

from machine import Pin

PIR = Pin(28,Pin.IN)
Buz = Pin(15,Pin.OUT)

while True:
    if PIR.value() == 1:
        Buz.high()
        
    else:
        Buz.low()


```

Save this code in Raspberry Pi Pico and and name it main.py




