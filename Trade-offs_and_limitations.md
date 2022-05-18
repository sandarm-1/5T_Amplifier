# Design trade-offs and limitations of single stage amplifier

## Design trade-offs and limitations of this topology

Trade-offs in terms of Offset and Noise reduction:

![image](https://user-images.githubusercontent.com/95447782/169100689-9d159184-2f5a-48d4-b946-c8bcfd95ac02.png)


For Noise, the trade-offs are:

![image](https://user-images.githubusercontent.com/95447782/169100716-b53fb947-3667-4620-bc6f-05a2a24c1e2f.png)


We would work iteratively to arrive to a final design that gets as close as possible to the specs we need.

More trade-offs for this topology:

* For **HIGH SPEED operation**, you will operate the transistors at higher and higher OVERDRIVE (strong inversion), i.e. higher VGS-VT. That is from the formula of the TRANSIT FREQUENCY of the transistor, ft. And large VGS-VT means large VDSAT.
* For **LOW POWER operation**, you will use small currents and very large transistors. This will increase parasitic caps so your non-dominant pole will move to lower frequency, so to preserve stability you will have to reduce unity-gain frequency omega_u which=gm1/C which means using larger cap on output or less gm1, overall you will have a slower circuit. Also, when you have a large transistor (as in large W/L) with small current through it, that will have a low overdrive, low VGS-VT, which will mean Low Slew Rate capability, so low speed.

So overall, HIGH SPEED will require the opposite of LOW POWER.

## Limitations of the single stage amplifier

Single stage op amp has some limitations:

* **You cannot operate it with resistive loads**, just capacitive loads (like an integrator), because it will drop the DC gain because DC gain is Ao=Gm·Rout and if you put a resistive load in parallel with this amp’s Rout you will drop the Rout, dropping the DC gain. We don´t want that because lower DC gain will mean larger steady-state error.
* The **overall DC gain that we can get from this is quite limited**, it’s not huge. It’s gm1/(gds1+gds3) and that is in the order of magnitud of the gain of a single transistor (single transistor gain Av=gm·rds).
* To increase the DC gain of this amp, you would have to increase the rds1 & rds3. We know rds of transistors depends on channel length, longer device is more resistive. But if we increase L of devices, we will also have to increase W proportionally to keep W/L, since we don’t want to change gm1. So overall we will end up increasing the overall size of transistors which will increase parasitic caps and will reduce speed. Even if we don’t care much about speed, and we want to go down this route of increasing L to get some extra DC gain, we cannot increase L by 100 times, so it will be quite limited anyway.
* The way to increase DC gain from this circuit is to use cascodes, both on input pair and on loads, and that leads to **the TELESCOPIC amplifier** and the **FOLDED CASCODE amplifier**.


