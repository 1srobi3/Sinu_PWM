# Sinu_PWM

A PWM signal with a frequency of 31250Hz will be generated on the PD7 pin. The fill factor of the PWM signal will be varied according to the shape of a sinusoidal signal in the range [0, 1] using the corresponding values in the range [0, 255].Of course, the resulting analog signal will be delayed until it stabilizes and the signal will oscillate around the desired output value. This oscillation depends on the R and C values of the filter. To reduce the amplitude of the oscillations we can either increase the values of R and C, or increase the frequency of the PWM signal. 
 After filtering the PWM signal through an low pass-filter circuit, a sinusoidal signal will result. 
To generate the sine signal, a vector with discrete sine values over a period will be defined. 
The fill factor of the PWM signal is set in the OCR2 register with the generated values. The period chosen for the sine signal is 1/1Hz, this results in a sampling period of 50 ms. The following code will appear in the ISR function of Timer 1. 
Because the frequency of the PWM signal was set to 31250Hz and taking into account the above, we will choose the cutoff frequency of the RC filter in the range [312, 3125] Hz. The values R and C will be chosen in such a way that their product is within the mentioned range. 
