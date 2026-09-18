## IIR-FILTER-DESIGN
## EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM: 

```sci
clc ;
close ;
wp=input('Enter the pass band frequency (Radians )= ' );
ws=input('Enter the stop band frequency (Radians )= ' );
alphap=input( ' Enter the pass band attenuation (dB)=' );
alphas=input( ' Enter the stop band attenuation(dB)=' );
T=input('Enter the Value of sampling Time=');
//Pre warping- Bilinear Transformation
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');
//Order of the filter
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
//Cut off frequency
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N)));
disp(omegac,'omegac=');
disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);
disp('Analog LPF Transfer function H(S)=');
hs= analpf(N,'butt',[0,0],omegac);
disp(hs);
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);
HW=frmag(Hz,512); // Frequency response
w=0:%pi/511:%pi ;
plot(w/%pi,abs(HW));
xlabel(' Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```
## CALCULATION

<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/88ad6392-7708-4c17-86e6-c2f082d5ee1a" />
<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/ee84ce12-ea7a-4596-9451-9cbbe6c9d4ea" />

## OUTPUT:

<img width="475" height="632" alt="image" src="https://github.com/user-attachments/assets/f6304d54-1070-4e46-a954-89dbcc9f81c8" />
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/18d5019e-c76a-4a36-9c30-8df57264e5e3" />

## RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.
