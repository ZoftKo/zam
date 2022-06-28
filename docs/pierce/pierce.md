---
title: Pierce Oscillator
nav_order: 2
layout: page
permalink: /pierce
has_children: true
math: katex
---
# Pierce Oscillator
Oscillators are vital for radio circuits. For the design of these the following resources were used:
* [Foundations of Oscillator Design by Guillermo Gonzalez](https://www.amazon.com/Foundations-Oscillator-Circuit-Microwave-Hardcover/dp/1596931620)
* [Crystal Oscillator Circuits by J. Matthys](https://www.amazon.com/gp/product/0471874019)
* [Pierce BJT Design Tool by devttys0](https://www.youtube.com/c/Analogzoo). His site is down, but I have uploaded
his design tool here.

For most if not all oscillators in this project, **quartz crystal oscillators** will be used, since they provide a great
frequency reference. 

Most if not all of them will also be **Pierce type oscillators**, since, based on Matthys'
and Guillermo's readings, they offer the best performance/simplicity trade off, in other words, **they have
good performance and are easy to build**.

From Foundations of Oscillator Design (talking about Clap, Colpitts and Pierce topologies): 
> The circuit biasing resistors and stray capacitances appear in shunt with
different elements in each of the three configurations. This makes the performance
of the three configurations different. The Pierce configuration is usually the most
desirable.

And from Crystal Oscillator Circuits:
> It has very good short-term stability because the crystal’s source and load impedances
are mostly capacitive rather than resistive, which give it a high
in-circuit Q. The circuit provides a large output signal and simultaneously drives the crystal at a low power level.

More in-depth explanations can be found on the resources listed above. The following just briefly explains all
the math behind designing the oscillator. This consists more or less of a transcript of devttys0's design tool source
code.

## DC Biasing
Let's quickly get over DC biasing. The biasing scheme is the same as the one used for Common Emitter (CE) amplifiers
with emitter degeneration.

![DC Biasing for BJT]({{ site.baseurl }}/assets/img/bjt-dc-bias.png)

$$
\begin{gather*}
V_B = V_{CC} * \frac{R_1}{R_1 + R_2} \\
I_{CQ} \approx I_{EQ} = \frac{V_B - 0.7}{R_E} \\
V_{CEQ} = V_{CC} - (I_{CQ}R_C) - V_E
\end{gather*}
$$

An inductor can replace $$R_C$$, making $$V_{CEQ} = V_{CC} - V_E$$ for DC biasing but acting as a resistor at the
Oscillation frequency.
