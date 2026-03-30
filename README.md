# Discrete-Component-LED-Dimmer
Simple project about controlling LED's brightness without using microcontroler and integrated circuits.

## Project Motivation:

At the begining, I didn't think about making full project. I was just curious about changing LED's brightness using only buttons and discrete components. When an idea came to my mind, I needed to design a schematic. Finally having a schematic made me ended up with working project.

## How It Works:
The primary challenge of this project was to transform a momentary signal into a constant state without using integrated memory circuits. This system uses capacitor which stores charge giving constant, but adjustable voltage. One side of capacitor is connected to the ground and the other side to two buttons - one goes to power supply, and the second one goes to ground. It makes capacitor voltage adjustable in range of this two electric potentials. Resitance near buttons and capacitor capacity are big enough to prevent instantaneous charging of the capacitor, so getting desired brightness is not difficult. Then voltage output goes in to base of first transistor. There are two of them as **Darlington pair** because current going into base of only one transistor would discharge the capacitor, making output unstable. The second transistor's collector is connected to the LED, and its emitter is tied to a resistor that determines the collector current based on the base voltage. This arrangement multiplies the transistors' $h_{FE}$, ensuring high input impedance.

## Calculating values

- LED needs a 20mA current to provide full brightness
- power supply is 9V battery
- I decided to use 1000μF electrolitic capacitor because it's big enough to provide stable outpu
- used transistor is NPN 2N2222.

### Calculating second's transitor emitter resistance:
***All the values and components which are calculeted and I'm refering to can be found on schematic in section below***

I assume that colector current is the same as emitter current because base current is 100-300 times smaller than collector current so I calculated this current using emitter current formula:

$$I_E = \frac{V_{BE}}{R_E}$$

The maximum volage provided by capacitor is 9V but because of the Darlington pair this voltage goes two times trough emitter–base junction we need to subtract voltage drops:

$$V_BE=9V-2*(0.7)=7.6V$$

#### Now $$R_E$$ can be found:

$$20mA = \frac{7.6V}{R_E}$$

$$R_E = 380Ω$$

### Calculating other currents:

hFE of 2N2222 is usually in range of 100-300 but I assume it as 100 (just in case) so if emitter current of Q2 (second transistor) is 20mA its base current would be 0.2mA which stands for Q1 emitter current. If Q1 emitter current is 0.2mA its base current would be only 2μA. Considering these currents I decided to put two safety resistors. R2 (2.2kΩ) limitates Q1   collector currents and drops collector voltage by ~0.4V which is far away from 9V of power supply. R3 (4.7kΩ) limitates Q1 base current in case of any short circuits, with typical current below 2μA won't be noticable.

### Choosing resitance near buttons
Calculating exact time of reachinig some voltage in this case is complicatead, because $$V_C(t)$$ **is not a linear function** we can calculate time to reach some part of $$V_{C_{MAX}}$$ but transition stll won't be linear. One RC stands for nearly 63% of maximum voltage, but to reach 95% of maximum voltage the time would be nearly 3*RC. Another problem is that discharging has inverted characteristic in comprassion to charging function. So to make operating on high brightness easy, discharging button should be tied to bigger resitance than charging button. I decided to put 1.8kΩ resistor near charging button which stands for charging to 63% in 1.8 seconds and 95% in 5,4 seconds of holding the button, and 4.7kΩ resistor near discharging to make operating on higher voltage easier.
## Schematic
This image featuers screenshot from KiCad where I designed schematic with calculated values.
<img width="1881" height="1243" alt="image" src="https://github.com/user-attachments/assets/00f0fc91-e434-41b2-a7f0-fd832bcc1576" />



