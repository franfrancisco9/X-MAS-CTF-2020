# X-MAS-CTF-2020
This was my first attempt at a CTF after being recently introduced to the concept. I challenged a friend and we set to try and do as many challenges as possible.
Personally, I also had the goal of trying to understand how the different types of areas worked and which ones I had most insterest!
The format of the CTF allowed for just that, specially with the adding of new challenges every other day as well as a good and active community on discord.
Great description of the competition can be found in the official competition website: <https://xmas.htsp.ro/home>

This will be my first attempt at write ups, so any suggestions let me know! Here is my discord Franfrancisco9 #0105

List of the categories and challenges I solved:
- [!Sanity Check](https://github.com/franfrancisco9/X-MAS-CTF-2020/edit/main/README.md/!Sanity_Check)
    - [Merry Christmas!](https://github.com/franfrancisco9/X-MAS-CTF-2020/edit/main/README.md/Merry_Christmas!_(5/5_Points))

*Note: For every challenge I will present the points they had at the end of the competition / the points at the begginning as the platform adjusted the difficulty according to how many teams have solved the challenge*

*Note 2: For every challenge I will give my personall evaluation of difficulty*

## !Sanity Check
>Introdutory category and just for fun 


#### **Merry Christmas! (5/5 Points)**

First challenge when you entered the competition made for fun as a welcoming text, flag was given in the description:

![Image of Merry Christmas!](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Merry_Christams!.png)

Flag was **X-MAS{H0_H0_H0_H4ck_4_4_br1gh73r_fu7ur3_4nd_m3rry_X-MAS!!!}**

#### **The place where all the elves hang out  (5/5 Points)**

Another fun challenge where you were directed to join the discord server and haas the name suggests, when checking *general* channel's description, there was your flag:

![The place where all the elves hang out](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/The_Place_Where_All_The_Elves_Hang_Out.png)

Flag was **X-MAS{Alr1gh7_50_W3_g07_734_b15cui75_4nd_7h3_w4rm357_w1n73r_50ck5_w3_c0uld_f1nd.L37'5_g0!}**

## Forensics 

#### **Conversation (26/50 Points)**
>Author: Yakuhito

![Image of conversation description](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Conversation/Conversation_Description.png)

We were given a file called *logs.pcapng*, and being new to CTF competitions I followed all the introductory steps you can find online when dealing with any file, being one of them of course the strings function.

Uppong calling the strings function, after some scrolling you could found the folling sequence of readable text:
>Hello there, yakuhito

>Hello, John! Nice to hear from you again. It's been a while.

>I'm sorry about that... the folks at my company restrict our access to chat apps.

>Do you have it?

>Have what?

>The thing.

>Oh, sure. Here it comes:

>Doesn't look like the thing

>A guy like you should know what to do with it.

At first I was really confused because it seemed there was nothing but giberish after *Here it comes:* but after a close look I noticed a text sequence that suggested some sort of base64 encryptation

>JP1ADIA7DJ5hLI9zpz9gK21upzgyqTyhM19bLKAsLI9hMKqsLz95MaWcMJ5xYJEuBQR3LmpkZwx5ZGL3AGS9Pt==

I imidiately run the echo | base64 --decode line just to find a pack of unreadable chars. After some digging I was recommend [cyberchef](https://gchq.github.io/CyberChef/), which definetely the best tool to quickly run over basic encodings, analysis, etc ( specially for begginers!)

I used the magic analysis and immediatly got a response with ROT13 base64 decoding:

![Imgae of conversation cyber chef](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Conversation/Conversation_Cyber_Chef.png)

Flag was **X-MAS{Anna_from_marketing_has_a_new_boyfriend-da817c7129916751}**

Difficulty:  *Easy* 

I felt like this was a pretty standart and easy challenge, which also showed me the importance of starting to identify the most common types of encoding
























