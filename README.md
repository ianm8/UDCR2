# uDCR2
A DC receiver with DSP and frequency announce. This is an updated version of the uDCR receiver. It tunes from 3.5 MHz to 15 Mhz. This version uses DSP for signal filtering which simplifies the circuitry. There are now fewer components compared to the uDCR. The most significant change is that the frequency is announced using an AI generated voice. When you pause tuning, after a 2 second delay, the frequency, in megahertz to the nearest KHz, is announced. Here is a summary of its features:

* XIAO RP2350
* TCXO frequency stability
* Floating point DSP
* SSB and CW filters
* AI voice frequency announce
* Effective AGC and S meter
* Mostly 0805 SM parts
* 60mm X 39mm PCB

![alt text](https://github.com/ianm8/uDCR2/blob/main/docs/uDCR2-Top.jpg?raw=true)

![alt text](https://github.com/ianm8/uDCR2/blob/main/docs/uDCR2-Bottom.jpg?raw=true)
