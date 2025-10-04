# DLD-Lab_Project



# **1. Project Overview**

The 16-bit subtractor calculator is a digital circuit designed to perform subtraction between two 16-bit binary numbers. The result of the subtraction is displayed in binary format using LEDs. The calculator uses basic digital components such as D flip-flops, multiplexers (MUX), adders, and inverters to implement the subtraction operation efficiently.

<br>

# **2. Specifications:**

Input: Two 16-bit binary numbers (A and B).
	Output: 16-bit result displayed on digital LEDs.<br>
	Operation: Subtraction (Result = A - B) using 2’s complement method.<br>

Components Used:

	1. 16 D Flip-Flops (for storing input/output data)
	2. 16 Multiplexers (for selecting input bits)
	3. 4 Adders (4-bit, combined for 16-bit addition)
	4. 74298 ICs (8-bit MUX ICs)
	5. Complementing circuitry for 2’s complement

<br>

# **3. Design Choices:**

  ### **Subtraction Method:**
  
  Implemented subtraction using 2’s complement addition:<br>
   A−B=A+(B‾+1) 

Complementing B before adding allows the use of existing adder circuits, avoiding the need for a dedicated subtractor IC.


### **Storage and Data Flow:**

16-bit registers implemented using 16 D flip-flops store input numbers and results. Flip-flops allow synchronous loading of input and hold the result until the next operation.

<br>

### **Multiplexer Usage:**

16 MUXs (via 2 × 74298 8-bit MUX ICs) were used to select between:

  - Original input bits and Complemented bits for 2’s complement operation
  - MUX selection ensures proper routing of input bits to the adder.

<br>

### **Adder Configuration:**

Four 4-bit adders were connected in series to create a 16-bit adder. This setup allows efficient handling of carry propagation across 16 bits.

<br>

# **4. Implementation:**

Input numbers A and B are stored in 16-bit registers.Each register consists of 16 D flip-flops, where each flip-flop stores one bit of the number.The 16-bit number B is complemented using bitwise NOT gates (inverters). A logic HIGH (1) is added to the least significant bit through the adder to form the 2’s complement. Multiplexers select either:<br>
  - Original A and B    
  - A and complemented B
Controlled by a selection signal to ensure subtraction is performed properly.


 ### **Addition:**
 
The 4 × 4-bit adders are connected in a ripple-carry configuration:<br>
  - First adder handles the least significant 4 bits
  - Last adder handles the most significant 4 bits, propagating any carry
  - Result of addition is the subtraction output.


 ## **Output :**
The 16-bit result is displayed via digital LEDs.Each LED represents one bit, with the most significant bit on the left and least significant on the right.

