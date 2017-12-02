Lab 6: "High Power" Control
The high power control describes the methods that we are going to be controlling a 12 volt DC fan. While 12 volts isn’t technically high power the current and voltage draw of this device cannot be driven using the power delivered by our launchpad boards which is more designed to allow for computer logic functions. In order to properly control the fan we need to change the voltage and current being delivered to the fan. This can be done using a pwm signal and a “switch” device that can turn on and off the power from an external source to the fan based on our logic level PWM signal.
Switching
There are 2 devices we examined for switching power to the fan in our system a relay and a mosfet.

A relay is a mechanical switch that allows for switching between open and closed, depending on the current input on an inductor in the relay. Relays are useful because they can handle larger amounts of current, but do generally need a voltage higher than 3.3V supplied by the launchpad leaving us with the same issue as before. 

A MOSFET, specifically an NMOS, is used to control the current going through the circuit. Applying a voltage difference to the gate allows the flow of current from the drain to the source. This allows us to not only control the fan but also to control the relay.

Lastly, the MSP430G2553 is used simply to toggle the NMOS via a PWM signal because the microprocessor can be removed from the launchpad and replaced from the tech office.
Usage

The first circuit set up was the relay circuit. The purpose of this circuit was to show that the MSP boards cannot drive high power circuits on their own, and must use external sources for help. Relays are able to handle extremely high levels of current flowing through them. This is done to attempt to prevent damage to the MSP430G2553 while still allowing the usage of the switch mechanism itself.

The MOSFET circuit, on the other hand, was used to show other alternatives to the relay that allow for switches, without the need for extremely high current in a circuit.  The low need for current in a MOSFET makes it desireable over a relay in some cases, especially when working with low-level equipment, such as the MSP’s that cannot handle very high levels of current.

