[# Ex No: 08 - Design and Simulation of a Booth Multiplier Using Verilog and Cadence nclaunch]

## Aim
To design and simulate a **Booth Multiplier** using **Verilog HDL** and verify its functionality in **Cadence nclaunch**.

## Tools Required
### Cadence EDA Suite
- **Cadence nclaunch** (for simulation)

### Computer System
- Minimum **4GB RAM** and a **multi-core processor**

## Theory
Booth’s multiplication algorithm is an efficient way to perform **signed integer multiplication**. It reduces the number of **add/subtract operations** and handles negative numbers efficiently.

### Booth's Algorithm Steps:
1. **Initialize** the multiplier and multiplicand.
2. **Examine the least significant bit (LSB)** and previous bit:
   - If **01**, **add** the multiplicand.
   - If **10**, **subtract** the multiplicand.
   - If **00** or **11**, do nothing.
3. **Shift the result** right after each step.
4. Repeat for **n** bits.

## Simulation Procedure
1. **Launch Cadence nclaunch** and create a new Verilog project.
2. **Write the Booth Multiplier code** and compile it.
3. **Apply test inputs** using a Verilog testbench.
4. **Run the simulation** and observe the output waveforms.
5. **Verify correctness** against expected results.

## Flow Chart

![image](https://github.com/user-attachments/assets/a34dd25e-3043-4243-81a5-567165d3f4b2)


## Verilog Code for Booth Multiplier
```verilog
module booth_multiplier (
    input signed [3:0] A, B,
    output reg signed [7:0] P
);
    reg signed [7:0] ACC;  // Accumulator
    reg signed [3:0] M;    // Multiplicand
    reg signed [4:0] Q;    // Multiplier (Extended for Booth's logic)
    reg Q_1;               // Extra bit for Booth's logic
    integer i;

    always @(*) begin
        // Initialize values
        M = A;            // Multiplicand
        Q = {B, 1'b0};    // Extend multiplier and add a zero LSB
        Q_1 = 0;
        ACC = 8'b0;       // Accumulator starts at 0

        for (i = 0; i < 4; i = i + 1) begin
            case ({Q[0], Q_1})
                2'b01: ACC = ACC + (M << i);  // Add if 01
                2'b10: ACC = ACC - (M << i);  // Subtract if 10
                default: ACC = ACC;           // Do nothing for 00 or 11
            endcase
            
            // Arithmetic right shift (preserving sign bit)
            {ACC, Q, Q_1} = {ACC[7], ACC, Q};
        end

        P = ACC;  // Store final product
    end
endmodule
```
## Truth Table for Booth Multiplier (Example)

![image](https://github.com/user-attachments/assets/742744b0-15e9-4c7c-8e0e-13a77f25673e)

## Simulation Results

![Screenshot 2025-05-21 111232](https://github.com/user-attachments/assets/c32ff88d-4bed-4fc8-9138-914de6fece47)



## Results
Successfully designed and simulated a Booth Multiplier in Verilog.
Performed signed multiplication efficiently.
Verified correctness using Cadence nclaunch.

# Ex No: 08 - Design and Simulation of a Booth Multiplier Using Verilog and Cadence nclaunch
## Ganapathy Shriram V B 
## 212223060064

## Aim
To design and simulate a **Booth Multiplier** using **Verilog HDL** and verify its functionality in **Cadence nclaunch**.

## Tools Required
### Cadence EDA Suite
- **Cadence nclaunch** (for simulation)

### Computer System
- Minimum **4GB RAM** and a **multi-core processor**

## Theory
Booth’s multiplication algorithm is an efficient way to perform **signed integer multiplication**. It reduces the number of **add/subtract operations** and handles negative numbers efficiently.

### Booth's Algorithm Steps:
1. **Initialize** the multiplier and multiplicand.
2. **Examine the least significant bit (LSB)** and previous bit:
   - If **01**, **add** the multiplicand.
   - If **10**, **subtract** the multiplicand.
   - If **00** or **11**, do nothing.
3. **Shift the result** right after each step.
4. Repeat for **n** bits.

## Simulation Procedure
1. **Launch Cadence nclaunch** and create a new Verilog project.
2. **Write the Booth Multiplier code** and compile it.
3. **Apply test inputs** using a Verilog testbench.
4. **Run the simulation** and observe the output waveforms.
5. **Verify correctness** against expected results.

## Flow Chart

![image](https://github.com/user-attachments/assets/a34dd25e-3043-4243-81a5-567165d3f4b2)


## Verilog Code for Booth Multiplier
```verilog
module booth_multiplier (
    input signed [3:0] A, B,
    output reg signed [7:0] P
);
    reg signed [7:0] ACC;  // Accumulator
    reg signed [3:0] M;    // Multiplicand
    reg signed [4:0] Q;    // Multiplier (Extended for Booth's logic)
    reg Q_1;               // Extra bit for Booth's logic
    integer i;

    always @(*) begin
        // Initialize values
        M = A;            // Multiplicand
        Q = {B, 1'b0};    // Extend multiplier and add a zero LSB
        Q_1 = 0;
        ACC = 8'b0;       // Accumulator starts at 0

        for (i = 0; i < 4; i = i + 1) begin
            case ({Q[0], Q_1})
                2'b01: ACC = ACC + (M << i);  // Add if 01
                2'b10: ACC = ACC - (M << i);  // Subtract if 10
                default: ACC = ACC;           // Do nothing for 00 or 11
            endcase
            
            // Arithmetic right shift (preserving sign bit)
            {ACC, Q, Q_1} = {ACC[7], ACC, Q};
        end

        P = ACC;  // Store final product
    end
endmodule
```
## Truth Table for Booth Multiplier (Example)

![image](https://github.com/user-attachments/assets/742744b0-15e9-4c7c-8e0e-13a77f25673e)

## Simulation Results

![Screenshot 2025-05-21 111232](https://github.com/user-attachments/assets/c32ff88d-4bed-4fc8-9138-914de6fece47)



## Results
Successfully designed and simulated a Booth Multiplier in Verilog.
Performed signed multiplication efficiently.
Verified correctness using Cadence nclaunch.

