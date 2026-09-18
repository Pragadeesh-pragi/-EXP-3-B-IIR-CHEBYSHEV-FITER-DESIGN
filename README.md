# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```sci
clc; 
clear; 
close; 
// Input specifications 
wp = input('Enter the pass band frequency (Radians)= '); 
ws = input('Enter the stop band frequency (Radians)= '); 
alphap = input('Enter the pass band attenuation (dB)= '); 
alphas = input('Enter the stop band attenuation (dB)= '); 
T = input('Enter the sampling time = '); 
// Convert digital frequencies to analog frequencies
omegap = wp/T; 
disp(omegap,'omegap='); 
omegas = ws/T; 
disp(omegas,'omegas=');
 // Calculate filter order 
N = log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
disp(N,'N='); 
N = ceil(N); 
disp(N,'Rounded value of N='); 
// Cutoff frequency 
omegac = omegap/((10^(0.1*alphap)-1)^(1/(2*N))); 
disp(omegac,'omegac=');
 // Normalized Analog LPF 
disp('Normalized Analog LPF Transfer Function H(s)'); 
Hs_normal = analpf(N,'butt',[0,0],1); 
disp(Hs_normal); 
// Analog Butterworth LPF
 disp('Analog LPF Transfer Function H(s)'); 
Hs = analpf(N,'butt',[0,0],omegac); 
disp(Hs); 
// Impulse Invariant Transformation 
Hz = dscr(Hs,T); 
disp('Digital LPF Transfer Function H(z)'); 
disp(Hz);
 // Frequency response 
HW = frmag(Hz,512);
 w = 0:%pi/511:%pi; 
plot(w/%pi,abs(HW)); 
xlabel('Normalized Digital Frequency'); 
ylabel('Magnitude');
 title('Frequency Response of Butterworth IIR LPF using Impulse Invariant Method');
```
## CALCULATION

<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/d4ffdf33-803f-490e-8dec-c10d797b23d2" />
<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/8b023a35-812e-4b02-89a7-eaaa8aa8769e" />
<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/abb7e32a-a173-4752-b0aa-9269bbbfe145" />

# OUTPUT: 

<img width="707" height="652" alt="image" src="https://github.com/user-attachments/assets/e19d6f8a-9cb1-4b4e-aa64-ef1121e42766" />
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/1d81a03f-2f1d-4659-ad64-abf959b26b98" />

# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
