---
title: Transmitters
nav_order: 3
layout: page
permalink: /transmitters
has_children: true
math: katex
---
# Transmitters
This section covers transmitters. Transmitters will be treated as monolithic circuits which consist of the following
sections (some standards/regulations may vary by country):

* **Power Supply**. Should introduce as little noise as possible and satisfy all power requirements. Linear
supplies will be preferred since they are much easier to build at home and usually have very good noise
characteristics. It's AM, big chunky transformers go better with it, using SMPS is just too anticlimactic.
* **Local Oscillator**. Will produce the carrier wave. For commercial broadcast the frequency range goes from 540kHz 
to 1700kHz. The signal should meet the following specifications:
  * Waveform should be sinusoidal, with 50% duty cycle.
  * All harmonics should be at least 30dbV down from the fundamental.
* **Audio input.** In charge of  treating the modulating signal. AM stations have 10kHz bandwidth, while audio
signals usually have a bandwidth of up to 20kHz (audible range) which means the modulating signal should be filtered.
Generally frequencies above 5kHz are attenuated until they practically disappear at the 10kHz mark.
* **Modulator.** As its name implies, it produces the amplitude modulated signal. It  does this by mixing the carrier
with the audio input which is mathematically described like: $$(f_m + 1)f_c$$. Must provide a good modulation index
which we will define as 80-90%. Ideally automatic controls would be used to keep it stable. For most if not all projects
here, the MC1496 chip will be used. It is basically a Gilbert Cell driven with a current source.
* **RF Amplifier.** The modulator deals with small signals, the carrier and audio inputs are 300mV at max for the 
MC1496. Therefore, this amplifier is in charge of upping the power without distorting the signal.
* **Antenna.** Probably the most mysterious element. Not as straightforward to implement since it will be
electrically short. Will radiate all the energy provided by the RF amplifier, at least that is the plan.

Overall, as a design goal, I will be very pleased if I can ever transmit up to 250 meters. I don't know if I will
ever reach the goal, and I certainly hope I don't go to jail in the process.



