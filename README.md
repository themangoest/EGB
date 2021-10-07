# EGB
Power supply: 5V 55mA (12V operation is possible with the arduino power supply circuit)
Waveform: log / exp, Bezier curve, inverse log / exp
A / D period: 8ms-4min
Amplitude: 0-5Vp
EG mode and LFO mode can be selected with the -p switch.
With manual trigger


The characteristic is the Bezier curve.
As far as I know, there is no commercially available module that outputs this curve.
The reason for the Bezier curve is that the mathematical formula is relatively simple (described later) and it is possible to draw an organic curve. Sometimes I wanted to add my own original elements.

Since the program
waveform is a curve, the formula is complicated to process with Arduino.
Therefore, we decided to create a waveform in Excel in advance and refer to the numerical values ​​in the table.
Since the waveform is stored in the table, it is possible to output a completely different waveform.
Since the resolution is 10.5 Vp-p, it becomes a stepped waveform of 50 mV. As a result of the hearing test, it was judged that the resolution was sufficient.

The detection of the trigger IN was not an interrupt but a constant monitoring by digitalRead.
In rare cases, the operation becomes unstable when operating with interrupt control. If interrupts are frequent like EG, there is a high possibility of instability.
Therefore, the program is a little annoying, but I decided not to use interrupts.

The Bezier curve formula is difficult, but if the start point is fixed at (0,0) and the end point is fixed at (1,1), it can be approximated to a simple formula. I was able to refer to the web page below.


