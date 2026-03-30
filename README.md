# Discrete-Component-LED-Dimmer
Simple project about controlling LED's brightness without using microcontroler and integrated circuits.

## Project Motivation:

At the begining, I didn't think about making full project. I was just curious about changing LED's brightness using only buttons and discrete components. When an idea came to my mind, I needed to design a schematic. Finally having a schematic made me ended up with working project.

## How It Works:
The biggest difficulty in this project is to tranform momentary signal into change of constant state of current without any integrated memory. This system uses capacitor which stores charge giving constant, but adjustable voltage. One side of capacitor  is connected to the ground and the other side to two buttons - one goes to power supply, and the second one goes to ground. It makese regulating capacitor voltage adjustable in range of this two electric potentials. Resitance near buttons and capacitor capacity are big enough to prevent instantaneous charging of the capacitor, so getting desired brightness is not difficult. Then voltage output goes in to base of first transistor. There are two of them as Darlington pair because current going into base of only one transistor would drain charge from capacitor, making output unstable. The second transitor's collector is connected to LED and its emitter is connected to resistor which determines colector's current depending on the voltage of the base. The base of second transistor is connected to emiter of first one, which makes them darlington pair and multiplies theiir hFE.



