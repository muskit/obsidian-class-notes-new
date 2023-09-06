## Instruction Types
![[Pasted image 20230320102129.png]]

![[Pasted image 20230320102211.png]]

![[Pasted image 20230320102303.png]]

## Addressing types
Register addressing
- *note the order of registers*; **`$rd` (destination) always goes first**
![[Pasted image 20230320102440.png]]

Immediate addressing
![[Pasted image 20230320102930.png]]

Pseudo-direct addressing
  *most* of the full address is in the instruction:
	- 4MSB removed (replaced with PC's)
	- 2LSB removed (always 0, since aligned in 4s)
![[Pasted image 20230320103047.png]]

Base (indirect register) addressing
![[Pasted image 20230320103145.png]]
in this example, `$t2` is a register holding an address. parentheses **dereferences** the register by its address.

PC-relative addressing
address is *number of instructions* **OFFSET** from PC's current value
- current PC actually points to the **next** instruction to execute; when running an instruction: READ --> SHIFT --> EXECUTE
- relative address is in 2's complement if negative
![[Pasted image 20230320103602.png]]