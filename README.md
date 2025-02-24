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

# Firmware Description
The firmware controls the MS5351M and does the DSP filtering. The audio signal is sampled at 500 KHz which means the analog signal filtering is simpler because it just needs to sufficiently attenuate signals below 250 KHz. The sampling detector has a cut-off of about 16KHz and the op-amp has a cut-off of about 3.3KHz. Combined, the tuned audio is attenuated by about 100 dB at 250KHz which is more then enough, especially since the RP2350 has a 12 bit ADC only. The DSP then uses a 4th order 32 element moving average filter which is very cheap to calculate and provides at least 60 dB of attenuation from 15625 Hz. Now the signal can be decimated down to 31250 Hz (ie, 500000 / 16) which is the sample rate for the FIR filter and the audio output. The FIR filter has a cut-off of 2400 Hz for SSB. A band-pass filter is used for CW. Then AGC is applied which also drives the S-meter LED and finally the signal is converted to 12 bits for the audio output. The audio value is split into high and low 6 bits driving two PWM outputs, so that the PWM frequency is higher. Each PWM output now operates at (150 MHz / 64 =) 2.3 MHz. A resistor network consists of 100K and 1.5K (ie 64 * 1.5K ~ 100K) so the correct weighting is applied to the high and low order bits. Volume is controlled using a PWM output signal driving the volume input of the LM4875.

![alt text](https://github.com/ianm8/uDCR2/blob/main/docs/uDCR2-Top.jpg?raw=true)

![alt text](https://github.com/ianm8/uDCR2/blob/main/docs/uDCR2-Bottom.jpg?raw=true)
