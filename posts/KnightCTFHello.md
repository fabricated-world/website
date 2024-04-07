---
published: true
title: KnightCTF - Hello
description: Our solution for the "Hello" challenge of the KnightCTF 2023
author: Cartoone
date: '01/22/2023'
icon: https://ctftime.org/media/cache/34/9f/349fe0a23f72ce7efeca1cf6e9eed649.png
tags:
    - ctf
    - pwn
---
For this challenge, we are given a capture of networks, we observe it and we notice that there are several seris of request between others login **ICMP** and request **DNS**, we notice a series of requests **DNS not solved** in the form:

X.knightctf.com for X a character change for each request.

We can see that their sub-domains are one character long, so we write them one after the other to obtain :

``VBCTHtvMV9tcjNhX2VuMF9oazNfaTBofQ==````

Decoding this string, which is obviously in base 64, gives us :

```UPBL{o1_mr3a_en0_hk3_i0h}```

We can see that this string is encrypted with a substitution algorithm, as the structure seems correct. We look for the beginning of the key (we're told in the statement that the flag is coded in **vigenère**) as we know that the flag begins with KCTF we obtain KNIG we deduce that the key was KNIGHT and we obtain the flag:

```KCTF{h1_th3n_wh0_ar3_y0u}```

Solved by cartoone and maple
