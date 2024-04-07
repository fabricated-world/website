---
published: true
title: FCSC - Fibonacci
description: Our solution for one of the challenges at FCSC 2023
author: Cartoone
date: '09/01/2023'
icon: https://france-cybersecurity-challenge.fr/files/f97f907f7be4a2ceea3fc20fa0fb9650/logo-fcsc.svg
tags:
    - ctf
    - hadware
---

for this series of challenge we are asked to write code in assembler for the first challenge my algorithm was very simple (at the same time given the problem ^^)

note that I use work register 6 as the reference value for the --

```
R5 --
R1 = 0
R2 = 1
R4 = 0

do
{
R3 = R2 + R1
R1 = R2
R2 = R3

R5 --
} while (R5 != 0)

R0 = R3

exit
```

```
MOV R6,#1
SUB R5,R5,R6
MOV R1,#0
MOV R2,#1
MOV R6,#1
MOV R4,#0
JR A
A:
ADD R3, R2, R1
MOV R1,R2
MOV R2,R3
SUB R5,R5,R6
CMP R5,R4
JZR B
JR A

B:
MOV R0,R3
STP
```

which gives us the machine code : 

```
800600014dad80010000800200018006000180040000CF004a53002100324dad0645C701CFF900301400
```

which gives us the flag : 

```
FCSC{770ac04f9f113284eeee2da655eba34af09a12dba789c19020f5fd4eff1b1907}
```

by cartoone
