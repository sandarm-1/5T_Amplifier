# Slew Rate of single stage amplifier

## Slew Rate

Slew rate is **the maximum rate of change that you can get on the output**.

If you apply **a large enough voltage STEP at the input, large enough that it saturates the diff pair, i.e. all the current goes to one branch while the other is dry**, then the current Io will flow to the output, charging the output cap C up at a constant current of Io, so **the voltage will rise with a slope of Io/C**.

That´s the Slew Rate.

![image](https://user-images.githubusercontent.com/95447782/169100413-5fae1615-8d80-4da9-b3af-79665117f75d.png)


For this op amp, both the rising and falling Slew Rates are the same and equal to Io/C.

An extra note on Slew Rate:

![image](https://user-images.githubusercontent.com/95447782/173550213-e67fa593-6931-4db6-bf5d-5d0c131f021c.png)



Next, design trade-offs and limitations of this topology.


## Design trade-offs and limitations

Next:

* [Design trade-offs and limitations of this topology](Trade-offs_and_limitations.md)
