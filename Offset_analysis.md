# Offset of single stage amplifier

We are done looking at the stability of it!
We have done so far:
* Gain of the opamp (without caps first, like Gm·Rout etc)
* Freq response & Stability (with parasitic caps, so Ym(s), and we did the Bode plot)

Now it’s time to look at the other non-idealities:
* Offset
* Noise
* Swing limits
* Slew Rate

## Offset

The **INPUT-REFERRED OFFSET** is what we are interested in. This is **the INPUT VOLTAGE FOR WHICH THE OUTPUT WILL BE ZERO**.

It comes because M1 & M2 are not identical, also M3 & M4 are not identical.

Instead of calculating the output voltage (difficult) the way to do it is by calculating the current going out of the output, that goes into a certain load impedance, and we get the voltage from that. It´s a lot easier that way.

**Two assumptions in Offset calculation are:**

1. **WE ASSUME THE GDS´s are SUFFICIENTLY SMALL.** We only do this because otherwise the offset calculation becomes too complicated (unnecessary). And the answer will be correct, or a good approximation, anyway.

2. **WE ASSUME THERE IS ONLY VTH MISMATCH (NO CURRENT FACTOR MISMATCH).** Again this is to make the calculation manageable. It is possible to add the current factor mismatch, not too difficult to do, you would just add a current source in parallel with each transistor which represents/injects the current factor mismatch. But we won´t do it here.
 
3. **We will do again the “TERMINATION VOLTAGE SOURCE TRICK”** at the output, where Vterm=VDD-Vsg3 so both M3 and M4 see the same VDS, so in STATIC STATE (quiescent bias current state, no Vd input) both branches are EXACTLY BALANCED and NO CURRENT flows out to the output.



We first analyze offset for the effect of M1 & M2, then for M3 & M4, then we add up contributions, then finally we take RMS values for variance.

![image](https://user-images.githubusercontent.com/95447782/169098640-5b0b39be-fbf5-49cb-8c3c-121c7ffaefb7.png)


Insight at this point:
* For overall offset:
* Contribution of M1 & M2 we cannot avoid it (with circuit techniques, all you can do is make them larger in layout as in INCREASE THEIR AREA W·L).
* Contribution of M3 & M4 we can reduce it if we make gm1 > gm3.

This makes sense intuitively. The input pair devices translate input differential voltage to current (M1 & M2 mismatch here causes a current mismatch) and the current mirror devices mirror that current but add some current mismatch of their own.


How to calculate specific offset values: Take sigma_squared expression and replace the individual sigma_Vt values by the Pelgrom model, using the Avt values which you can get from process information.

![image](https://user-images.githubusercontent.com/95447782/169098711-ceee9892-5f27-4b88-9754-66b5a9ea2c30.png)


This concludes Offset analysis.


Next thing is Noise.


## Noise

Next:

* [Noise](Noise_analysis.md)
