- What are data headers?
	- HAZARDS, not headers.
- What is forwarding?

- Forwarding does not solve all the problems.
	- Load from mem, want to use data in the execution stage.
	- Pipeline: memory is after execution. generate the result of lw in memory and want to use result in stage earlier.
- lw you have rd and another register. that reg is needed in execution stage.
	- say lw x1, 0(x2). x2 is needed in execution stage. how can you find the answer?
	- sw x3, 0(x4)
		- when do you need x3? sw moves register file to memory. you need x3 in register read?

in which stage do we use data memory? - MEM.

in Data Memory what is the output? data loaded from memory.

WITHOUT forwarding:
add x1, x2, x3
sub x2, x1, x4
2 stall cycles because x1 is written to in WB, need x1 in ID stage for sub.
In ID stage you check the bits. After ID stage you are not checking any bits. Know it is subtraction in cycle 3 bc you are checking the opcode.

```
				1		2		3		4		5		6		7
--------------------------------------------------------------------
add x1,x2,x3	IF		ID		EX		MEM		WB	
--------------------------------------------------------------------
sub x2,x1,x4			IF		ID		-		-		EX		MEM
--------------------------------------------------------------------
```
2 stall cycles.

reg read/reg write in the same cycle. this happens in the ID stage.
Why can we execute sub in 6? Because we read the correct x1 value.

With forwarding, which forwarding path does the sub instruction use?
 
A. EX/MEM to EX -- this one
B. MEM/WB to EX
C. MEM/WB to MEM
D. None

add is executed in ex, so value of x1 is available.
x1 is needed for sub in ex.

$\\$

## Control Hazards

