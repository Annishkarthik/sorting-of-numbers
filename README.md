# sorting-of-numbers
## Aim
To write and execute an Assembly Language Program for sorting data in Ascending and  descending order using 8051 microcontroller on Keil software.
---

## Apparatus Required
- Personal Computer  
- Keil µVision software  
---

## Algorithm(ASCENDING ORDER)
1. Initialize the register **R7** with count (number of elements).  
2. Get the first two elements into two registers.  
3. Compare the two elements:  
   - If the value in register **R0** is lower, exchange **A** and **R0** data.  
   - Otherwise, increment pointer and decrement register **R7**.  
4. Check if **R7 = 0** → if yes, move the register **R0 & A**.  
5. Increment pointer and decrement **R7**.  
6. If **R7 ≠ 0**, repeat from Step 2.  
7. Otherwise, stop the program.  
---

## Program (Ascending order)

```asm
;------------------------------------------------
; Program : Sorting in Ascending Order
; Microcontroller : 8051
; Software : Keil
;------------------------------------------------

ORG 0000H

MOV R0, #30H       ; Starting address of data
MOV R7, #04H       ; Number of comparisons

OUTER:
    MOV R1, #30H   ; Start of array
    MOV R6, #04H   ; Number of comparisons

INNER:
    MOV A, @R1     ; Get first element
    MOV R2, A      ; Store first element in R2

    INC R1
    MOV A, @R1     ; Get second element

    CJNE A, R2, COMPARE

COMPARE:
    JC NO_SWAP     ; If A < R2, no exchange

    MOV R3, A      ; Store second element
    MOV A, R2
    MOV @R1, A     ; Move first element to second position

    DEC R1
    MOV A, R3
    MOV @R1, A     ; Move second element to first position

    INC R1

NO_SWAP:
    DJNZ R6, INNER
    DJNZ R7, OUTER

HERE:
    SJMP HERE

END



```
## OUTPUT(Ascending order)
Input Data

Store the data in internal RAM before execution:

Address	Data
30H	25H
31H	12H
32H	45H
33H	08H
34H	30H
Output — Ascending Order

After execution:

Address	Data
30H	08H
31H	12H
32H	25H
33H	30H
34H	45H

Output: 08H, 12H, 25H, 30H, 45H


---

## Algorithm(Descending order)
1. Initialize the register **R7** with count.  
2. Get first two elements in two registers.  
3. Compare the two elements of data:  
   - If the value of **R0** register is high, then exchange **A** and **R0** data.  
   - Else, increment pointer and decrement register **R7**.  
4. Check if **R7 = 0**, then move the contents of **R0** and **A**.  
5. Again increment pointer and decrement **R7**.  
6. Check if **R7 = 0**:  
   - If **No**, repeat the process from Step 2.  
   - If **Yes**, stop the program.  
---
## Program (Descending order)

```asm
;------------------------------------------------
; Program : Sorting in Descending Order
; Microcontroller : 8051
; Software : Keil
;------------------------------------------------

ORG 0000H

MOV R7, #04H       ; Number of passes

OUTER:
    MOV R1, #30H   ; Starting address
    MOV R6, #04H   ; Number of comparisons

INNER:
    MOV A, @R1     ; Get first element
    MOV R2, A      ; Store first element

    INC R1
    MOV A, @R1     ; Get second element

    CJNE A, R2, COMPARE

COMPARE:
    JNC NO_SWAP    ; If A > R2, no exchange

    MOV R3, A      ; Store second element
    MOV A, R2
    MOV @R1, A     ; Move first element to second position

    DEC R1
    MOV A, R3
    MOV @R1, A     ; Move second element to first position

    INC R1

NO_SWAP:
    DJNZ R6, INNER
    DJNZ R7, OUTER

HERE:
    SJMP HERE

END



```
## OUTPUT(Descending order)

Input Data
Address	Data
30H	25H
31H	12H
32H	45H
33H	08H
34H	30H
Output — Descending Order

After execution:

Address	Data
30H	45H
31H	30H
32H	25H
33H	12H
34H	08H

Output: 45H, 30H, 25H, 12H, 08H


---
## RESULT:
Thus the sorting of given data was done using 8051 keil software.

