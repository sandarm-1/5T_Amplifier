# Gain of Single Stage amplifier - 5T op amp
Analysis of the Gain of the basic Single Stage amplifier - 5T op amp.


## Differential Pair with Asymmetrical load
First of all, we analyze the Differential Pair with ASYMETRIC RESISTIVE LOAD.

![image](https://user-images.githubusercontent.com/95447782/168821330-9842893a-1b67-49c8-87fd-ee87f075f497.png)


The main point of this is: even if the load resistors R1 and R2 are DIFFERENT, the voltage on Vx node will be 0, if we neglect rds of the diff pair devices (if it was infinite). (that is small signal, with purely differential voltage excitation).

BUT if the rds of the diff pair devices is not infinite (as in reality) then IN SOME CIRCUMNSTANCES you may get Vx NOT 0. And we want to get Vx=0 just because it simplifies the analysis greatly. **If you fall in the conditions where Vx is NOT ZERO, then the analysis will not be valid and the results of your circuit will not be what you expect.**

![image](https://user-images.githubusercontent.com/95447782/168823161-06705aea-61b4-4203-b4fa-5932820b76a3.png)

Overall, Vx will be ZERO if:

    • If R1=R2 (symmetrical loads), Vx=0
    
    • If R1 different than R2 BUT gds1=0 (infinite rds of diff pair devices), Vx=0 also
    
    • If rds1 MUCH LARGER than R1 and R2, Vx=0 also.

    • BUT the problem comes if rds of diff pair becomes TOO SMALL or of R1 & R2 become TOO BIG. If R1 & R2 are COMPARABLE to rds of diff pair, then Vx is NOT 0 (and the analysis becomes invalid and further results down the line will not be what you expect).

So we need to keep rds of diff pair RELATIVELY LARGE, or don’t make R1 and R2 excessively large, don´t allow them to be COMPARABLE to diff pair rds's.

## Differential Pair with Current Mirror load
Now the Diff Pair with a CURRENT MIRROR LOAD.

First of all, we notice that the loads are ASYMMETRICAL.

Because one is the diode connected device M3 and the other one is non diode connected. 

For the diode connected device the Rout seen is around 1/gm. For the non-diode it’s around 1/gds.

So they are quite different indeed. Since a gm is roughly 10x the gds for a transistor.


![image](https://user-images.githubusercontent.com/95447782/168823997-e577521a-28dc-4ca5-b02b-be139fbadf5f.png)


Now, are they both much smaller than rds1 and rds2 of the diff pair? (just to see if we can say we have Vx=0).
Well for M1 vs M3, 1/gm3 is SMALLER than 1/gds1, since a gm is about 10x larger than a gds.
But for M2 vs M4, it is NOT smaller, since 1/gds3 is COMPARABLE to 1/gds2.
**So in this particular circuit (DIFF PAIR WITH CURRENT MIRROR LOAD) we are in the case where we cannot (WE CAN’T) say that Vx=0.**
And therefore We note that if we can’t assume Vx=0 it’s pointless to plug in our circuit equations (for like the differential half-circuit etc) because the reality will just not be like whichever result we get from that.

BUT we apply a TRICK. (This may seem COUNTER INTUITIVE at first.)

We note the TRICK is to put a “TERMINATION voltage” on the output, because when doing that the output resistance seen from vout upwards will be the parallel combination of the Rout of M4 (1/gds3) and that of the voltage source, and that of the voltage source is ZERO, so the parallel combination is also ZERO, and now “MAGIC!” we now have VERY SMALL Routs both on the left side (M3) and the right side (M4) because now the right side has ZERO Rout. And thus NOW we have both load resistances SMALLER than rds of the diff pair and hence we are in the case where we can say that Vx=0. And hence we are happy in our magic ideal world!

![image](https://user-images.githubusercontent.com/95447782/168827229-0ad39f35-224a-4234-bedb-515887ca673e.png)

## Gain

### Transconductance Gm
Summary from this: if we put a VOLTAGE SOURCE on the output of this circuit, then EVEN THOUGH THE CIRCUIT IS ASSYMMETRICAL, now the 2 load resistances are SO SMALL that we can SAFELY ASSUME that the TAIL NODE voltage Vx=0.

And that makes the analysis MUCH EASIER.

![image](https://user-images.githubusercontent.com/95447782/168828099-0820a728-27d3-470c-9d4b-a21bbcde5b0f.png)


Here we have proved that **the DIFF PAIR WITH CURRENT MIRROR LOAD (5T-OTA) IS A TRANSCONDUCTOR.** In particular, it’s a transconductor with overall transconductance Gm=gm1 where gm1 is the gm of any of the diff pair devices.

We could say one transistor is a SINGLE ENDED transconductor and the 5T-OTA is a DIFFERENTIAL INPUT, SINGLE ENDED OUTPUT transconductor.

The next step is to calculate the overall output resistance of the diff pair with current mirror load.

### Rout
Now that we know the Gm of the transconductor, we need to calculate the Rout of it so that we can get its DC gain as Av=Gm·Rout.

Quite an important quantity because it determines the steady state error.

This is the Rout calculated by me, using an “approximation”. It happens to give the correct result for Rout, but to be “accurate” you should know that the “correct” analysis is more complicated than this (what we do is a bit more complicated than just replacing M3 by 1/gm3 and M4 by 1/gds3).


![image](https://user-images.githubusercontent.com/95447782/168830283-688d3238-1c43-42ae-82ff-630a04844c77.png)


Actually you know what… Let’s to do the “correct / complete” analysis.
First thing is we look at M1 and M3 and we note that, if the gate of M1 is at fixed Vbias, looking from the bottom up, this is a common gate amp (M1) loaded by a diode connected M3 which looks like a 1/gm3.

So M1 and M3 in combination, looking upwards from Vx up, we see an Rin of around 1/gm1.

We do this, so that we can use this as the load for M2.


![image](https://user-images.githubusercontent.com/95447782/168844642-894a980e-b6ff-46d7-a46f-ce3c5dc18db2.png)


With that, we can calculate the current “i_n” flowing into M2. And we get this:

![image](https://user-images.githubusercontent.com/95447782/168845448-559c014c-3aef-4b72-9e32-e5613a15ab79.png)


Now do the same for “i_p” flowing upwards into M4. But here it’s not just the “vtest/itest” that flows into M4, but also the “i_n” that goes down through M2 comes back up into M3 and gets mirrored into M4, so that also contributes to “i_p”.

![image](https://user-images.githubusercontent.com/95447782/168846900-0820d511-843d-4a20-8129-ac8bcb005793.png)


Overall, “i_n” plus “i_p” is the total of itest, so we can now do vtest/itest for the whole circuit Rout.

![image](https://user-images.githubusercontent.com/95447782/168846680-a674b786-788f-4ebb-b514-6d3a4247c951.png)


Overall **we get the same Rout result as before (with the “not so thorough” approach) but this time it’s with a thorough analysis.**

### Gain = Gm·Rout

With this we have the overall Gm and overall Rout of the transconductor.

So now we can calculate the overall Gain Ao=Gm·Rout. This is the overall opamp that we can make with this circuit.


![image](https://user-images.githubusercontent.com/95447782/168847704-933a5462-92eb-46e6-9042-269df413213a.png)


And that's the GAIN of the single stage amplifier.

**This is the 5T-OTA or DIFF PAIR WITH CURRENT MIRROR LOAD, or BASIC SINGLE STAGE AMPLIFIER.**
    
* It’s the most basic of amplifiers

* It has many shortcomings

* But it’s the starting point for all other amplifiers (telescopic, folded cascode…)

* It’s a single pole circuit.

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


And this is the plot of that frequency response (without any feedback):

![image](https://user-images.githubusercontent.com/95447782/168857113-2d292da7-63db-4655-a7ad-7d26ff48c10d.png)


**The dominant pole (lowest frequency) of the whole op-amp will be determined by the load cap C.** Since that’s the biggest cap, it will create the lowest frequency pole.

**And that's the frequency response of the basic Single Stage amplifier (differential pair with current mirror load, 5T op amp), including parasitics and load cap.**


## Offset

Next:
* [Offset](/Offset_analysis.md)





