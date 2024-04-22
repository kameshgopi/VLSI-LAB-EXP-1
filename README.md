
SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS

AIM: 
To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.2.
APPARATUS REQUIRED: 
VIVADO 2023.2
PROCEDURE: 
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

**LOGIC GATES
LOGIC DIAGRAM**
![image](https://github.com/CalebSamraj14/VLSI-LAB-EXP-1/assets/163808923/6881dbeb-686d-4a10-a17e-fe9cb11ae4d3)

**VERILOG CODE**
~~~
module logicgate(a,b,andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate);

input a,b;

output andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate;

and(andgate,a,b);

or(orgate,a,b);

nand(nandgate,a,b);

nor(norgate,a,b);

xor(xorgate,a,b);

xnor(xnorgate,a,b);

not(notgate,a);

endmodule
~~~
**OUTPUT WAVEFORM**
![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/371ee540-b0c1-45ff-aed6-980fbcd5b928)


**HALF ADDER

LOGIC DIAGRAM**



![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/e18e6265-27ba-4c9e-9d1d-ee598b26d517)


**VERILOG CODE**
~~~
module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

xor g1(sum,a,b);

and g2(carry,a,b);

endmodule 
~~~
**OUTPUT WAVEFORM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/44388b42-3264-4eb4-82cb-6da6f1d8de43)

**FULL ADDER

LOGIC DIAGRAM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/d4e97326-00e7-4579-b58d-409a07aff8d5)


**VERILOG CODE**
~~~
module fulladder(a,b,c,sum,carry);

input a,b,c;

output sum,carry;

wire w1,w2,w3;

xor(w1,a,b);

xor(sum,w1,c);

and(w2,w1,c);

and(w3,a,b);

or(carry,w2,w3);

endmodule
~~~
**OUTPUT WAVEFORM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/024f719b-17f4-44d8-a68d-88717861321f)


**HALF SUBTRACTOR

LOGIC DIAGRAM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/a319202d-a027-44dd-960d-74891ccb2821)

**VERILOG CODE**
~~~
module halfsub(a,b,diff,borrow);

input a,b;

output diff,borrow;

xor(diff,a,b);

and(borrow,~a,b);

endmodule
~~~
**OUTPUT WAVEFORM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/6e977938-e048-46fa-827d-adbd593571d2)

**FULL SUBTRACTOR
LOGIC DIAGRAM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/c4ac68b7-81d9-42e2-9412-1d4c1db19327)

**VERILOG CODE** 
~~~
module fs(a,b,bin,d,bout);

input a,b,bin;

output d,bout;

wire w1,w2,w3;

xor(w1,a,b);

xor(d,w1,bin);

and(w2,~a,b);

and(w3,~w1,bin);

or(bout,w3,w2);

endmodule
~~~
**OUTPUT WAVEFORM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/741bdfa7-f0cb-42c0-be8c-cbcdfa56a94d)


**RIPPLE CARRY ADDER
LOGIC DIAGRAM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/7415fb59-6bf5-407f-a28c-43170a8bc618)


**VERILOG CODE** 
~~~
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
~~~
**OUTPUT WAVEFORM**

![image](https://github.com/kameshgopi/VLSI-LAB-EXP-1/assets/164839944/a643846c-50d6-49d7-8db5-f41a04b9796f)


**Result**

 simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 completed successfully





