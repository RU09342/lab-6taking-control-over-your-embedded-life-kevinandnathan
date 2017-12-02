# Lab 6: Open Loop Systems
An open loop system is one that is directly controlled by user input, as opposed to being dependent on an equation or code function to properly operate. Any time a circuit asks for a value or character from an outside source, such as a person using code for example, it is considered an open loop circuit.
# Voltage Regulator
A 5 volt regulator is a device that is able to provide 5 Volts while taking in up to 20 volts. The regulator produces heat which is how the additional current and volt are removed from the device so depending on what the regulator is powering the excess power being drawn from the power supply will become heat that we use to raise the temperature so we have something to cool with the fan. 
# Board Selection
The board we chose to use for this section was the MSP430FR6989. This board was chosen because of its built-in LCD display screen, which was used to visually show the temperature changing as an ADC value. We avoided adding conversion code that would slow down our temperature readings. For the load on the regulator output we had a 5 Watt 100 ohm resistor that gave us a good temperature range for the lab requirements.
# Fan Control
![Open Loop Schematic](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Open%20Loop%20Systems/OpenloopSchematic.PNG)

The fan we chose to operate within our circuit ran off of 12 volts, which is well above the capacity of the MSP4306989. We used a NMOS mosfet to switch the power supplied from to the fan on and off with a PWM signal. The duty cycle would essentially control when the fan was on and off which could be pretty noisy if the fan was being switched at a fast rate. We placed the fan directly head on, facing the circuit perpendicularly, to make sure the 5 volt regulator got as much cooling as possible.

# Temperature Reading
As stated above, the 6989 was chosen because it is able to display numerical values and characters on it’s built in LCD display screen. We used this to our full advantage and displayed the changing ADC values from the temperature sensor on the screen for ease of access. The targeted temperatures for this lab were achieved by using a conversion from degrees celsius to PWM value based on the duty cycle from 0 to 100%. The conversion equations are shown below where Y is duty cycle and X is degrees celsius. The equations would need to be multiplied by 2.55 to be converted to PWM for our coding purposes and we had an upper temperature range equation which is the first equation for 90-50 degrees celsius and a lower range equation which is the second equation for 50-35 degrees celsius. The equation was split like this to create a better fit for the data we recorded.

(1) y = -0.2533x + 22.449

(2) y = 0.3368x2 - 34.397x + 888.18
 
# System Modeling
The lowest temperature achieved by the regulator when the fan was running at maximum PWM was about 35 degrees Celsius. When the fan was off, the regulator easily heated up to about 100 degrees Celsius. This became too high, however, and the regulators internal trip went off and the temperature began to decrease on its own again.

By looking at the chart above, it can be seen that 5 degrees Celsius is a change of about 62 AD. This can be used to calculate values above and below those that appear above.
