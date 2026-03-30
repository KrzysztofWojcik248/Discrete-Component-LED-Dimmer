# Discrete-Component-LED-Dimmer
Simple project about controlling LED's brightness without using microcontroler and integrated circuits.

## Project Motivation:

At the begining, I didn't think about making full project. I was just curious about changing LED's brightness using only buttons and discrete components. When an idea came to my mind, I needed to design a schematic. Finally having a schematic made me ended up with working project.

## How It Works:
The biggest difficulty in figuring this out is how to transfer momentary button signal into constant in time output value without any typical memory components. But you can think about capacitors as elements memorizing information - voltage. Using properly big capacitor and resistors you can make the time of loading actually noticable. When you connect big capacitor from one side to ground, and the other side is contected by buttons and resistors to gnd and power supply you can control voltage using buttons. So now we can store power, but another problem is that LED diode can consume this power in seconds. So we cant't connect diode to capacitor, we have to use voltage on capacitor as an information for other elements - transistors. You can use transitor as a current sources if you place resistance on emiter, and voltage on base which is great for controling LDS's! 



