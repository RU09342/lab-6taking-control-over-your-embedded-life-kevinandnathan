# Precision Control
It makes sense that one would be able to alter the output voltage or current in a handmade circuit. In a practical application, it is important for a system to be responsive to the user and as accurate as possible. The goal of this section is to change the outcome of the circuit to whatever value the user desires.

## PWM
Since the PWM code has already been created in a previous lab, all that really leaves is the hardware aspects. 

## Active Low Pass Filter
An active low pass filter was constructed in order to test the output of the system with an input driven by the processor which is outputting a PWM signal.

![lpfschematic](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/LowPassFilter.png)

The figure above displays the low pass filter schematic used. We went for unity gain through the use of two 10k resistors as well as a 100nF capacitor which gave a cutoff frequency of 159 Hz.
We ran a PWM signal of 50% duty cycle with an amplitude of 3.3V and received the following output signal:
![lpfpwm1](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/pmw50-uart1.png)

As displayed in the figure above, the output amplitude was 1.63V, which is approximately half of the input implitude, which corresponds to the theory.

## R2R DAC
Sometimes a system needs to be more accurate than it currently might be, for purposes of measurements or precision. One way to fix this issue is to use a DAC, or digital to analog converter.
![R2RDAC](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/R2R_DAC.png)

The picture above shows a standard DAC used in this lab. A DAC consists of several matching resistors in series with one another, and another set of different value matching resistors coming from several different sources, that meet up with the original resistors. In this case, we used 1k resistors strung together in series, and 2k resistors branching onto them, as well as a 2k resistor at the end.

## Loading Effects
Once the DAC is completed and operational, it is important to add a load that can test the capabilities of the system. This can be simulated by placing different valued resistors at the end of the circuit.

![R2R820](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/r2r-ladder-820k.png)

The figure above displays the output of the R2R DAC with 3.3V through the circuit. The output is a ramp function that is decreased in amplitude. We have more pictures of the output under different loads labeled accordingly.

![R2R1MEG](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/triangle1meg1.png)

The graph above shows what happens when a 1M ohm resistor was placed at the end of the DAC with a triangle wave input from the microprocessor. A perfect triangle wave was returned on the oscilloscope, which shows the DAC steadily climbing and decreasing. It is a triangle wave because the rate that the DAC is climbing and the rate it is falling are the same, which creates peaks on the graph.
This process was repeated for several resistors with decreasing values, which smaller, but just as steady, triangle waves.

The same was done with the low pass filter. The results are as follows:

![lpfpwmload](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/pmw50-uart-560k1.png)

The output of the low pass filter with a load higher than 560k displayed a flatline. The figure above displays the output with a load of 560k.
## FFT 
![lpffft](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/lpffft.png)

The figure above displays the FFT of the output of the lowpass filter. This displays the frequency response from 0 to 50kHz. As expected, it looks like a standard low pass response.

![R2RFFTnoload](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/trianglefft1.png)

The figure above displays the output of the unloaded DAC with a triangle wave input as well as the FFT of the system. The FFT graph above shows the frequency response from 0 to 50kHz.

## Bill of Materials
| Materials                 | Usage    	     | 
| ------------------------- | -------------- | 
| Resistors: 1M, 470k, 820k | Load testing   | 
| 7 1k Resistors            | R2R Series     | 
| 9 2k Resistors            | R2R Parallel   | 
| 2 10k Resistors           | LPF Unity Gain |
| 1 100nF Capacitor         | LPF Capacitor  |
| 1 LM324 Op Amp            | LPF Op Amp     |


