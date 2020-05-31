# Latches-flip-flop-Registers
VHDL coding

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/Untitled%20picture.png)

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/1Untitled%20picture.png)



| Clk |	S	| R |	Qa    |	Qb    |   
|-----|---|---|-------|-------|
| 1   |	0	| 0 |	latch |	latch | 
| 1   | 0	| 1 |	0     |	1     |
| 1	  | 1	| 0	| 1     |	0     |
| 1	  | 1	| 1 |	0	    | 0     |
| 0	  | 0	| 0	| latch |	latch |
| 0	  | 0	| 1	| latch	| latch |
| 0	  | 1 | 0	| latch	| latch |
| 0	  | 1 |	1	| latch	| latch |


![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/2Untitled%20picture.png)


The Q and not-Q outputs are supposed to be in opposite states. I say “supposed to” because making both the S and R inputs equal to 1 results in both Q and not-Q being 0. For this reason, having both S and R equal to 1 is called an invalid or illegal state for the S-R latch. Otherwise, making S=1 and R=0 “sets” the latch so that Q=1 and not-Q=0. Conversely, making R=1 and S=0 “resets” the latch in the opposite state. When 'S' and 'R' are both equal to 0, the latch's outputs “latch” in their prior states. By definition, a condition of Q=1 and not-Q=0 is set. A condition of Q=0 and not-Q=1 is reset.

When the Clk=0, the outputs of the two AND gates are forced to 0, regardless of the states of either S or R. Consequently, the circuit behaves as though S and R were both 0, latching the Q and not-Q outputs in their last states. Only when the enable input is activated (1) will the latch respond to the S and R inputs.

From <https://www.allaboutcircuits.com/textbook/digital/chpt-10/the-gated-s-r-latch/> 

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/3Untitled%20picture.png)

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/4Untitled%20picture.png)

|Clk|	D	|Q	|Qz|
|---|---|---|--|
|0	|0	|Previous state	|Previous state|
|0	|1	|Previous state	|Previous state|
|1	|0	|0 |	1|
|1	|1	|1 |	0|

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/5Untitled%20picture.png)

Since the enable input on a gated S-R latch provides a way to latch the Q and not-Q outputs without regard to the status of S or R, we can eliminate one of those inputs to create a latch circuit with no “illegal” input states. Such a circuit is called a D latch, and its internal logic looks like in the above table.

The R input has been replaced with the complement (inversion) of the old S input, and the S input has been renamed to D. As with the gated S-R latch, the D latch will not respond to a signal input if the enable input is 0 — it simply stays latched in its last state. When the enable input is 1, however, the Q output follows the D input.
Since the R input of the S-R circuitry has been done away with, this latch has no “invalid” or “illegal” state. Q and not-Q are always opposite of one another. If the above diagram is confusing at all, the next diagram should make the concept simpler:

From <https://www.allaboutcircuits.com/textbook/digital/chpt-10/d-latch/> 

# Part II

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/6Untitled%20picture.png)

Remember to replace E with Clk

A D latch is like an S-R latch with only one input: the “D” input. Activating the D input sets the circuit, and de-activating the D input resets the circuit. Of course, this is only if the clock input (Clk) is activated as well. Otherwise, the output(s) will be latched, unresponsive to the state of the D input.

D latches can be used as 1-bit memory circuits, storing either a “high” or a “low” state when disabled, and “reading” new data from the D input when enabled.

From <https://www.allaboutcircuits.com/textbook/digital/chpt-10/d-latch/> 

# Part III

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/7Untitled%20picture.png)

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/8Untitled%20picture.png)

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/9Untitled%20picture.png)

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/10Untitled%20picture.png)

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/11Untitled%20picture.png)


This above represents it's now independent from the input 'D'. And when the clock gets high it get the state of Q_out (the output state of master D latch). This can be considered as a rising edge D latch. The final output starts at the rising edge of the clock.  

The wire connections between the two latches can see in the above figure.
In part 3 there are D latches connected series. This type of can be used in 2 ways.
		1. Save 2 bits
		2. Set and reset 

Most important one is to set this as a set and reset. If using a push button it's easier to use this type to set a bit (0 or 1). Here in master latch the clock is not set (0) and giving a value to D, it can be set or reset. And the output will be effect to the slave latch. To initialize the slave latch the clock must be high (1) then the output of the latch will work as the previously fixed latch (master latch) state. Using this, assign a bit and use it whenever it needed. 

# Part IV

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/12Untitled%20picture.png)

Qc - falling edge D latch
Qb - rising edge D latch
Qa - D latch

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/13Untitled%20picture.png)


This figure presents how the output will be when the input and the clock differs. 

Qa - the output will be the input (D) when the clock is high. Otherwise the output will be the previous state.
Qb - the output will be the input (D) when the state of the rising edge of the clock , otherwise the output will be the previous state.
Qc - the output will be the input (D) when the state of the falling edge of the clock, otherwise the output will be the previous state.

# Part V

![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/14Untitled%20picture.png)
![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/15Untitled%20picture.png)
![figure 1](https://github.com/hasithz/Latches-flip-flop-Registers/blob/master/iamges/16Untitled%20picture.png)


In here to display 4 HEXA decimal values using 16 switches and use the same switches to show another 4 HEXA decimals values. Feeding a single input to a D latch and connect 4 swathes with 4 latches can be able to create to display 0 to F HEXA values in a seven segment display. The above diagram will show how the pins are connected to each other. 


