---
title: 1 MHz Transistor Design
layout: page
permalink: pierce/1mega-design
parent: Pierce Oscillator
---
# 1MHz Transistor Design
This brief article covers the design of a 1MHz Oscillator which uses BJTs. It was mostly designed with the help
of the design tool, only differing in the use of an inductor instead of a resistor at the collector and the addition
of a common collector buffer.

Using an inductor is particularly useful when supply voltages are low, since it aids in DC biasing by eliminating
the voltage drop a resistor would cause, which saves precious headroom to keep $$V_{CE}$$ out of its saturation
region. The inductor behaves as a resistor at AC frequencies which provides the gain needed to drive the oscillator.

A common collector buffer was added to isolate the oscillator. A DC offset already exists at the base so to bias
it only a constant current source was added. Normally a small signal diode would be used, but all that was available
at the time of its creation were rectifier diodes. The current source was designed to sink 4mA.

## Schematic
{% include figure.html
file="assets/img/pierce-1mhz/schematic.png"
caption="Schematic for 1MHz Pierce Oscillator with CC buffer."
%}

## Soldered Board
{% include figure.html
file="assets/img/pierce-1mhz/board.jpg"
caption="Soldered 1MHz Pierce Oscillator without any buffer."
%}

{% include figure.html
file="assets/img/pierce-1mhz/board-buffer.jpg"
caption="Soldered 1Mhz Pierce Oscillator with the CC buffer."
%}

## Results
### Waveforms
The output signal is not the same depending on where you take it from. This is important, and comparisons can be
seen in Matthys' book. The waveforms I obtained were very similar to the ones shown in his book:

{% include figure.html
file="assets/img/pierce-1mhz/base-wave.png"
caption="Output taken from the BJT's base."
%}

{% include figure.html
file="assets/img/pierce-1mhz/collector-wave.png"
caption="Output taken from the BJT's collector."
%}

### Frequency Spectrum
The waveform at the base of the transistor looks quite good, almost as a perfect sinusoid. But the frequency
spectrum shows otherwise:

{% include figure.html
file="assets/img/pierce-1mhz/base-fft.png"
caption="Output taken from the BJT's collector."
%}

{% include figure.html
file="assets/img/pierce-1mhz/base-fft-markers.png"
caption="Output taken from the BJT's collector."
%}

At least there first harmonic is 30dBV down, but it's still not a pretty sight.

## Conclusions
Depending on the application this oscillator might be good enough. It certainly is for at home experimenting, but
is junk for any commercial application. Mexico's Regulation for AM transmission states the carrier must not divert
by more than 10Hz (IFT-001-2015), so this oscillator being at 1.00013MHz (130Hz off) would not make the cut. 

I am still pleased with the results, specially with it being the first iteration, and it served me well as the carrier
for my first amplitude modulator prototype. Further investigation on the harmonics is needed.
