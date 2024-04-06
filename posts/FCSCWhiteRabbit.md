---
published: true
title: FCSC - White Rabbit
description: Our solution for one of the challenges at FCSC 2023
author: Cartoone
date: '09/01/2023'
icon: https://france-cybersecurity-challenge.fr/files/f97f907f7be4a2ceea3fc20fa0fb9650/logo-fcsc.svg
tags:
    - ctf
    - cryptography
---

for this challenge, from the first time I connected to the server and entered my first sentence, I understood that the objective was to make a timing attack because the calculation time is clearly displayed in the communication, so all I had to do was make a script to automate the process. 

python
from pwn import *

HOST, PORT = "challenges.france-cybersecurity-challenge.fr", 2350

io = remote(HOST, PORT)

resp = b""

while not b "Answer: " in resp:
	rep = io.recv()
	print(resp.decode(), end='')
	print()

flag = ""

dic = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&\'()*+,-./:;<=>?@[\]^_`{|}~ '

while True:
	time = [0]*len(dic)
	for i in range(len(dic)):
		io.sendline((flag + dic[i]).encode())
		resp = b""
		tt = ""
		while not b "Answer: " in resp:
			rep = io.recv()
			tt += resp.decode()
		T1 = int(tt.split("]")[0].split("[")[1])
		T2 = int(tt.split("]")[1].split("[")[1])
		
		DT = T2-T1
		time[i] = DT
	flag += dic[time.index(max(time))]
	print(flag)
```

my script doesn't handle the case where the sentence is corect so it only displays the sentence with the last character down before crashing but the last character is easily deducible moreover as the sentence doesn't change it suffices to restart a conaction and enter manuallment the flag which is :

***FCSC{t1m1Ng_1s_K3y_8u7_74K1nG_u00r_t1mE_is_NEce554rY}***
