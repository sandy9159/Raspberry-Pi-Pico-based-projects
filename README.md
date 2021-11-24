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




