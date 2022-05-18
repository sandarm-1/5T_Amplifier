# Noise of single stage amplifier

## Noise

**Noise in the single-stage opamp (5T-OTA or differential pair with current mirror load).**

General strategy for noise:

* For each noise source, calculate contribution to output current, all other sources being 0.
* Sum all contributions (in an UNCORRELATED way) to get the overall output noise current. This is the overall noise spectral density of the current.
* Refer it to the input, simply dividing by the Gm^2 of the transconductor (just like with offset).

**The input referred noise (spectral density) is a model/representation of all noise sources in the circuit.**


Assumptions for noise derivations:
* Like for offset, we ignore the gds’s because it makes calculations cumbersome and doesn’t add much value. And usually doesn’t affect quantitatively the results much.


We start looking at noise contribution from M0:

![image](https://user-images.githubusercontent.com/95447782/169099082-44323a16-2881-4bae-8c84-f1649ff94291.png)

Now let’s look at noise contribution due to M3 and M4.


![image](https://user-images.githubusercontent.com/95447782/169099137-aed73b3b-4869-4e36-b443-00d9e0c4b786.png)
 

For M1 and M2 contribution, we apply a technique/trick:

![image](https://user-images.githubusercontent.com/95447782/169099148-1877a4f9-c092-48a9-9caa-a7d7a1d0a7f0.png)


Same thing happens for M2 if we do the analysis.

Finally we can add up all noise contributions and we get:


![image](https://user-images.githubusercontent.com/95447782/169099165-d2b3a73b-44c0-4797-800e-c83ad3d0c336.png)


We have thus calculated the **overall input referred noise voltage source.**

This calculation ignores the frequency dependence of noise. But it’s still useful like that. If you want to calculate the frequency dependence of noise you would probably go to the simulator.

![image](https://user-images.githubusercontent.com/95447782/169099206-778e7ef2-5788-4a09-81f1-0a26a9868212.png)


Observations about NOISE for this circuit (basic single stage amp, 5T-op amp, diff pair with current mirror load):
* 1st part of expression is 16/3·KT/gm1. That’s about equivalent to 2 MOSFETs, since one MOSFET’s noise, referred to its VGS, is 8/3·KT/gm. Since we have 2 transistors at the input with gm1, that’s why we get the 16/3·KT/gm1 contribution from those. No way to reduce it by circuit techniques, other than bias the transistors at a point which has less noise (higher gm1, which requires more current on them).
* 2nd part of the expression is related to the load and it has the gm3/gm1 factor again (same as with the OFFSET). Again this shows that by making the gm3 of the loads much smaller than the gm1 of the input device we can reduce this component.

That’s the end of the NOISE analysis for the single stage amplifier, 5T op amp, differential pair with current mirror loads.

Next is swing limits (large signal swing).




## Swing limits

Next:

* [Swing limits](Swing_analysis.md)
