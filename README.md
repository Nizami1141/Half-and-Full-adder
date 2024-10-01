# Lab 1 - Half Adder and Full Adder in Verilog

### Date: 18.09.2024

## Objective
The goal of this lab was to work with Verilog code in RTL design using Intel Quartus Prime and Vivado applications. The primary focus was implementing Half Adder and Full Adder designs using Verilog and verifying their functionality through RTL design and simulation.

## Background
A **Half Adder** and **Full Adder** are foundational components in digital circuits for performing binary addition. The Half Adder adds two single-bit inputs and produces a sum and a carry. The Full Adder adds two single-bit inputs along with an additional carry input.

### Half Adder
- **Inputs**: A, B
- **Outputs**: Sum, Carry
- The Half Adder is implemented using XOR and AND gates.
  
**Truth Table:**
| A   | B   | Sum | Carry |
|-----|-----|-----|-------|
| 0   | 0   | 0   | 0     |
| 0   | 1   | 1   | 0     |
| 1   | 0   | 1   | 0     |
| 1   | 1   | 0   | 1     |

- **Boolean Algebra**:
  - Sum = A'B + AB'
  - Carry = A.B

### Full Adder
- **Inputs**: A, B, Cin (Carry In)
- **Outputs**: Sum, Carry
- The Full Adder can be implemented using two Half Adders.
  
**Truth Table:**
| A   | B   | Cin | Sum | Cout |
|-----|-----|-----|-----|------|
| 0   | 0   | 0   | 0   | 0    |
| 0   | 0   | 1   | 1   | 0    |
| 0   | 1   | 0   | 1   | 0    |
| 0   | 1   | 1   | 0   | 1    |
| 1   | 0   | 0   | 1   | 0    |
| 1   | 0   | 1   | 0   | 1    |
| 1   | 1   | 0   | 0   | 1    |
| 1   | 1   | 1   | 1   | 1    |

- **Boolean Algebra**:
  - Sum = A ⊕ B ⊕ Cin
  - Carry = AB + (A ⊕ B)Cin

## Results

### Half Adder Verilog Code:
```verilog
module halfadder(
    input a,        // First input
    input b,        // Second input
    output s,       // Sum output
    output c        // Carry output
);
    xor gate_xor(s, a, b);  
    and gate_and(c, a, b);
endmodule
````


### Full Adder Verilog Code:
```verilog
module fulladder(
    input a,        // First input
    input b,        // Second input
    input cin,      // Carry input
    output sum,     // Sum output
    output carry    // Carry output
);
    wire c, c1, s;
    halfadder ha0(a, b, s, c);
    halfadder ha1(cin, s, sum, c1);
    assign carry = c | c1;
endmodule
```
###Analysis
In this lab, we implemented and tested the Half Adder and Full Adder using Verilog. Both adders were simulated and synthesized to ensure they functioned correctly, performing binary addition based on the truth tables provided. The design flow through RTL verification demonstrated the correct working of these digital components.

###Conclusion
By successfully synthesizing and simulating the Verilog code for Half Adder and Full Adder, we confirmed that both circuits perform binary addition accurately. The RTL designs and truth tables were verified, ensuring the correctness of the logic implementation.

###Tools Used
Vivado: Used to synthesize and implement the Verilog code.
Logisim: Used to simulate the logic design of the adders before coding in Verilog.
References
Lecture notes on combinational logic circuits.
Documentation from Intel Quartus and Vivado for RTL synthesis and simulation.

