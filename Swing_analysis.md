# Swing limits of single stage amplifier

## Swing limits of the 5T op amp

First we look at the output swing limits.

![image](https://user-images.githubusercontent.com/95447782/169099622-d09c090e-3daf-4312-bce0-e21a88ce69b0.png)

Then the input swing limits.

![image](https://user-images.githubusercontent.com/95447782/169099652-725f421f-a7fc-429e-b6bd-fa607216149c.png)


Overall, these are the swing limits:

![image](https://user-images.githubusercontent.com/95447782/169099674-9c4601eb-b671-4bb2-808d-cf0f47a83c8f.png)


Observations about swing:
* **Output range, on the upper side is quite good**, it can go quite close to VDD (just one VDSat below it).
* **Output range, on the lower side is not so good,** it can’t go too low, it’s actually limited by Vbias (the input common mode level also limits the lowest output you can achieve).

* **Input range, on the upper side is also good,** again it can go quite close to VDD (just one VDSat below it, assuming the two VTs cancel out roughly).
* **Input range, on the lower side is not so good either,** the lowest it can go is Ground PLUS one VT and 2 VDSATs, so that’s around 1.1V above ground.

**This is for NMOS input pair, if you use PMOS input pair the ranges are reversed.** You can go close to ground, but not so close to supply.


A depiction of these swing ranges:

![image](https://user-images.githubusercontent.com/95447782/169099792-d8213fe0-0f5f-4af6-a439-4840303bc797.png)


Now even if we know that’s the possible range, how do we choose the Vbias level?

This will depend on the circuit that we use this opamp inside of. For example, whether we wrap it in unity feedback, or in a non-inverting amplifier configuration.



By the way this amplifier (and any other) can be used with single supply or dual supplies. The dual supplies case is just the same case where we shift all voltages by a certain amount, so that the node that we were previously using as Ground reference becomes a negative voltage and another voltage becomes the Ground reference.

Example of this:

![image](https://user-images.githubusercontent.com/95447782/169099816-1406e127-e468-4e96-be38-9cc06c43f96c.png)


![image](https://user-images.githubusercontent.com/95447782/169099823-178eaf9d-a4cf-4fd7-903e-fc3279dd5068.png)


That example is with a resistive load. Usually we wouldn’t use this single stage amplifier to drive a resistive load, since the gain depends so much on the overall Rout, so putting a load at the output would reduce overall Rout a lot and hence DC gain would drop a lot and the circuit would be useless as an op amp in that case. So that’s why we would only use this circuit to drive into a Capacitor, like an integrator.

Example, using this single stage amplifier in unity feedback configuration to form a voltage follower:

![image](https://user-images.githubusercontent.com/95447782/169099850-ce0196f9-6b4b-436d-b61c-c213e3f4ce41.png)

In particular, for this voltage follower with this single stage amplifier, the swing limits would look like this, this would be the Vbias selection that we would choose in order to maximize the output swing.

![image](https://user-images.githubusercontent.com/95447782/169099871-cd4015f5-e555-4219-a297-656c64e9bd30.png)


Next is Slew Rate.


## Slew Rate

Next:

* [Slew Rate](/Slew_Rate_analysis.md)


