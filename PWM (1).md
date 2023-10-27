\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ 

Indian Institute of Technology, Kharagpur 

![](Aspose.Words.f24c0582-bf2f-459a-875f-c6603c25c856.001.png)

Department of Electrical & Electronics Communication Engineering 

Subject                      : Analog Communication Laboratory (EC39001)  

Course Instructors  : Dr. Jithin Ravi   

`           `Dr. Pechetti Sasi Vinay \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ 

Experiment 7: PULSE WIDTH MODULATION 

![](Aspose.Words.f24c0582-bf2f-459a-875f-c6603c25c856.002.jpeg)

ABOUT THE CIRCUIT 

- PWM  circuit  consists  of  a  Sawtooth  Wave  Generator  and  a  Voltage Comparator. 
- Saw-tooth Wave Generator: -  741 Op-amp is configured as an integrator to transform a repetitive pulse signal into a sawtooth signal. 
- Voltage  Comparator:  IC  710  is  a  voltage  comparator  IC,  which  compares Sawtooth signal amplitude level with the amplitude of modulating signal. 
- The demodulation can be done with a low pass filter. 

PROCEDURE 

1. Set a pulse signal (frequency fc = 10KHz, Amplitude = 5V and duty cycle = 20%) as carrier for modulator. 20% Duty cycle implies if Pulse period = 0.1 mS, then Pulse width should be 0.02mS. 
1. Set a sinusoidal signal of frequency fm = 1 KHz, Amplitude = 4Vpp as modulating signal. 
1. Fed  the  carrier  pulse  signal  to  the  integrator  circuit  and  observe  the  output  of Integrator as sawtooth signal of frequency same as 10 KHz. (Output Waveforms as like in figure -2). 
1. Now built a comparator circuit using IC 710. Provide modulating signal to inverting input and sawtooth signal to non-inverting i/p of Comparator. 
1. Observe the comparator output on the oscilloscope. (Output Waveform as like in fig - 3). 
1. Build a low pass filter to demodulate the modulated signal. (Output Waveform as like in fig-4).  

INPUT & OUTPUT WAVEFORMS 

![](Aspose.Words.f24c0582-bf2f-459a-875f-c6603c25c856.003.jpeg)

Fig -1 (a) Carrier Pulse Signal    (b) Modulating Signal 

![](Aspose.Words.f24c0582-bf2f-459a-875f-c6603c25c856.004.png)

Fig- 2.  Sawtooth Output w.r.t Pulse Input 

![](Aspose.Words.f24c0582-bf2f-459a-875f-c6603c25c856.005.png)

Fig – 3. Pulse Width Modulated Output w.r.t. Input Modulating Signal. 

![](Aspose.Words.f24c0582-bf2f-459a-875f-c6603c25c856.006.png)

Fig – 4 Demodulated Output w.r.t pulse width modulated input. 
