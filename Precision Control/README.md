# Precision Control
It makes sense that one would be able to alter the output voltage or current in a handmade circuit. In a practical application, it is important for a system to be responsive to the user and as accurate as possible. The goal of this section is to change the outcome of the circuit to whatever value the user desires.

## PWM
Since the PWM code has already been created in a previous lab, all that really leaves is the hardware aspects. 

## R2R DAC
Sometimes a system needs to be more accurate than it currently might be, for purposes of measurements or precision. One way to fix this issue is to use a DAC, or digital to analog converter.
![R2RDAC](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/R2R_DAC.png)

The picture above shows a standard DAC used in this lab. A DAC consists of several matching resistors in series with one another, and another set of different value matching resistors coming from several different sources, that meet up with the original resistors. In this case, we used 1k resistors strung together in series, and 2k resistors branching onto them, as well as a 2k resistor at the end.

## Loading Effects
Once the DAC is completed and operational, it is important to add a load that can test the capabilities of the system. This can be simulated by placing different valued resistors at the end of the circuit.
![R2R1MEG](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/triangle1meg1.png)

The graph above shows what happens when a 1M ohm resistor was placed at the end of the DAC. A perfect triangle wave was returned on the oscilloscope, which shows the DAC steadily climbing and decreasing. It is a triangle wave because the rate that the DAC is climbing and the rate it is falling are the same, which creates peaks on the graph.
This process was repeated for several resistors with decreasing values, which smaller, but just as steady, triangle waves.

## FFT 
![R2RFFTnoload](https://github.com/RU09342/lab-6taking-control-over-your-embedded-life-kevinandnathan/blob/master/Precision%20Control/trianglefft1.png)

The FFT graph above shows the frequency response from 0 to 50kHz.

## Bill of Materials
| Materials                 | Usage    	     | 
| ------------------------- | -------------- | 
| Resistors: 1M, 470k, 820k | Load testing   | 
| 7 1k Resistors            | R2R Series     | 
| 9 2k Resistors            | R2R Parallel   | 
| 2 10k Resistors           | LPF Unity Gain |
| 1 100nF Capacitor         | LPF Capacitor  |
| 1 LM324 Op Amp            | LPF Op Amp     |


