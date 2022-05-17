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

So we need to keep rds of diff pair RELATIVELY LARGE, or don’t go crazy making R1 and R2 excessively large.

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

