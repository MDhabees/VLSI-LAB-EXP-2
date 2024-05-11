SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Vivado 2023.2.

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
PROCEDURE:
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
VERILOG CODE

ENCODER:
~~~
module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
~~~

OUTPUT :
 ![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/e5f0d321-36d4-4aa0-a30a-0a5291ca9944)
![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/eda78136-88f2-48dd-bda9-214a27128142)

DECODER:
~~~
module decoder_3to8(
    input [2:0] a,
    output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule
~~~
OUTPUT:



MULTIPLEXER:
~~~
module mux_8to1(in,sel,out);
  input[7:0]in;
  output reg out;
  always @(*)
    begin
      case(sel)
        3'b000: out = in[0];
        3'b001: out = in[1];
        3'b010: out = in[2];
        3'b011: out = in[3];
        3'b100: out = in[4];
        3'b101: out = in[5];
        3'b110: out = in[6];
        3'b111: out = in[7];
        default: out = 1'bx;
      endcase
    end
endmodule
~~~
OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/3d047610-7418-4019-9c8b-417bd006b0b4)
![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/cd106a6f-d463-4d0d-aca8-a0cdf502bfec)


DEMULTIPLEXER:
~~~
module demux_1_8(y,s,a);
output reg [7:0]y;
input [2:0]s;
input a;

always @(*)
begin 
y=0;
case(s)
3'd0: y[0]=a;
3'd1: y[1]=a;
3'd2: y[2]=a;
3'd3: y[3]=a;
3'd4: y[4]=a;
3'd5: y[5]=a;
3'd6: y[6]=a;
3'd7: y[7]=a;
endcase
end
endmodule
~~~
OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/1fc71a63-9e42-419d-af95-270a345ba4ff)
![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/2c55e09a-5110-4468-8651-95b03e456601)

MAGNITUDE COMPARATOR:
~~~
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
~~~
OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-2/assets/165646570/8625193e-a157-403b-9627-92930d10bdd2)
![Uploading image.png…]()

RESULT


