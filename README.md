# Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib
### AIM
    To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries.   
### APPARATUS REQUIRED
1.	Software: Python with NumPy and Matplotlib libraries  
2.	Hardware: Personal Computer  
### THEORY 
Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier wave is varied according to the instantaneous amplitude of the message signal. The general form of an FM signal is:


<img width="508" height="200" alt="image" src="https://github.com/user-attachments/assets/d69f6e8c-de84-4ee7-886b-0dc349407e29" />


### ALGORITHM

1.	Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and frequency deviation.    
2.	Generate Time Axis: Create a time vector for the signal duration.  
3.	Generate Message Signal: Define the message signal as a cosine wave.  
4.	Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.  
5.	Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.  
6.	Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

### PROGRAM
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import hilbert


Ac = 17.2
Am = 8.6
fc = 8430
fm = 843
fs = 84300
t = np.arange(0, 2/fm, 1/fs)


m = Am * np.cos(2 * np.pi * fm * t)    
c = Ac * np.cos(2 * np.pi * fc * t) 
s = (Ac + m) * np.cos(2 * np.pi * fc * t) 


env = np.abs(hilbert(s))  
m_demod = env - np.mean(env)  


plt.figure(figsize=(10,8))

plt.subplot(4,1,1)
plt.plot(t, m)
plt.title('Message Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

plt.subplot(4,1,2)
plt.plot(t, c)
plt.title('Carrier Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

plt.subplot(4,1,3)
plt.plot(t, s)
plt.title('AM Modulated Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

plt.subplot(4,1,4)
plt.plot(t, m_demod)
plt.title('Demodulated Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

plt.tight_layout()
plt.show()
```

### TABULATION
![WhatsApp Image 2025-11-23 at 11 46 13_361a2373](https://github.com/user-attachments/assets/646c17d6-e1c9-476c-ad49-b015ab9bc4da)

### OUTPUT
<img width="989" height="790" alt="AC EXP8" src="https://github.com/user-attachments/assets/d3756d52-8ffe-46d6-af92-c5e423b5b96a" />

### RESULT
The message signal, carrier signal, and frequency modulated (FM) signal will be displayed in separate plots. The modulated signal will show frequency variations corresponding to the amplitude of the message signal.
