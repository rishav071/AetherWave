# AetherWave: A Contactless Musical Synthesizer

## Introduction:
AetherWave is based on the principle that the human body introduces variable capacitance when in proximity to an electromagnetic field. By tracking these changes, the circuit modulates audio signals in real time.

Pitch is controlled by how far your hand is from one antenna.

Volume is shaped by your hand’s position relative to a second antenna.

Together, they let you “play the air” like an instrument.




##Technical Architecture
### Pitch Control Module
A Colpitts oscillator, operating around 400 kHz, is implemented using an LM358 op-amp.

The oscillator circuit includes an antenna that functions as one capacitor plate, with the player’s hand acting as the opposing plate.

As hand distance changes, capacitance shifts, subtly altering the oscillator's frequency (limited to a ±20 kHz range for stability).

This changing signal is mixed with a stable reference sine wave (baseline oscillator frequency with no hand nearby).

The mixing process creates two components — one at the sum and one at the difference of the input frequencies.

A low-pass filter isolates the difference frequency, yielding a signal in the audible frequency range (<20 kHz) that becomes the musical pitch.

### Volume Control Module
A mirrored sensing setup detects hand movement near a second antenna to modulate volume.

This signal is processed through a Sallen-Key low-pass filter (2nd order Butterworth), configured with a sharp transition zone.

Frequencies falling into the transition region experience varying attenuation, which converts them into a control voltage.

The filtered output is passed into a Voltage-Controlled Amplifier (VCA), where it dynamically adjusts the gain applied to the audio signal.

As a result, volume increases or decreases smoothly based on hand proximity.

## Prototype Implementation
The entire circuit was assembled and tested on a breadboard, allowing flexibility for experimentation and iterative improvements.

Component values were fine-tuned through real-world testing.

Audio signals were monitored via speaker/headphone output.

Functionality was verified using signal analysis tools (oscilloscope/frequency counter).
