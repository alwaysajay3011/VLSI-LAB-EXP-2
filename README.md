AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7 Spartan6 FPGA

PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

Logic Diagram:
![301405876-ee17970c-3ac9-4603-881b-88e2825f41a4](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/415cd142-3ac0-4391-b485-4b499df52c0e)



Logic Gates:
verilod code:
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
out put:
![324748953-591199a0-016e-40c2-8eff-374918e0c097](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/4bb71c63-e8c7-4757-9320-98aa756c33f3)


logic daigram:
![324749090-6564a8a4-8ccf-4af3-a1e6-becd6e3359f6](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/e0cc1406-47c5-40f8-bb9a-1e06b1ab457e)

Half Adder:
verilog code:
module half_adder(Sum,carry,a,b);
input a,b;
output Sum,carry;
assign Sum = a ^ b;
assign carry = a & b;
endmodule
out put:
![324749159-9c0dafdb-d179-4f52-b0f9-04c668ad427a](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/b821070d-53fa-4339-a3ba-2c6f1ae4406e)


logic daigram:
![324749235-52c8feb1-fecd-4ec4-b200-7ca2b5030e3c](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/42016968-94da-499a-822f-09b17daacbf8)


Full adder:
verilog code:
module fulladder(sum,cout,a,b,c);
input a,b,c;
output sum,cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and a1(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,c1,c2);
or o2(cout,w5,c3);
endmodule
out put :
![324749296-a0ab6127-fd6f-4d2a-b84a-44fe31bb122e](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/46ea3f72-6483-463f-93f1-8365c8f0dac7)


logic daigram:
![324749329-6b49afba-c40c-4c53-9811-a82b5c1a5fd1](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/5df89b55-5b34-46ed-a0e2-f93f02f36ad6)


Half Subtractor:
verilog code:
module half_sub(Diff,Borrow,a,b);
input a,b;
output Diff,Borrow;
wire w1;
not(w1,a);
xor(Diff,a,b);
and(Borrow,b,w1);
endmodule
out put:
![324749374-54a47f64-fa15-4cd5-9205-0a9f1147a83e](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/6edd044c-c264-4aeb-b1d5-7fab4b84609d)


logic daigrm:
![324749398-dbbfe3ee-cf23-452c-ba83-6d2e51917e6f](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/ff5d6146-37ac-4b05-92a1-9dbdb5a773b9)


Full Subtractor:
verilog code:

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

out put:
![324749487-e471cbc7-5212-45db-a861-552639ce4a43](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/bda6daf1-5da7-4b3a-9323-887d3a932d10)



logic daigram :
![301406117-7385a408-40a5-4203-8050-b72818622d79](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/6910f3a5-cbb1-4e0b-b6ff-183f7501ce69)

8 Bit Ripple Carry Adder:
verilog code:

module rippe_adder(S, Cout, X, Y,Cin);
input [7:0] X, Y;// Two 4-bit inputs
input Cin;
output [7:0] S;
output Cout;
wire w1, w2, w3, w4, w5, w6, w7;
 // instantiating 8 1-bit full adders in Verilog
fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], w4,X[3], Y[3], w3);
fulladder u5(S[4], w5,X[4], Y[4], w4);
fulladder u6(S[5], w6,X[5], Y[5], w5);
fulladder u7(S[6], w7,X[6], Y[6], w6);
fulladder u8(S[7], Cout,X[7], Y[7], w7);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
  //Structural code for one bit full adder
xor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
out put:
![324749539-b39f3593-9b6c-4fa6-b03f-23f2aed569cc](https://github.com/alwaysajay3011/VLSI-LAB-EXP-2/assets/161150132/f4addbb0-cb8d-4be8-95e7-97a1493c1747)


RESULT:
THUS THE LOGIC GATES,ADDERS,SUBTRACTORS VERILOG CODE IS SIMULATED USING VIVADO 2023.1 AND OUTPUT VERIFIED SUCCESSFULLY
