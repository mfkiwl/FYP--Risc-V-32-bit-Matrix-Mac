
##### By [Saad Khan](https://www.linkedin.com/in/saad-k-7aba04138/)

<table>
  <tr>
    <th>S. No</th>
    <th>Note</th>
  </tr>
  <tr>
    <td>0</td>
    <td>RISC-V has 5 steps: fetch, decode, execute, memory ops (optional), and writeback (optional).</td>
  </tr>
  <tr>
    <td>0.1</td>
    <td>
        <b>Register File:</b></br>
        <ul>
            <li>    RISC-V has a <b>32bit-Register File with 32 Registers</b> of different Types(R, I, S, B, U, J).</li>
            <li>It also acts as tmp registers to work directly with ALU.</li>
            <li>it has 5 input ports as A1,A2,A3 and WD3,WE3, and 2 output ports as RD1 and RD2. A3 is the address of the register to store the data which is in WD3 register. it also has a flag, as WE3, known as Write enable on active high. </li>
            <li>A1, A2 are connected to RD1 & RD2 respectively, to be able to read 2 different registers value/data concurrently, whose addresses are in A1 and A2. </li>
            <li>A3 is usually the destination register, to store the value in case of addition/subtraction, etc</li>
        </ul>
    </td>
  </tr>
  <tr>
    <td>0.2</td>
    <td>
        <b>Instruction Types:</b></br>
        6 types (R, I, S, B, U, J) of instructions in RISC-V:
        <ul>
          <li><b>R-Type</b> (Register Type): An operation on registers (x5, x6).</li>
          <li><b>I-Type</b> (Load/Load Immediate): Load variables/registers with values or constants from external memory, where a constant is used.
            <ul>
              <li>x5, x6, 7; <i>// load Immediate</i></li>
              <li>lw x8, offset(Base); <i>// load 32-bit word from memory to x8</i></li>
              <li>lw x8, 4(x6); <i>// Memory Base stored in X6 register, with 4 byte as an offset</i></li>
              <li>Note: offset is in increments of 4 bytes, in hex. i.e., 4, 8, c, etc.</li>
            </ul>
          </li>
          <li><b>S-Type</b> (Store Type): use to store values from registers in register file to the <b>external memory</b>
            <ul>
              <li>sw rs2, offset(rs1 (aka Base)); <i>// store word from source register to memory</i></li>
              <li>sw x9, 8(x6); <i>// store x9 into memory with base in x6 with 8 offset</i></li>
              <li><b>Note</b>: offset is also known as Immediate or Imm.</li>
            </ul>
          </li>
          <li><b>B-Type</b> (Branch Type):
            <ul>
              <li>beq x8, x9, 8; <i>// branch if equal, compare x8 and x9 if equal, jump to immediate 8, or point PC to immediate.</i></li>
            </ul>
          </li>
        </ul>
    </td>
  </tr>
  <tr>
  <td>0.3</td>
  <td>
    <b>Data Memory</b></br>
    <ul>
        <li> it has a signle read/write port. if WE (write enable) is 1, it writes data which is in WD into address A on posedge clk. if the WE is 0, it reads Address A onto RD</li>
    </ul>
  </td>
  
  </tr>
  <tr>
    <td>0.4</td>
    <td><b>PC: </b> The Program Counter is a standard 32-bit register with a read port and a PCNext value, which points to the next instr. It takes a 32-bit address (A) and reads the corresponding 32-bit data from the instruction memory, outputting it to the RD (read) port. </td>
  </tr>
  <tr>
    <td>1</td>
    <td>RISC-V prefers <b>5-stage pipelining</b>, but usually, 14 stages are preferred. We will try to achieve at least 10 stages.</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Pipelining has 3 types of hazards.</td>
  </tr>
  <tr>
    <td>3</td>
    <td>
      <ul>
        <li>A) <b>Structural Hazard</b>: When hardware cannot execute planned instruction because of hardware limitation in the next clock cycle. When the processor has a single memory, use separate instruction and data memory.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>4</td>
    <td>
      <ul>
        <li>B) <b>Data Hazard</b>: When data needed to execute an instruction is not yet available, use bypassing/forwarding or Nops(Stalling) to fix this.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>5</td>
    <td>Note: Load-use data hazard: Using data that isn't loaded yet, bubbles/wasted cycles are used to stall the computer so once the data gets loaded, then to use it.</td>
  </tr>
  <tr>
    <td>6</td>
    <td>
      <ul>
        <li>C) <b>Control Hazard</b>: Branching hazard, when needed to make a decision based on one instruction while others are executing, basically calculating whether to branch or not, while the next instruction gets executed. One solution is to stall until the branch condition gets calculated, good but slow. The best solution is to predict branches!!! Mostly take branches' condition as false, if you get wrong and the branch is actually true, just add delay to it.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>7</td>
    <td>Note: Pipelining only improves throughput.</td>
  </tr>
  <tr>
    <td>8</td>
    <td><b>Temporal locality</b>: If a data location is referenced, it is likely to be referenced again.</td>
  </tr>
  <tr>
    <td>9</td>
    <td><b>Spatial locality</b>: If a data location is referenced, the location with nearby addresses will likely be referenced soon.</td>
  </tr>
  <tr>
    <td>10</td>
    <td>Memory hierarchy (Speed): SRAM &gt;&gt; DRAM &gt;&gt; Disk.</td>
  </tr>
  <tr>
    <td>11</td>
    <td>Memory hierarchy is of different levels, but we can only access 2 adjacent levels at a time.</td>
  </tr>
  <tr>
    <td>12</td>
    <td>Memories: SRAM -&gt; Cache, DRAM -&gt; Main Memory, flash/magnetic -&gt; secondary memory.</td>
  </tr>
</table>



##### By [Zaeem Shakir](https://www.linkedin.com/in/syed-zaeem-shakir-85b82125b/)



<table>
  <tr>
    <th>S. No</th>
    <th>Note</th>
  </tr>
  <tr>
    <td>1</td>
    <td>
        <h4><b>Verilog Basic Code Examples</b></h4>
        <ol>
        <li>
            <pre>module ANDGate(input a, input b, output y);
assign y = a & b;
endmodule</pre>
        </li>
    <li>
        <pre>
module ORGate(input a, input b, output y);
  assign y = a | b;
endmodule
        </pre>
        </li>
        <li>
        <pre>
module NOTGate(input a, output y);
  assign y = ~a;
endmodule
        </pre>
        </li>
        <li>
        <pre>
module RippleCarryAdder(input [3:0] A, input [3:0] B, output [3:0] Sum, output Carry);
  assign Carry = 0;
  genvar i;
  generate
    for (i = 0; i < 4; i = i + 1) begin
      assign Sum[i] = A[i] ^ B[i] ^ Carry;
      assign Carry = (A[i] & B[i]) | (Carry & (A[i] ^ B[i]));
    end
  endgenerate
endmodule
        </pre>
        </li>
         <li>
          <pre>
module SyncCounter(input clk, input rst, output reg [2:0] count);
  always @(posedge clk) begin
    if (rst)
      count <= 0;
    else
      count <= count + 1;
  end
endmodule
  </pre>
        </li>
        <li>
        <pre>
module RAM(input [1:0] address, input [7:0] data_in, input write_enable,
           output reg [7:0] data_out);
  reg [7:0] mem [3:0];

  always @(address) begin
    data_out <= mem[address];
  end

  always @(posedge clk) begin
    if (write_enable)
      mem[address] <= data_in;
  end
endmodule
  </pre>
  </li>
        </ol>
    </td>
  </tr>
  <tr>
    <td>2</td>
    <td>.</td>
  </tr>
</table>







##### By [Mahnoor Maleeka](https://www.linkedin.com/in/mahnoormaleeka/)

<table>
  <tr>
    <th>S. No</th>
    <th>Note</th>
  </tr>
  <tr>
    <td>1</td>
    <td>
      <h4>SystemVerilog VS Traditional Verilog</h4>
      <ul>
        <li><b>Data Types:</b> SystemVerilog introduces additional data types like logic, bit, byte, int, shortint, longint, enum, struct, union, real, and time. These new data types provide more flexibility in representing and handling different types of data.</li>
        <li><b>Interfaces:</b> SystemVerilog introduces interfaces, which are collections of signals and methods.</li>
        <li><b>Clocking Blocks:</b> SystemVerilog introduces clocking blocks to model clock and reset signal properties more accurately, particularly with regards to multiple clock domains.</li>
        <li><b>Constraints and Randomization:</b> SystemVerilog provides upgraded randomization abilities with the `rand` keyword and constraint blocks. These features enable generating random test cases for verification purposes.</li>
        <li><b>Assertions:</b> SystemVerilog incorporates support for assertions using the `assert`, `assume`, `cover`, and `restrict` keywords. These constructs enable designers to specify properties and requirements on signals and variables to check the correctness of the design during simulation.</li>
      </ul>
    </td>
  </tr>
</table>

