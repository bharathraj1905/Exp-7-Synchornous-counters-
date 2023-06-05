# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
1.Create a new project in QuartusII software.

2.Name the project as uc for upcounter and dc for down counter.

3.Create a new verilog hdl file in the project file.

4.Name the module as dc and uc for down counter and up counter.

5.Within the module declare input and output variables.

6.Create a loop using if-else with condition parameter as reset value.

7.End the loop.

8.End the module.

### PROGRAM 
Program for flipflops  and verify its truth table in quartus using Verilog programming.
```
Developed by: Barathraj B
RegisterNumber: 212222230019 
```
### UP COUNTER :
```
module sync(clk,t);
input clk;
output reg [0:2]t;
always@ (posedge clk)
begin
t[2]=((t[1]&t[0])^t[2]);
t[1]=t[0]^t[1];
t[0]=1^t[0];
end
endmodule
```
### DOWN COUNTER :
```
module sync(clk,t);
input clk;
output reg [0:2]t;
wire bar2,bar1,bar0;
not(bar2,t[2]);
not(bar1,t[1]);
not(bar0,t[0]);
always@ (posedge clk)
begin
t[2]=((bar1&bar0)^t[2]);
t[1]=bar0^t[1];
t[0]=1^t[0];
end
endmodule
```
### RTL LOGIC UP COUNTER AND DOWN COUNTER  

### UP COUNTER :
![upcounter](https://github.com/bharathraj1905/Exp-7-Synchornous-counters-/assets/121490575/c4d5a8c5-b3b4-4b86-b845-398d278fc1f5)

### DOWN COUNTER :
![down counter](https://github.com/bharathraj1905/Exp-7-Synchornous-counters-/assets/121490575/55b92a96-cef0-40a6-8a47-0c8f9b5b0306)


### TIMING DIGRAMS FOR COUNTER  

### UP COUNTER :
![upcounter timing diagram](https://github.com/bharathraj1905/Exp-7-Synchornous-counters-/assets/121490575/f6162413-2593-466c-b1e3-041dd0f8da84)

### DOWN COUNTER :
![down counter timing diagram](https://github.com/bharathraj1905/Exp-7-Synchornous-counters-/assets/121490575/12c5f1f3-5a82-4ef8-9aa6-6d3d3a57007f)



### TRUTH TABLE 

### UP COUNTER :
![upcounter truthtable](https://github.com/bharathraj1905/Exp-7-Synchornous-counters-/assets/121490575/3d5e2939-e33b-419d-907b-ff91ac45881f)

### DOWN COUNTER :
![down counter truth table](https://github.com/bharathraj1905/Exp-7-Synchornous-counters-/assets/121490575/d27340e7-299d-47db-b524-321c7f4a99c6)


### RESULTS 
Thus, 4 bit up and down counters are implemented and its functionality is validated successfully.
