# Lab 6: Open Loop Systems
An open loop system is one that is directly controlled by user input, as opposed to being dependent on an equation or code function to properly operate. Any time a circuit asks for a value or character from an outside source, such as a person using code for example, it is considered an open loop system. These sytems cannot take in a feed back that would make continuous adjustments if the system isn't performing its function properly. 
# Voltage Regulator
![5 Volt Regulator pinout](https://www.electrical4u.com/images/2017/march/1489671183.png)

A 5 volt regulator is a device that is able to provide 5 Volts while taking in up to 20 volts. The LM 7805 was the 5 Volt Regulator used in this system its pinout can be seen in the picture above. The regulator produces heat which is how the additional current and volt are removed from the device so depending on what the regulator is powering the excess power being drawn from the power supply will become heat that we use to raise the temperature so we have something to cool with the fan. For the load on the regulator output we had a 5 Watt 100 ohm resistor that gave us a good temperature range for the lab requirements.
# Board Selection
The board we chose to use for this section was the MSP430FR5529. This board was chosen because we already had writen code for using UART to control the PWM of the fan so the conversion equation was the only additonal features needed for this board from a coding side.
# Fan Control
![Open Loop Schematic](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Open%20Loop%20Systems/OpenloopSchematic.PNG)

The fan we chose to operate within our circuit ran off of 12 volts, which is well above the capacity of the MSP4306989. We used a NMOS mosfet to switch the ground connection from to the fan on and off with a PWM signal. The duty cycle would essentially control when the fan was on and off by controlling current flow through the device which could be pretty noisy if the fan was being switched at a fast rate. We placed the fan directly head on, facing the circuit perpendicularly, to make sure the 5 volt regulator got as much cooling as possible. We had issues with the set up due to the noise but adding some additional space between the fan and circuit solved these interference problems.

# Temperature Reading
As stated above, the 5529 was chosen because we already had code written to send pwm values to it over UART which was a large part of what the code needed to do for the open loop system. The targeted temperatures for this lab were achieved by using a conversion from degrees celsius to PWM value based on the duty cycle from 0 to 100%. The conversion equations are shown below where Y is duty cycle and X is degrees celsius. The equations need to be multiplied by 2.55 to be converted to PWM for our coding purposes. We had an upper temperature range equation which is the first equation for 90-50 degrees celsius and a lower range equation which is the second equation for 50-35 degrees celsius. The equation was split like this to create a better fit for the data we recorded.

(1) y = -0.2533x + 22.449

(2) y = 0.3368x2 - 34.397x + 888.18
 
# System Modeling
In order to characterize the cooling effect of the fan on the 5 volt regulator we did this using the osciliscope to view the temperature on the LM35 temperature sensor as we ran the fan at different PWM duty cycles. The graph that we made of the temperature vs PWM can be seen below for 19 Volts across the 5 volt regulator and fan.

![19 Volt graph](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Open%20Loop%20Systems/19V.PNG)
