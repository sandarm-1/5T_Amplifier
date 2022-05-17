# Gain of Single Stage amplifier - 5T op amp
Analysis of the Gain of the basic Single Stage amplifier - 5T op amp.


## Differential Pair with Asymmetrical load
First of all, we analyze the Differential Pair with ASYMETRIC RESISTIVE LOAD.

![image](https://user-images.githubusercontent.com/95447782/168821330-9842893a-1b67-49c8-87fd-ee87f075f497.png)


The main point of this is: even if the load resistors R1 and R2 are DIFFERENT, the voltage on Vx node will be 0, if we neglect rds of the diff pair devices (if it was infinite). (that is small signal, with purely differential voltage excitation).

BUT if the rds of the diff pair devices is not infinite (as in reality) then IN SOME CIRCUMNSTANCES you may get Vx NOT 0. And we want to get Vx=0 just because it simplifies the analysis greatly. **If you fall in the conditions where Vx is NOT ZERO, then the analysis will not be valid and the results of your circuit will not be what you expect.**

