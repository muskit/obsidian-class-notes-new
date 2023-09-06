## Final Exam Notes
- Similar to midterm: in-class & at-home
- best way to prepare for final is to be able to read an instruction's **single-cycle diagram**, as opposed to **multi-cycle diagram**

## General Advice: Specialization
Instead of learning every detail of a particular tech, focus on **one** desirable aspect of it, and **specialize** in it
- Employers look for **specialists**
- Studying the high-level "architecture" is important too.

## Ch. 4 Review

**Five Addressing Modes**
- Immediate
	- `addi`
- Register
	- `add`
- Base
	- `lw` - load word
	- called "base" bc designed to support arrays of higher-level langs
```
# t0 points to the **base** of an array.
	lw $t1, ($t0)
	lw $t1,4($t0)
	lw $t1,8($t0)
	lw $t1,12($t0)
	lw $t1,16($t0)
```
- PC-Relative
	- `beq`
- Pseudo-direct
	- `j` (jump)

**MIPS Datapath (in a cycle; loops around):**
* Instruction fetch/decode
* Operand fetch
* Execute instruction
* Memory access
* Writeback

Data Hazard (like a race condition)
- occurs when the next instruction depends on **register that the previous instruction hasn't outputted to** in the MIPS datapath yet
	- ie. `I1` is beginning *writeback* when `I2` is at *operand fetch* with `I1`'s dest. register
- solution: **forwarding**
	- ALU stores result in a temporary "register"
	- the previous instruction can access that temporary "register"

Load-Use Hazard
- occurs when next instruction depends on memory content being loaded in prev. instruction
	- ie. `I1` calls `$t0` when prev. register is `lw $t0, ...`
- solution: **stall**
	- wait for memory content to be stored into the register before continuing
	- compiler can optimize for best time to stall

## Ch.5 Prep: Locality Leads to Re-Use
*temporal*: recent activity is likely to be acknowledged again
*spatial*: proximity to activity raises likelihood of re-use