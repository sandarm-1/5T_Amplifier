# Frequency response of single stage amplifier

## Frequency response

### If we neglect parasitics (just load cap) it's a single pole circuit

When we say it’s a single pole circuit, we mean this:

A simple RC circuit is a single pole circuit. Like, series RC voltage driven, or parallel RC current driven.

Quick reminder of general single-pole systems:

![image](https://user-images.githubusercontent.com/95447782/168850081-a968e040-5c52-4954-b4a8-9638e9b28cd9.png)


The TRANSCONDUCTOR is also like a current-driven parallel RC circuit, which has a V-to-I before it.

![image](https://user-images.githubusercontent.com/95447782/168850210-46e6b3ae-8e80-4f58-aa9c-4e89156e0c56.png)


If we draw the bode plot for the transconductor:

![image](https://user-images.githubusercontent.com/95447782/168850283-a98e6030-7d88-438f-b95c-53007086a089.png)


And that's the frequency response of the trasnsconductor (diff pair with current mirror load, 5T-ota).

**NOTE, THIS SO FAR IS NOT INCLUDING THE PARASITIC CAPS OF THE DEVICES.**

The next step is just do the same thing, but including PARASITIC CAPs.

### Frequency response with parasitic caps, 2-pole system

These are the parasitic caps:

![image](https://user-images.githubusercontent.com/95447782/168851573-c2bbfd28-4558-4a65-90b7-d23d45346cc6.png)


At this stage we notice, previously all the left branch current was mirrored from M3 to M4 and added to the output current, but now we have the extra cap Cd3, and that takes some current, so a bit less current is mirrored to the output. Let’s see how much.

![image](https://user-images.githubusercontent.com/95447782/168852480-06d84ad9-6f29-416e-9cea-f230a645bc0c.png)


This is called **“imperfect current mirroring at high frequencies”**. Since at high frequencies not all current is mirrored, some is “lost” into the parasitic cap Cd3.

After that we can calculate how much is the total current that goes out, frequency dependent.

![image](https://user-images.githubusercontent.com/95447782/168853377-2e2a0721-cb5b-4042-95dc-1b8ebb742ff7.png)


And we get this Y(s) which shows one Zero and a Pole, that’s for the diff pair with current mirror load, due to the parasitic caps, not considering the Load Cap yet.

Now if we drive the load cap with this, we have the full OTA circuit:

![image](https://user-images.githubusercontent.com/95447782/168854820-e56369b0-94f4-4fa4-9589-b8b218611d9c.png)


And this is the plot of that frequency response (without any feedback, i.e. open loop).

This is the 2-pole system that we mentioned, once we include not only the load cap but also the parasitic caps, we get the 2 poles.

![image](https://user-images.githubusercontent.com/95447782/168857113-2d292da7-63db-4655-a7ad-7d26ff48c10d.png)


**The dominant pole (lowest frequency) of the whole op-amp will be determined by the load cap C.** Since that’s the biggest cap, it will create the lowest frequency pole.

**And that's the frequency response of the basic Single Stage amplifier (differential pair with current mirror load, 5T op amp), including parasitics and load cap, without feedback i.e. open loop.**


## Offset

Next:

* [Offset](Offset_analysis.md)
