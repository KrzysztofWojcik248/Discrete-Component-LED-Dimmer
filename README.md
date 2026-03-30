# Discrete-Component-LED-Dimmer
Simple project about controlling LED's brightness without using microcontroler and integrated circuits.

## Project Motivation:

At the begining, I didn't think about making full project. I was just curious about changing LED's brightness using only buttons and discrete components. When an idea came to my mind, I needed to design a schematic. Finally having a schematic made me ended up with working project.

## How It Works:
The primary challenge of this project was to transform a momentary signal into a constant state without using integrated memory circuits. This system uses capacitor which stores charge giving constant, but adjustable voltage. One side of capacitor is connected to the ground and the other side to two buttons - one goes to power supply, and the second one goes to ground. It makes capacitor voltage adjustable in range of this two electric potentials. Resitance near buttons and capacitor capacity are big enough to prevent instantaneous charging of the capacitor, so getting desired brightness is not difficult. Then voltage output goes in to base of first transistor. There are two of them as **Darlington pair** because current going into base of only one transistor would discharge the capacitor, making output unstable. The second transistor's collector is connected to the LED, and its emitter is tied to a resistor that determines the collector current based on the base voltage. This arrangement multiplies the transistors' $h_{FE}$, ensuring high input impedance.

## Calculating values

LED needs 20mA current to provide full brightness and power supply is 9V battery. I decided to use 1000μF electrolitic capacitor because it's big enough to provide stable output and as trainsitor I use NPN 2N2222.

### Calculating second's transitor emitter resistance:
I assume that colector current is the same as emitter current because base current is 100-300 times smaller than collector current so I calculated this current using emitter current formula:

$$I_E = \frac{V_{BE}}{R_E}$$

The maximum volage provided by capacitor is 9V but because of the Darlington pair this voltage goes two times trough emitter–base junction we need to subtract voltage drops:

$$V_BE=9V-2*(0.7)=7.6V$$

#### Now we can find $$R_E$$

$$20mA = \frac{7.6V}{R_E}$$ $$R_E = 380Ω$$
