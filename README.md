# Seven-Segment Display Driver using Verilog HDL

## Aim  
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

## Apparatus Required  
- **Vivado 2023.1**  

## Procedure  

### 1. Launch Vivado 2023.1  
- Open Vivado and create a new project.  

### 2. Design the Verilog Code  
- Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.  

### 3. Create the Testbench  
- Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.  

### 4. Create the Verilog Files  
- Create both the design module and the testbench in the Vivado project.  

### 5. Run Simulation  
- Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs **0000 to 1001** (decimal **0 to 9**).  

### 6. Observe the Waveforms  
- Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.  

### 7. Save and Document Results  
- Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.  

---
## Logic Diagram

![image](https://github.com/user-attachments/assets/e561cdb5-b1b0-42d0-94f5-e1efaec9704c)

![image](https://github.com/user-attachments/assets/dc32254e-f88d-471a-a2ba-e4ec5eb3fc11)

![image](https://github.com/user-attachments/assets/a8a8921e-0a37-4697-86d8-0c43cd8aef5a)

## Verilog Code for Seven-Segment Display  

```
`timescale 1ns / 1ps
module bcd_to_7seg(bcd, seg);
input [3:0] bcd;
output reg [6:0] seg;
always @(bcd)
case (bcd)
0: seg = 6'b0000001;
1: seg = 6'b1001111;
2: seg = 6'b0010010;
3: seg = 6'b0000110;
4: seg = 6'b1001100;
5: seg = 6'b0100100;
6: seg = 6'b0100000;
7: seg = 6'b0001111;
8: seg = 6'b0000000;
9: seg = 6'b0000100;
default : seg = 6'b1111111;
endcase
endmodule

```
## Testbench for Seven-Segment Display
```
module bcd_to_7seg_tb;

reg [3:0] bcd;
wire [6:0] seg;


bcd_to_7seg uut (
    .bcd(bcd),
    .seg(seg)
);


initial begin
    
    bcd = 4'b0100;

    #10 bcd = 4'd0;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd1;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd2;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd3;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd4;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd5;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd6;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd7;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd8;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);
    #10 bcd = 4'd9;
    $display("Time: %0t, BCD: %b, 7-seg: %b", $time, bcd, seg);

   
    #10 $finish;
end

endmodule
```
## Simulated Output

<img width="1920" height="1080" alt="Screenshot 2025-08-29 151127" src="https://github.com/user-attachments/assets/aadfb461-176a-4cbc-b2af-11cf297d88e9" />

---

## Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs.

This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
