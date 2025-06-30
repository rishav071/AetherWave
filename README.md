# AetherWave: A Contactless Musical Synthesizer

## Introduction:
AetherWave is based on the principle that the human body introduces variable capacitance when in proximity to an electromagnetic field. By tracking these changes, the circuit modulates audio signals in real time.

Pitch is controlled by how far your hand is from one antenna.

Volume is shaped by your hand’s position relative to a second antenna.

Together, they let you “play the air” like an instrument.




## Methodology:
### Frequency Block:
A high frequency Colpittis Oscillator of 400KHz built using LM358 opamp was used to detect the change in capacitance of the tank circuit by taking advantage of the parasitic capacitance of humans. The antenna acts as the first plate and the player's hand as the second, hence by changing the distance of the player's hand from the antenna, he changes the effective capacitance of the Colpitts oscillator tank circuit. It is designed to change its frequency by not more than 20KHz.

Now by mixing this signal with a sine wave of frequency same as that of the tank circuit (without the player's hand). We extracted two waves of frequencies. The first one has a frequency equal to the sum of the frequencies of the two signals and the second one has its frequency equal to the difference between the frequencies of the two signals. The lower frequency wave can be extracted by just passing the signals through a low pass filter. It is to be noted that this obtained wave has a frequency less than 20Khz (Since the Oscillator is designed to not change more than 20KHz) and hence in audible range. 

### Amplitude Block:
Now we mirror the frequency block and connect its output to a Butterworth Salen Key low pass filter (A second order, active filter ) with a very low cut-off frequency so that the frequencies of audible range lie on the transition band. Since the frequencies lie on the rapidly falling slope of the graph, each frequency will be associated with a specific DC gain (or I guess attenuation would be a better word). Now that we assigned a voltage to a frequency we integrated it with a Voltage Controlled Amplifier . Hence now we control the gain by varying the player's hand's distance from the antenna.


