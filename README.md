# X-MAS-CTF-2020
This was my first attempt at a CTF after being recently introduced to the concept. I challenged a friend and we set to try and do as many challenges as possible.
Personally, I also had the goal of trying to understand how the different types of areas worked and which ones I had most insterest!
The format of the CTF allowed for just that, specially with the adding of new challenges every other day as well as a good and active community on discord.
Great description of the competition can be found in the official competition website: <https://xmas.htsp.ro/home>

I participated alongside [Francisco Rodrigues](https://github.com/ArmindoFlores) and we ended up in 97th.

My teammate did a write up for *Santa's ELF holomorphing machine* (which was one of the most interessing and fun challenges in my opinion, that you can found [here](https://gist.github.com/ArmindoFlores/21bea2dd3e75040115498754f42864c6)

This will be my first attempt at write ups, so any suggestions let me know! Here is my discord *Franfrancisco9 #0105*

List of the categories and challenges I solved:
- !Sanity Check
    - [Merry Christmas!](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#merry-christmas-55-points)
    - [The place where all the elves hang out](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#the-place-where-all-the-elves-hang-out--55-points)
- Forensics
    - [Conversation](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#conversation-2650-points)
- Miscellaneous
    - [PMB](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#pmb-5050-points)
    - [Bobi's Whacked](https://github.com/franfrancisco9/X-MAS-CTF-2020#bobis-whacked-5050-points)
    - [Whispers of Ascalon](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#whispers-of-ascalon-5050-points)
- Programming
    - [Biggest Lowest](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#biggest-lowest-3750-points)
    - [Least Greatest](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#least-greatest-5050-points)
- Web Exploitation
    - [PHP Master](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#php-master-3350-points)
    - [Santa's Consolation](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#santas-consolation--5050-points)
    
*Note: For every challenge I will present the points they had at the end of the competition / the points at the begginning as the platform adjusted the difficulty according to how many teams have solved the challenge*

*Note 2: For every challenge I will give my personall evaluation of difficulty*

## !Sanity Check
>Introductory category and just for fun 


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

Uppon calling the strings function, after some scrolling you could found the folling sequence of readable text:
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

## Miscellaneous

#### **PMB (50/50 Points)**
>Author: Yakuhito

![Image of PMB description](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_description.png)

This challenge was really all about the nuances in the different descriptions. After connecting with the given IP you would be greeted by this menu:

![Image of PMB Menu](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_menu.png)

They tell us our number cannot have a modulus higher or equal to 100 and that it can ***any*** number ( this will be important). I started with some basic tests:

>Interest: 1

![PMB months](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_months.png)

So it seems that is a simple multiplication process each month, the problem is we cannot have any positive value until the last month.

That is where the ***any*** so strongly written importance appears, as it is sopposed to remind us that you can also use complex numbers! They also have a modulus to respect but they have this great thing where for z = a + bj if we have a = 0 and b = 1, then we have j

And j^2 = -1, and -1j = -j and -j^2 = 1, which means we just need to use a certain b with j that gets us to the required 10 million

That number is 10, as 10 x 1000 = 10 000, 10 000 x 10 = 100 000, 100 000 x 10 = 1 000 000 and 10 x 1 000 000 = 10 000 000 000

Joining 10 with j (does not matter if it is -10j or 10j) we will get to the 10 million and obtain the flag:

![PMB flag](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_flag.png)

Flag was **X-MAS{th4t_1s_4n_1nt3r3st1ng_1nt3r3st_r4t3-0116c512b7615456}**

Difficulty:  *Easy*


Great challenge that shows importance of reading descriptions carefully!

#### **Bobi's Whacked (50/50 Points)**
>Author: Bobi

For this challenge we start with nothing else but this line:

![Bobis description](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Bobi's%20Whacked/Bobis_Whacked_Description.png)

This suggests this is an OSINT challenge, meaning we have to look for clues online, usually in social media or other available websites, and try to follow clues or hints for the information we want.

In this case I immediatly looked the name *Bobi whack* and found one channel on the name *Bobi's wHack*. 

The reason i immediatly went for youtube is because the description mentions *caption* which is a usual word for subtitles.

4 videos showed to have captions inserted by the channel owner. By clicking on the video and choosing the transcript option I got to text bits:

>X-MAS{nice_thisisjustthefirstpart

>_congrats}

I tested to submit *X-MAS{nice_thisisjustthefirstpart_congrats}* but it did not work, meaning there is probably a middle section missing.

When checking the channel, I found the following sequence in the *about* section:

>6D6964646C6570617274

Using cyber chef we got from hex decoding the word *middlepart*

Flag was **X-MAS{nice_thisisjustthefirstpart_middlepart__congrats}**

Difficulty:  *Easy*

Great challenge overall

#### **Whispers of Ascalon (50/50 Points)**
>Author: Bobi

For this challenge the description had the following quote:

>*The one who bears the Magdaer shall curse his people forever after*

As well the following image:

![Whisper os Ascalon](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Whispers%20of%20Ascalon/Whispers_of_Ascalon.png)

Now, at first this did not called for anything to me, but after some research of the name *Magdaer*, I quickly understood this was part of the game Guild of Wars 2.

All it took was some look around in the Guild Wars Official Wiki (<https://wiki.guildwars2.com/wiki/Main_Page>) to find the so called *New Krytan* alphabet along side a handy translation:

![whispers translation](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Whispers%20of%20Ascalon/Whispers_of_Ascalon_translation.png)

After that was just getting the flag.

Flag was **X-MAS{GW2MYFAVORITEGAME}**

Difficulty:  *Easy*

All about looking for the description references!

## Programming

#### **Biggest Lowest (37/50 Points)**
>Authors: Gabies and Nutu

The challenge had the following description:

    I see you're eager to prove yourself, why not try your luck with this problem?

    Target: nc challs.xmas.htsp.ro 6051

    When you connected to the given address you were greated with a little introduction of how hte challenge works 
    (this will be very similar across all programming challenges):

    So you think you have what it takes to be a good programmer?

    Then solve this super hardcore task:

    Given an array print the first k1 smallest elements of the array in increasing order and then the first k2 elements of the array in decreasing order.

    You have 50 tests that you'll gave to answer in maximum 45 seconds, GO!

    Here's an example of the format in which a response should be provided:

    1, 2, 3; 10, 9, 8

After which was the values you had to work with in this format:

    Test number: 1/50

    array = [2, 5, 9, 3, 8]

    k1 = 2

    k2 = 1

It becomes clear we need a script to achieve such a fast order otherwise you do not have time to do all 50 tests, specially because after a certain number the arrays of numbers become way to big.

Being fairly new to python, this was the perfect challenge to learn some of the basics of connections and socket send a receive functions(even though I have been now thought about the wonders and much perks of using pwn). Nonetheless, here was my approach when doing the code, followed by the actual code commented:

    - Setup connection to the address and retrieve all the necessary values
    
    - Sort the given numbers from low to high and then high to low
    
    - Make the sort only until the specified k1 or k2 elements
    
    - Set up the correct form for input ( e.g: 1, 2, 3; 10, 9, 8)
    
    - Send the input
    
    - Implement loop to do this for the 50 tests
    
```python
import socket

# Connection set up
ip = 'challs.xmas.htsp.ro'
port = 6051
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.connect((ip, port))

# Get the first set of data
data = sock.recv(16000)
#print(data)

# Loop to ensure the 50 tests
for x in range(51):

    # So I could follow along
    print("Test number ", x + 1, '\n')

    # Splitting the received data so we only look for the numbers we care about)
    data = data.split(b'array = ')[-1]

    # Take all the symbols connected to numbers and replace with spaces ( this allows us to get all numbers directly)
    numbers = data.replace(b',', b'')
    numbers = numbers.replace(b'[', b'')
    numbers = numbers.replace(b']', b'')
    dat = numbers.decode()

    # By this point we get an array that contains all the values to order and in the last to slots the k1 and k2 values
    res = [int(i) for i in dat.split() if i.isdigit()]

    # small test so did not get errors showing up when i made mistakes
    if len(res) == 0:
        break

    # I used the sorted function and first did an overall sorting of the array minus the k1 and k2
    increase = sorted(res[0:len(res)-2])

    # Then I did it again (even though it is already sorted, but only for the first k1 numbers9
    # There is probably a direct way, but starting with normal sorting this gave back exactly what I wanted
    increase1 = sorted(increase[0:res[len(res) - 2]])

    # Same process but now we do the reverse order and use k2
    decrease = sorted(res[0:len(res)-2], reverse = True)

    decrease1 = sorted(decrease[0:res[len(res)-1]], reverse = True)

    # We start the string that will be passed to input
    str1 = ''

    # this will add the numbers we obtained plus the commas
    for i in range(len(increase1)):
        if i != len(increase1) - 1:
            str1 = str1 + str(increase1[i]) + ',' + ' '
        else:
            str1 = str1 + str(increase1[i])

    # Separation between the k1 and k2 orders
    str1 = str1 + ';'

    # Starts with space
    str2 = ' '

    # Same process as in k1
    for i in range(len(decrease1)):
        if i != len(decrease1) - 1:
            str2 = str2 + str(decrease1[i]) + ',' + ' '
        else:
            str2 = str2 + str(decrease1[i])

    # Adding the \n so at the end of the string it presses enter
    strfinal = str1 + str2 + '\n'

    #print(strfinal)

    # send the input!
    sock.send(strfinal.encode())

    # after sending we get the info for the next test in the loop
    data = sock.recv(16000)

# this prints the last data that is the string (x = 51)
print(data.decode())
```

After running the code we were greeted with a winning text:

    Good, that's right

    Those are some was lightning quick reflexes you've got there!

    Here's your flag: X-MAS{th15_i5_4_h34p_pr0bl3m_bu7_17'5_n0t_4_pwn_ch41l}

Flag was **X-MAS{th15_i5_4_h34p_pr0bl3m_bu7_17'5_n0t_4_pwn_ch41l}**

Difficulty:  *Medium Easy*

Even though it certainly was one of the easiest, since I was so unfammiliar with python, it took obviously longer than it should, but gave me excellent tools to do the next challenge and made it feel much easier!

#### **Least Greatest (50/50 Points)**
>Authors: Gabies and Nutu

As mentioned in *Biggest Lowest*, the approach for this challenge was very much similar, the difference being we now wanted to find the number of pairs of numbers *(x.y)* thatd had the given *greates common divisor* and *least common multiple*.

We were given the following description:

    Today in Santa's course in Introduction to Algorithms, Santa told us about the greatest common divisor and the least common multiple.
    He this gave the following problem as homework and I don't know how to solve it.
    Can you please help me with it?

    Target: nc challs.xmas.htsp.ro 6050
 
After connecting to target we had the following introduction:
  
    Hey, you there! You look like you know your way with complex alogrithms.
    There's this weird task that I can't get my head around. It goes something like this:
    Given two numbers g and l, tell me how many pairs of numbers (x, y) exist such that gcd(x, y) = g and lcm(x, y) = l
    Also, i have to answer 100 such questions in at most 90 seconds.

So, like I said, the exact same process will be used, but now the format of the numbers is:

    Test number: 1/100                                                                                                       
    gcd(x, y) = 6272065202853374095609                                                                                       
    lcm(x, y) = 3724998340170227435504471927 

After some research, I found out that the GCD and LCM are actually easy to interconnect and my first approach was to use the property that 
*xy = GCD x LCM*, and since x and y will be smaller or equal to the LCM, trying all possible pairs with product equal to *GCD x LCM*.
Well, it does not surprise that this did not work for the big tests, since numbers get insanely huge.

I had to make it more effiecient, which entailed the need to change algorithm to something much more efficient. After some research I found a lot of websites describing an approach trhough a prime factor method. Here is the idea behind it:

    We know that GCD * LCM = x * y
    Since GCD is gcd(x, y), both x and y will have GCD as its factor
    
    Let X = x/GCD
    Let Y = y/GCD

    This means GCD(X, Y) = 1
    We can write, x = GCD * X, x = GCD * Y

    GCD * LCM = GCD * X * GCD * Y
    X * Y = LCM / GCD
    
    So we need all pairs of (X, Y) thats respect gcd(X, Y) = 1 and X*Y = LCM/GCD
    
    This is where the prime factors come in, as if we consider p1, p2 up to pk as prime factors of LCM/GCD
    
    Then if p1 is present in prime factorization of X then p1
    can't be present in prime factorization of Y because 
    gcd(X, Y) = 1.
    
    This means each prime factor is either in X or in Y
    This concludes that the total possible ways to divide all prime 
    factors among X and Y is 2^k, where LCM/GCD has k distinct 
    prime factors.
    
Whit this in mind this was the final script:

```Python

# Efficient python3 program to count  
# all pairs with GCD and LCM.  

# A function to find number of distinct  
# prime factors of a given number n  
def totalPrimeFactors(n):
    # To keep track of count
    count = 0;

    # 2s that divide n
    if ((n % 2) == 0):
        count += 1;
        while ((n % 2) == 0):
            n //= 2;

            # n must be odd at this point.
    # So we can skip one element
    # (Note i = i +2)
    i = 3;
    while (i * i <= n):

        # i divides n
        if ((n % i) == 0):
            count += 1;
            while ((n % i) == 0):
                n //= i;
        i += 2;

        # This condition is to handle the
    # case when n is a prime number
    # greater than 2
    if (n > 2):
        count += 1;

    return count;


# function to count number
# of pair with given GCD and LCM
def countPairs(G, L):
    if (L % G != 0):
        return 0;

    div = L // G;

    # answer is 2^totalPrimeFactors(L/G)
    return (1 << totalPrimeFactors(div));


import socket

# connection
ip = 'challs.xmas.htsp.ro'
port = 6050
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.connect((ip, port))
data = sock.recv(8192)

for x in range(101):
    # So I could follow along
    print("Test number ", x + 1)

    pairs = 0
    res = [0, 0]

    # print(data)

    if data.find(b'gcd') != -1:
        # get the numbers we need
        numbers = data.split(b'gcd')[-1]
        dat = numbers.decode()
        # print(data)

        # we only want the numeric values
        [res[0], res[1]] = [int(i) for i in dat.split() if i.isdigit()]

        # print(res)

        # iniciate the counting of the pairs
        pairs = countPairs(res[0], res[1])
        # print(pairs)

        # prepare the string to send
        pairs = str(pairs) + '\n'

        # sending the value to input
        sock.send(pairs.encode())

        # get data for next loop round
        data = sock.recv(8192)

# this prints the last data that is the flag(x = 101)
print(data.decode())
```
Just run it and we get the winning text:

    Wow, you really know this kind of weird math?
    Here's your flag: X-MAS{gr347es7_c0mm0n_d1v1s0r_4nd_l345t_c0mmon_mult1pl3_4r3_1n73rc0nn3ct3d}
    
Flag was **X-MAS{gr347es7_c0mm0n_d1v1s0r_4nd_l345t_c0mmon_mult1pl3_4r3_1n73rc0nn3ct3d}**

Difficulty:  *Easy*

Thanks to the first programming challenge this one felt much easier and just all about finding an effiecient method to solve the challenge.


## Web Exploitation

#### **PHP MAster (33/50 Points)**
>Author: Yakuhito

The description was:

    Another one of *those* challenges.
    Target: http://challs.xmas.htsp.ro:3000/

When we got in the web page we could see the following code:

```php
<?php

include('flag.php');

$p1 = $_GET['param1'];
$p2 = $_GET['param2'];

if(!isset($p1) || !isset($p2)) {
    highlight_file(__FILE__);
    die();
}

if(strpos($p1, 'e') === false && strpos($p2, 'e') === false  && strlen($p1) === strlen($p2) && $p1 !== $p2 && $p1[0] != '0' && $p1 == $p2) {
    die($flag);
}

?>
```

I never had any contact with php before, but after some chatting with my colleague and some overall research online, I understood that I need to find the correct values for param1 and param2 ( as they are required as inputs with the *$_GET* function) so that we activated the code part where they give us the flag (*die($flag)*)

The first if segment only checks if the varaibles have any value and are not NULL.

The second if is what we care about as it describes the required relationship between param1 and param2.

The first definition is 
```php 
strpos($p1, 'e') === false && strpos($p2, 'e') === false 
```
Which basically means that param1 and param2 cannot have the letter e. It is interesting to note that it does not check for ther letter E, which allowed for another solution that I did not consider at the time

Then we have:
```php 
strlen($p1) === strlen($p2) && $p1 !== $p2
```
So param1 and param2 need to have the same lenght, but their values ( considering the type) have to be different, but then we are told that:
```php
 $p1[0] != '0' && $p1 == $p2
```
Which tells us that the first character of param1 cannot be 0 and that apprently param1 = param2. This seems to go against what we saw in the above line. However, in php == is different than === and != is different than !==, the two first do not take into account the data type of variables, whereas the second ones do.

Alright, this means we need to get a number that can be represented in two different ways but its value be the same without using e, and make sure both variables have the same lenght, as well param1 not starting with a 0.

There are many options! Here some I got to work:

    param1 = .10 and param2 = 0.1
    param1 = 1.0 and param2 = 001
    param1 = 10. and param2 = 010
    param1 = -0 anda param2 = 00

And like I said, after the competition was over people mentioned that the intend solution was actually to exploit the fact that is does not check for E meaning this also works:

    param1 = 1E2 and param2 = 100

By adding */?param1=1.0&param2=001* to the end of the address or any other solution the flag would appear.

Flag was **X-MAS{s0_php_m4ny_skillz-69acb43810ed4c42}**

Difficulty:  *Medium Easy*

First time working with php, so at first was a bit confused with the particularities of the language, but after some research this challenge was the perfect intro to simple web exploitation.

#### **Santa's consolation  (50/50 Points)**
>Author: littlewho

This was a very fun challenge that started of with a bit of promoting a website:

    Santa's been sending his regards; he would like to know who will still want to hack stuff after his CTF is over.

    Note: Bluuk is a multilingual bug bounty platform that will launch soon and we've prepared a challenge for you. Subscribe and stay tuned!
    Target: https://bluuk.io

    PS: The subscription form is not the target :P
    
Uppon entering the website you were greeted witha  button that said *Let´s Hack*.

You press it and it says *challenge has been loaded*.

I inspected the page and into to source to find a challenge.js file:

![Santa's Consolation:js](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Santa's%20Consolation/santa%C2%B4s_consolation_js.png)

So the goal is very much straightfoward:

- find the value of k1
- go back the steps of bobify function to find the input string
- put ii in win() function in the console

We are told that k1 does:

- atob(k) which basically means decode from base64
- split('').reverse().join(''), which means it reverses the result

So we start with:

    MkVUTThoak44TlROOGR6TThaak44TlROOGR6TThWRE14d0hPMnczTTF3M056d25OMnczTTF3M056d1hPNXdITzJ3M00xdzNOenduTjJ3M00xdzNOendYTndFRGY0WURmelVEZjNNRGYyWURmelVEZjNNRGYwRVRNOGhqTjhOVE44ZHpNOFpqTjhOVE44ZHpNOEZETXh3SE8ydzNNMXczTnp3bk4ydzNNMXczTnp3bk13RURmNFlEZnpVRGYzTURmMllEZnpVRGYzTURmeUlUTThoak44TlROOGR6TThaak44TlROOGR6TThCVE14d0hPMnczTTF3M056d25OMnczTTF3M056dzNOeEVEZjRZRGZ6VURmM01EZjJZRGZ6VURmM01EZjFBVE04aGpOOE5UTjhkek04WmpOOE5UTjhkek04bFRPOGhqTjhOVE44ZHpNOFpqTjhOVE44ZHpNOGRUTzhoak44TlROOGR6TThaak44TlROOGR6TThSVE14d0hPMnczTTF3M056d25OMnczTTF3M056d1hPNXdITzJ3M00xdzNOenduTjJ3M00xdzNOenduTXlFRGY0WURmelVEZjNNRGYyWURmelVEZjNNRGYzRVRNOGhqTjhOVE44ZHpNOFpqTjhOVE44ZHpNOGhETjhoak44TlROOGR6TThaak44TlROOGR6TThGak14d0hPMnczTTF3M056d25OMnczTTF3M056d25NeUVEZjRZRGZ6VURmM01EZjJZRGZ6VURmM01EZjFFVE04aGpOOE5UTjhkek04WmpOOE5UTjhkek04RkRNeHdITzJ3M00xdzNOenduTjJ3M00xdzNOendITndFRGY0WURmelVEZjNNRGYyWURmelVEZjNNRGYxRVRNOGhqTjhOVE44ZHpNOFpqTjhOVE44ZHpNOFZETXh3SE8ydzNNMXczTnp3bk4ydzNNMXczTnp3WE94RURmNFlEZnpVRGYzTURmMllEZnpVRGYzTURmeUlUTThoak44TlROOGR6TThaak44TlROOGR6TThkVE84aGpOOE5UTjhkek04WmpOOE5UTjhkek04WlRNeHdITzJ3M00xdzNOenduTjJ3M00xdzNOendITXhFRGY0WURmelVEZjNNRGYyWURmelVEZjNNRGYza0RmNFlEZnpVRGYzTURmMllEZnpVRGYzTURmMUVUTTAwMDBERVRDQURFUg==

Then we use cyberchef to decode from base64 to:

    2ETM8hjN8NTN8dzM8ZjN8NTN8dzM8VDMxwHO2w3M1w3NzwnN2w3M1w3NzwXO5wHO2w3M1w3NzwnN2w3M1w3NzwXNwEDf4YDfzUDf3MDf2YDfzUDf3MDf0ETM8hjN8NTN8dzM8ZjN8NTN8dzM8FDMxwHO2w3M1w3NzwnN2w3M1w3NzwnMwEDf4YDfzUDf3MDf2YDfzUDf3MDfyITM8hjN8NTN8dzM8ZjN8NTN8dzM8BTMxwHO2w3M1w3NzwnN2w3M1w3Nzw3NxEDf4YDfzUDf3MDf2YDfzUDf3MDf1ATM8hjN8NTN8dzM8ZjN8NTN8dzM8lTO8hjN8NTN8dzM8ZjN8NTN8dzM8dTO8hjN8NTN8dzM8ZjN8NTN8dzM8RTMxwHO2w3M1w3NzwnN2w3M1w3NzwXO5wHO2w3M1w3NzwnN2w3M1w3NzwnMyEDf4YDfzUDf3MDf2YDfzUDf3MDf3ETM8hjN8NTN8dzM8ZjN8NTN8dzM8hDN8hjN8NTN8dzM8ZjN8NTN8dzM8FjMxwHO2w3M1w3NzwnN2w3M1w3NzwnMyEDf4YDfzUDf3MDf2YDfzUDf3MDf1ETM8hjN8NTN8dzM8ZjN8NTN8dzM8FDMxwHO2w3M1w3NzwnN2w3M1w3NzwHNwEDf4YDfzUDf3MDf2YDfzUDf3MDf1ETM8hjN8NTN8dzM8ZjN8NTN8dzM8VDMxwHO2w3M1w3NzwnN2w3M1w3NzwXOxEDf4YDfzUDf3MDf2YDfzUDf3MDfyITM8hjN8NTN8dzM8ZjN8NTN8dzM8dTO8hjN8NTN8dzM8ZjN8NTN8dzM8ZTMxwHO2w3M1w3NzwnN2w3M1w3NzwHMxEDf4YDfzUDf3MDf2YDfzUDf3MDf3kDf4YDfzUDf3MDf2YDfzUDf3MDf1ETM0000DETCADER
    
And we reverse it:

    REDACTED0000MTE1fDM3fDUzfDY2fDM3fDUzfDY4fDk3fDM3fDUzfDY2fDM3fDUzfDY4fDExMHwzN3w1M3w2NnwzN3w1M3w2OHwxMTZ8Mzd8NTN8NjZ8Mzd8NTN8Njh8OTd8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTIyfDM3fDUzfDY2fDM3fDUzfDY4fDExOXwzN3w1M3w2NnwzN3w1M3w2OHwxMDV8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE1fDM3fDUzfDY2fDM3fDUzfDY4fDEwNHwzN3w1M3w2NnwzN3w1M3w2OHwxMDF8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE1fDM3fDUzfDY2fDM3fDUzfDY4fDEyMnwzN3w1M3w2NnwzN3w1M3w2OHwxMjF8Mzd8NTN8NjZ8Mzd8NTN8Njh8NDh8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE3fDM3fDUzfDY2fDM3fDUzfDY4fDEyMnwzN3w1M3w2NnwzN3w1M3w2OHw5OXwzN3w1M3w2NnwzN3w1M3w2OHwxMTR8Mzd8NTN8NjZ8Mzd8NTN8Njh8OTd8Mzd8NTN8NjZ8Mzd8NTN8Njh8OTl8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTA1fDM3fDUzfDY2fDM3fDUzfDY4fDExN3wzN3w1M3w2NnwzN3w1M3w2OHwxMTB8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTIyfDM3fDUzfDY2fDM3fDUzfDY4fDEwMnwzN3w1M3w2NnwzN3w1M3w2OHwxMDF8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE0fDM3fDUzfDY2fDM3fDUzfDY4fDEwNXwzN3w1M3w2NnwzN3w1M3w2OHw5OXwzN3w1M3w2NnwzN3w1M3w2OHwxMDV8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE2
    
Now we have the value that needs to be at the end of bobify, lets start rewinding the bobify function.

We have the btoa function which is encoding to base64, and inside we have the sum of s2 (which comes from our input) and the following string:

    D@\xc0\t1\x03\xd3M4
    
If we go back to the obtained k1 string we see that if we decode the first part *REDACTED0000* we obtain:

    D@À	1.ÓM4
    
Which means that the rest is our string s2:

    MTE1fDM3fDUzfDY2fDM3fDUzfDY4fDk3fDM3fDUzfDY2fDM3fDUzfDY4fDExMHwzN3w1M3w2NnwzN3w1M3w2OHwxMTZ8Mzd8NTN8NjZ8Mzd8NTN8Njh8OTd8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTIyfDM3fDUzfDY2fDM3fDUzfDY4fDExOXwzN3w1M3w2NnwzN3w1M3w2OHwxMDV8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE1fDM3fDUzfDY2fDM3fDUzfDY4fDEwNHwzN3w1M3w2NnwzN3w1M3w2OHwxMDF8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE1fDM3fDUzfDY2fDM3fDUzfDY4fDEyMnwzN3w1M3w2NnwzN3w1M3w2OHwxMjF8Mzd8NTN8NjZ8Mzd8NTN8Njh8NDh8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE3fDM3fDUzfDY2fDM3fDUzfDY4fDEyMnwzN3w1M3w2NnwzN3w1M3w2OHw5OXwzN3w1M3w2NnwzN3w1M3w2OHwxMTR8Mzd8NTN8NjZ8Mzd8NTN8Njh8OTd8Mzd8NTN8NjZ8Mzd8NTN8Njh8OTl8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTA1fDM3fDUzfDY2fDM3fDUzfDY4fDExN3wzN3w1M3w2NnwzN3w1M3w2OHwxMTB8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTIyfDM3fDUzfDY2fDM3fDUzfDY4fDEwMnwzN3w1M3w2NnwzN3w1M3w2OHwxMDF8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE0fDM3fDUzfDY2fDM3fDUzfDY4fDEwNXwzN3w1M3w2NnwzN3w1M3w2OHw5OXwzN3w1M3w2NnwzN3w1M3w2OHwxMDV8Mzd8NTN8NjZ8Mzd8NTN8Njh8MTE2
    
That we know is encoded, so we run from base64 once again and obtain the following:

    115|37|53|66|37|53|68|97|37|53|66|37|53|68|110|37|53|66|37|53|68|116|37|53|66|37|53|68|97|37|53|66|37|53|68|122|37|53|66|37|53|68|119|37|53|66|37|53|68|105|37|53|66|37|53|68|115|37|53|66|37|53|68|104|37|53|66|37|53|68|101|37|53|66|37|53|68|115|37|53|66|37|53|68|122|37|53|66|37|53|68|121|37|53|66|37|53|68|48|37|53|66|37|53|68|117|37|53|66|37|53|68|122|37|53|66|37|53|68|99|37|53|66|37|53|68|114|37|53|66|37|53|68|97|37|53|66|37|53|68|99|37|53|66|37|53|68|105|37|53|66|37|53|68|117|37|53|66|37|53|68|110|37|53|66|37|53|68|122|37|53|66|37|53|68|102|37|53|66|37|53|68|101|37|53|66|37|53|68|114|37|53|66|37|53|68|105|37|53|66|37|53|68|99|37|53|66|37|53|68|105|37|53|66|37|53|68|116
    
Now, we look at the line that describes how s2 is obtained:

    const s2=encodeURI(s1).split('').map(c=>c.charCodeAt(0)).join('|');

So we first need to remove the | and replace with a space, then decode from charcode the numbers, and then decode from URL:

Using split('|') and join (' '):

    115 37 53 66 37 53 68 97 37 53 66 37 53 68 110 37 53 66 37 53 68 116 37 53 66 37 53 68 97 37 53 66 37 53 68 122 37 53 66 37 53 68 119 37 53 66 37 53 68 105 37 53 66 37 53 68 115 37 53 66 37 53 68 104 37 53 66 37 53 68 101 37 53 66 37 53 68 115 37 53 66 37 53 68 122 37 53 66 37 53 68 121 37 53 66 37 53 68 48 37 53 66 37 53 68 117 37 53 66 37 53 68 122 37 53 66 37 53 68 99 37 53 66 37 53 68 114 37 53 66 37 53 68 97 37 53 66 37 53 68 99 37 53 66 37 53 68 105 37 53 66 37 53 68 117 37 53 66 37 53 68 110 37 53 66 37 53 68 122 37 53 66 37 53 68 102 37 53 66 37 53 68 101 37 53 66 37 53 68 114 37 53 66 37 53 68 105 37 53 66 37 53 68 99 37 53 66 37 53 68 105 37 53 66 37 53 68 116
    
Then From charcode with base 10:

    s%5B%5Da%5B%5Dn%5B%5Dt%5B%5Da%5B%5Dz%5B%5Dw%5B%5Di%5B%5Ds%5B%5Dh%5B%5De%5B%5Ds%5B%5Dz%5B%5Dy%5B%5D0%5B%5Du%5B%5Dz%5B%5Dc%5B%5Dr%5B%5Da%5B%5Dc%5B%5Di%5B%5Du%5B%5Dn%5B%5Dz%5B%5Df%5B%5De%5B%5Dr%5B%5Di%5B%5Dc%5B%5Di%5B%5Dt
    
Then decode from url:

    s[]a[]n[]t[]a[]z[]w[]i[]s[]h[]e[]s[]z[]y[]0[]u[]z[]c[]r[]a[]c[]i[]u[]n[]z[]f[]e[]r[]i[]c[]i[]t

And now we continue the process to deconstruct s1 that will give us string s that is our input:

    const s1=s.replace(/4/g,'a').replace(/3/g,'e').replace(/1/g,'i').replace(/7/g,'t').replace(/_/g,'z').split('').join('[]');
    
We first do split('[]') and join('')

    santazwisheszy0uzcraciunzfericit
    
And now we replace a with 4, e with 3, i with 1, t with 7 and z with _

    s4n74_w1sh3s_y0u_cr4c1un_f3r1c17

And then we could asssume this was the falg since in the code we have
    
     return check(x)?"X-MAS{"+x+"}"
     
But for good measure if we run in console win("s4n74_w1sh3s_y0u_cr4c1un_f3r1c17") we get

    X-MAS{s4n74_w1sh3s_y0u_cr4c1un_f3r1c17}
    

Flag was **X-MAS{s4n74_w1sh3s_y0u_cr4c1un_f3r1c17}**

Difficulty:  *Easy*

The great thing about this challenge was to learn to identify different types of enconding, specially in the url decode part where if you did from charcode with base 16( the normal one) you would not obtain a valid url encryption so you had to look for different bases until it looked like the correct one.

That finishes my write ups for this competition, I also colaborated for the solutions of *Many Paths* and *Santa's ELF holomorphing machine*, but they were mainly developed by my colleague.








 


























