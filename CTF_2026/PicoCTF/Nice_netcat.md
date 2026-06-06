# Nice netcat...

This challenge is an introduction to the $nc command in shell. The goal is to use netcat to listen to a specific port of an address. The nc command allows the user to open a TCP connection or send UDP packets. 
We use it this way : $ nc wily-courier.picoctf.net 50025.

We get a list of numbers : 
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
100 
57 
52 
55 
54 
125 
10

So I first thought about the ASCII characters, and I translated it in actual characters : 

picoCTF{g00d_k1tty!_n1c3_k1tty!_d9476}.
