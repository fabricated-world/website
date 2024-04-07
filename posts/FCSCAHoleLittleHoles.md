---
published: true
title: FCSC - A hole, little holes...
description: Our solution for one of the challenges at FCSC 2023
author: Cartoone
date: '09/01/2023'
icon: https://france-cybersecurity-challenge.fr/files/f97f907f7be4a2ceea3fc20fa0fb9650/logo-fcsc.svg
tags:
    - ctf
    - misc
---

In this challenge, we are provided with punch cards from the IBM-029 machine. This punch card technique was used to store data in the distant past when mass storage had not yet seen the light of day:

![Image of the puch cards provided with the challenge](/blog/FCSCAHoleLittleHoles.jpg)

after some research i came across the following web page:

http://laighside.com/punchcard.htm

but we're missing the settings after some research on the IBM-029 drilling machine we end up finding a card format that corresponds to ours **80x12** we apply these settings and effectively decode our first card then I used this python script with basically the same settings to automatically decode all the other cards:

https://github.com/digitaltrails/punchedcardreader

once all the cards have been decoded, we get what amounts to a computer program we do a quick historical search and discover that 70 years ago, when the machine in question was released, two programming languages dominated the market: **cobolte** and **fortran** we also notice that in the program we've just decoded there are comments and that they all start with a "!" based on this information, we can conclude that the language of the mysterious program is **fortran**.

the second part of the challenge, in addition to decoding, was to put the program back in order. it's based on **4** loops, equivalent to our for loop, and uses the variable i as an index. we can therefore classify the instructions into two categories: those that use i in their syntax and the others. in the lines that don't use i, you'll find a number of set-up lines used to declare variables or to include a set of data, so at the top you'll also see 3 instructions that will end the program - an equivalent of what would be a print("") in python, an instruction that would be the equivalent of return 0 in C, and finally an instruction that tells the compiler that the program is finished. Thanks to these deductions, we've reconstructed a good part of the program, leaving the body of the program to be rebuilt. I assumed that the loops were not nested, so I put the instructions in the following order, using abbreviations in the following section:

SSS = S1
SS = SSS
SSS = S2
SSSS = SSS

we start by putting each of them in a loop, then we add the write instruction in the last one to display the result, then we execute the code which now looks like this:

```fortran-free-form
! --------------------------------------------------
PROGRAM HELLO
USE HELLO_1
IMPLICIT NONE
901 FORMAT (99A)

INTEGER :: SSS(0:255)
CHARACTER :: SSSS(0:255)
INTEGER :: I
! - - - - - -

DO I = 0,29,1
SSS(I:I) = S1(SS(I+1)+1:SS(I+1)+1)
END DO

DO I = 0,29,1
SS(H(I+1)+1:H(I+1)+1) = SSS(I:I)
END DO

DO I = 0,29,1
SSS(I:I) = S2(SS(I+1)+1:SS(I+1)+1)
END DO
! - - - - - -

DO I = 0,29,1
SSSS(I:I) = CHAR(SSS(I:I))
WRITE (*,901,ADVANCE='NO') SSSS(I:I)
END DO

WRITE (*,901,ADVANCE='YES') ''

STOP 0
END PROGRAM

! --------------------------------------------------
```

and it returns:

```
FCSC{#!F0RTR4N_1337_FOR3V3R!}
STOP 0
```
