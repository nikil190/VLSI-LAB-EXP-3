# SIMULATION AND IMPLEMENTATION OF MULTIPLIER
# AIM:
To simulate and synthesis multiplier using vivado.

# APPARATUS REQUIRED:
vivado 2023.2

# PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# Logic Diagram
# 2 bit Multiplier
![image](https://github.com/nikil190/VLSI-LAB-EXP-3/assets/161817112/b9606355-c8a8-42be-8878-5d84f2d31937)


# 4 Bit Multiplier
![image](https://github.com/nikil190/VLSI-LAB-EXP-3/assets/161817112/7f661fca-7651-4727-8240-bc2f6a8ecac3)


# Verilog code
# 2 bit multiplier:
module ha(a,b,sum,c);

input a,b;

output sum,c;

xor g1(sum,a,b);

and g2(c,a,b);

endmodule

module bitmultiplier(a,b,c);

input [1:0]a,b;

output[3:0]c;

wire w1;

and g1(c[0],b[0],a[0]);

ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);

ha ha2(a[1] &b[1],w1,c[2],c[3]);

endmodule

# 4 bit multipler:
module ha(a,b,c,s);

input a,b;

output s,c;

xor g1(s,a,b);

and g2(c,a,b);

endmodule

module fa(a,b,c,s,carry);

input a,b,c;

output s,carry;

wire w1,w2,w3;

xor g1(w1,a,b);

and g2(w2,a,b);

xor g3(s,w1,c);

and g4(w3,w1,c);

or g5(carry,w3,w2);

endmodule

module bitmultiplier(x,y,z);

input[3:0]x,y;

output[7:0]z;

wire [17:1]w;

and g1(z[0],x[0],y[0]);

ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);

fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);

fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);

ha ha2(x[3]&y[1],w[3],w[7],w[4]);

ha ha3(w[5],x[0]&y[2],z[2],w[8]);

fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);

fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);

fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);

ha ha4(w[12],x[0]&y[3],z[3],w[15]);

fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);

fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);

fa fa8(w[11],x[3]&y[3],w[17],z[6],z[7]);

endmodule

# Output Waveform
# 2 bit multiplier:


![image](https://github.com/nikil190/VLSI-LAB-EXP-3/assets/161817112/1a80edf5-6d8e-410e-bcac-83d6fb7ba9ec)


# 4 bit multiplier:

![image](https://github.com/nikil190/VLSI-LAB-EXP-3/assets/161817112/76c2093e-6cc1-438e-855f-14a9fd36eeb5)


# Result
Thus,the simulation and synthesis of multipliers by using vivado has been successfully excecuted and verified.
