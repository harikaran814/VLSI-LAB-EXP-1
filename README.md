# SIMULATION OF LOGIC GATES, ADDERS AND SUBRACTORS USING VIVADO
AIM: 

To simulate and synthesis Logic Gates,Adders and Subtractor using vivado.

APPARATUS REQUIRED: 

Vivado 2023.1

PROCEDURE:

STEP:1 Start the Xilinx navigator, Select and Name the New project. 
STEP:2 Select the device family, device, package and speed. 
STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 
STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. 
STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. 
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. 
STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. 
STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into 
.bit file here. 
STEP:11 Load the Bit file into the SPARTAN 6 FPGA 
STEP:12 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)


Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)


8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)


# LOGIC GATES

VERILOG CODE :
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```

OUTPUT:

![WhatsApp Image 2024-04-01 at 14 19 50](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/d761016b-56d4-47ec-9d75-5af644c626a3)

![WhatsApp Image 2024-04-01 at 14 19 40](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/8b277866-b2b8-4da3-89d0-954b778a908a)


# HALF ADDER
VERILOG CODE :
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry; 
or(sum,a,b);
and(carry,a,b);
endmodule
```

OUTPUT:

![WhatsApp Image 2024-04-01 at 14 19 37](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/116d70f4-b698-4d9a-aa13-9c1988b417fe)

![WhatsApp Image 2024-04-01 at 14 19 36 (1)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/6642c69c-a68d-42fb-98ee-e2ea36025630)


# FULL ADDER

VERILOG CODE :
```
module fa_ha(a,b,c,sum,cout);
input a,b,c;
output sum,cout;
wire wl, w2, w3, w4, w5;
xor x1(w1,a,b);
xor x2 (sum,w1,c) ;
and al(w2,a,b) ;
and a2(w3,b,c);
and a3(w4,a,c) ;
or o1(w5,w2,w3) ;
or o2(cout,w5,w4) ;
endmodule
```

OUTPUT :
![WhatsApp Image 2024-04-01 at 14 19 36](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/a7106ba1-5c5f-4c4d-9d31-66dbad63ce53)

![WhatsApp Image 2024-04-01 at 14 19 39](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/9b5a3e2f-13fc-4a0d-9413-061eeaf3bbef)


# HALF SUBRACTOR

VERILOG CODE :
```
module halfsubtractor( D,Bo,A,B);
input A,B;
output D,Bo;
wire w1;
xor (D,A,B);
not (w1,B);
and (Bo,B,w1);
endmodule
```

OUTPUT:

![WhatsApp Image 2024-04-01 at 14 19 35](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/c2a77dc5-d2be-4a6d-8746-d587cd33f165)

![WhatsApp Image 2024-04-01 at 14 19 46](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/f05b66ef-4a79-4520-9751-51004d87db10)


# FULL SUBRACTOR

VERILOG CODE :
```
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule
```

OUTPUT :

![WhatsApp Image 2024-04-01 at 14 19 50 (2)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/0943900d-f719-4d70-8365-347baf71d8a8)

![WhatsApp Image 2024-04-01 at 14 19 46 (1)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/72507552-3a34-4f9b-9e30-5bdf9b0c92ca)


# RIPPLECARRYADDER 4_Bit

VERILOG CODE :
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```

OUTPUT :

![WhatsApp Image 2024-04-01 at 14 19 50 (3)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/17dbf7a9-a78c-4fc7-89c3-fe940920a391)

![WhatsApp Image 2024-04-01 at 14 19 39 (1)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/a404cdfd-d668-4454-96c0-362af02cd11a)


# RIPPLECARRYADDER 8_Bit

VERILOG CODE :
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```

OUTPUT :

![WhatsApp Image 2024-04-01 at 14 19 37 (1)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/40d226f6-3670-4f58-9a4d-6ecafbe1f280)

![WhatsApp Image 2024-04-01 at 14 19 37 (2)](https://github.com/harikaran814/VLSI-LAB-EXP-1/assets/164861651/19f56c9b-3449-40f9-b5a6-22678a165522)


RESULT:
Thus the simulation of Logic Gates, Adders and Subtractor is completed using Vivado.
