# CAPITULO 2 DEL CUADERNILLO DE PRACTICAS DE RPI ASM ARM


```asm
@ ###############################################################
@ ejercicio 2.1
@ ###############################################################
.data
.text
.global main
main:
    push{r4, r5, r6, lr}
    mov r4, #100
    ldr r5, .L5
.L2:
    mov r1, r4
    mov r0, r5
    bl printf
    subs r4, r4, #2
    bne .L2
    mov r0, r4
    pop {r4, r5, r6, pc}
.L6:
    .align 2
.L5:
    .word .LC0
.LC0:
    .ascii "%d \012\000"



###############################################################
ejercicio 2.2
###############################################################
.data
.text
.global main
main:
    push{r4, lr}
    ldr r0, .L3
    bl printf
    mov r0, #0
    pop {r4, pc}
.L3:
    .word .LC0
.LC0:
    .ascii "hola mundo\000"
    
    
##############################################################
ejercicio 2.3
##############################################################
a:  .asciz "%d es impar \012"
b:  .asciz "%d es par \012"
.text
.global main
main:   
    push {r4, lr}
    mov r4, #0
.L2:
    mov r1, r4
    ands r5, r4, #1
    cmp r5, #0
    bne else
    ldr r0, =b
    add r4, r4, #1
    bl printf
    cmp r4, #10
    bne .L2
    pop {r4, pc}
else:
    ldr r0, =a
    bl printf
    add r4, r4, #1
    cmp r4, #10
    bne .L2
    pop {r4, pc}
    
    
    
    
###############################################################
ejercicio 2.4
###############################################################
.data
.text
.global main
main:
    push {r4, r5, r6, r7, r8, lr}
    ldr r4, .L11
    ldr r5, .L11+4
    ldr r6, .L11+8
    ldr r7, .L11+12
.L6:
    ands r3, r4, #3
    moveq r1, r4
    moveq r0, r5
    beq .L10
    cmp r3, #2
    moveq r1, r4
    moveq r0, r7
    moveq r1, r4
    moveq r0, r6
.L10:
    bl printf
    ldr r3, .L11+16
    add r4, r4, #1
    cmp r4, r3
    bne .L6
    mov r0, #0
    pop {r4, r5, r6, r7, r8, pc}
.L11:
    .word 1950
    .word .LC0
    .word .LC2
    .word .LC1
    .word 2015
.LC0:
    .ascii "En %d hubo olimpiadas\012\000"
.LC1:
    .ascii "En %d hubo mundial de futbol\012\000"
.LC2:
    .ascii "En %d no paso nada\012\000"
```
