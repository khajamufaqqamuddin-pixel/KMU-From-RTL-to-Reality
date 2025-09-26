---
   #                       SKY130RTL Verilog Constructs Reference
   #               Target: RISC-V SoC design using SKY130 process
---


---

# SKY130RTL Constructs 
|Topics: |
|----------------------|
| 1. IF-CASE Constructs|
| 2. Incomplete IF Statements|
| 3. Incomplete - Overlapping CASE Statements| 
| 4. FOR Loop in Verilog|
| 5. FOR-GENERATE Blocks |

---


---
1. IF-CASE Constructs: Combining conditional logic in RTL (RISC-V example)
Typical usage: control mux selection, ALU ops, pipeline stages, etc.
---
```bash
module if_case_example(
    input  wire [3:0] opcode,
    input  wire [31:0] rs1, rs2,
    output reg  [31:0] alu_result
);

always @(*) begin
    if (opcode == 4'b0001) begin
        // Add operation
        alu_result = rs1 + rs2;
    end else if (opcode == 4'b0010) begin
        // Subtract operation
        alu_result = rs1 - rs2;
    end else begin
        // Default: Pass rs1 through
        alu_result = rs1;
    end
end

endmodule
```


---
2. Incomplete IF Statements
What happens if you miss an else branch?
Synthesizable but beware of inferred latches
---

```bash
module incomplete_if(
    input  wire enable,
    input  wire [7:0] data_in,
    output reg  [7:0] data_out
);

always @(*) begin
    if (enable) begin
        data_out = data_in;
    end
    // Missing else branch: may infer latch on data_out
end

endmodule
```


---
3. Incomplete - Overlapping CASE Statements
Case statements must cover all cases or have a default to avoid inferred latches
Overlapping case items can cause simulation vs synthesis mismatch
---


```bash
module case_example(
    input  wire [1:0] sel,
    output reg  [3:0] out_signal
);

always @(*) begin
    case (sel)
        2'b00: out_signal = 4'hA;
        2'b01: out_signal = 4'hB;
        // 2'b10 not handled - incomplete case!
        default: out_signal = 4'h0;  // default catches missing cases
    endcase
end

endmodule
```


---
Overlapping cases example - avoid this in SKY130RTL, can cause unexpected behavior
---


```bash
module overlapping_case(
    input  wire [1:0] sel,
    output reg  [3:0] out_signal
);

always @(*) begin
    case (sel)
        2'b00, 2'b01: out_signal = 4'h5;  // combined cases - allowed but be cautious
        2'b01: out_signal = 4'hA;          // overlapping case item - not recommended
        default: out_signal = 4'h0;
    endcase
end

endmodule
```


---
4. FOR Loop in Verilog (Procedural loop)
Commonly used for generating repetitive logic, e.g. register initialization
---


```bash
module for_loop_example #(parameter WIDTH = 8)(
    input  wire [WIDTH-1:0] data_in,
    output reg  [WIDTH-1:0] data_out
);

integer i;

always @(*) begin
    for (i = 0; i < WIDTH; i = i + 1) begin
        data_out[i] = ~data_in[i];  // bitwise inversion per bit
    end
end

endmodule
```


---
5. FOR-GENERATE (Generate block)
Used to instantiate multiple hardware blocks parametrically (structural RTL)
This is elaborated at compile time
---


```bash
module for_generate_example #(parameter NUM_REGS = 4)(
    input  wire [NUM_REGS-1:0] en,
    input  wire [7:0]          data_in [NUM_REGS-1:0],
    output wire [7:0]          data_out[NUM_REGS-1:0]
);

genvar idx;

generate
    for (idx = 0; idx < NUM_REGS; idx = idx + 1) begin : gen_regs
        assign data_out[idx] = en[idx] ? data_in[idx] : 8'b0;
    end
endgenerate

endmodule
```


---
Notes for SKY130RTL & RISC-V:
- Always include default cases to avoid latches in case statements.
- Avoid incomplete if statements without else, or else explicitly define outputs.
- Use generate loops for scalable hardware replication.
- Procedural for loops are suitable only inside always blocks.
- Simulate and lint carefully to catch overlap or latch issues in your design.
- Follow SKY130 PDK and coding standards for analog-digital mixed designs.
- RISC-V core control signals commonly use if-case combos for ALU-mux control.
- Check timing constraints and synthesis reports after RTL design for issues.
---




