Past concept of computing: abstraction
`hardware --> processor --> asm --> high-level language`

Wasn't a great to think of it, so we came up with **Instruction Set Architecture**
`software --> high-level --> hardware --> asm --> instruction set --> hardware`

**How can we go from instruction set to hardware?**

Recall the Von Neumann cycle:
- fetch
- decode
- execute



A proposed architecture: Modified Harvard architecture
![[Pasted image 20230416201609.png]]
![[Pasted image 20230416201401.png]]
A curious question: why the separation of memory?

In the first image, we still need a **controller** that handles operation flow. To connect the controller to these components, we add **2-to-1 multiplexers**.
![[Pasted image 20230416203108.png]]
Doesn't quite have enough components to recreate a Von Neumann machine.

***2-to-1 multiplexer (mux)*: given two inputs, another "control" input determines which one gets outputted.