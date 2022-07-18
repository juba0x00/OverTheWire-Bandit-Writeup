# Bandit

## Bandit-OverTheWire

<details>

<summary>Bandit 0 (Click Me)</summary>

*   Connecting using SSH

    * `**ssh bandit0@bandit.labs.overthewire.org -p 2220**`
    * password: bandit0

    ![Untitled](<Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled.png>)

***

</details>

<details>

<summary>Bandit 0 → Bandit 1 (Click Me)</summary>

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

*   password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 1.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 1 → Bandit 2 (Click Me)</summary>

The password for the next level is stored in a file called - located in the home directory

* there is many commands will not work like:
  *   `cat -`

      <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 2.png" alt="Untitled" data-size="original">
  *   `cat -- -`

      <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 3.png" alt="Untitled" data-size="original">
* we will use `--` to **signify the end of command options, so we can show “-” file content**
* or we can use `<` to tell `cat` get the input from `-` ( STDIN)
* password: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 4.png" alt="Untitled" data-size="original">

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 5.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 2 → Bandit 3 (Click Me)</summary>

The password for the next level is stored in a file called **spaces in this filename** located in the home directory

* password: UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
*   we will use double quotes to cat a file that contains spaces in it’s name

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 6.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 3 → Bandit 4 (Click Me)</summary>

The password for the next level is stored in a hidden file in the **inhere** directory.

* we will use ls with -AR options
  * \-A Almost all don’t list . and ..
  * \-R recursive
* then we cat the file using `**cat inhere/.hidden**`
* password: pIwrPrtPN36QITSp3EQaw936yaFoFgAB

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 7.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 4 → Bandit 5 (Click Me)</summary>

The password for the next level is stored in the only human-readable file in the **inhere**  directory. Tip: if your terminal is messed up, try the “reset” command.

1. first navigate to `inhere` directory
2. list the files with `ls` command
3. we can use for loop instead of checking each file individually
   1. `for i in {0..9}; do file -- "-file0$i" ; done`
4. we can see that “-file07” is ASCII file, we can view it’s content using `cat -- -file07` command
   1. `--` to say that this is the end of options

* password: koReBOKuIDDepwhWk7jZC0RTdopnAYKh

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 8.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 5 → Bandit 6 (Click Me)</summary>

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

* human-readable
* 1033 bytes in size
* not executable

1. first, navigate to `inhere` directory
2. list the files
3. find a file with size of 1003 bytes and not executable
   1. `**find . -type f -size 1033c ! -executable**`

* password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 9.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 6 → Bandit 7 (Click Me)</summary>

The password for the next level is stored **somewhere on the server** and has all of the following properties:

* owned by user bandit7
* owned by group bandit6
* 33 bytes in size

<!---->

* `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null`
* password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 10.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 7 → Bandit 8 (Click Me)</summary>

The password for the next level is stored in the file **data.txt** next to the word **millionth**

* `**cat data.txt | grep millionth**` easy command
* password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 11.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 8 → Bandit 9 (Click Me)</summary>

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

* `**uniq**` command, ONLY, identifies the duplicate lines, if they are adjacent to each other. So you know why do we need a command to `sort` lines first.
* `cat data.txt | sort | uniq -uc`
  * \-u → remove duplicate lines
  * \-c → count
* password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 12.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 9 → Bandit 10 (Click Me)</summary>

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ character

* we can see that “data.txt” isn’t an ASCII file so we can use `strings` command to show any printable character
* `**strings data.txt | grep =**`
* password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 13.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 10 → Bandit 11 (Click Me)</summary>

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

* `**cat data.txt | base64 -d**`
* password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 14.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 11 → Bandit 12 (Click Me)</summary>

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

* first view the content of data.txt

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 15.png" alt="Untitled" data-size="original">

* we can use [CyberChef](https://gchq.github.io/CyberChef/) to rotate the letters
* search for rotate in the top left bar then drag ROT13 and drop it in the Recipe section then paste the letters we found in the file data.txt

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 16.png" alt="Untitled" data-size="original">

* password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
* login to bandit 12 using the password

***

</details>

<details>

<summary>Bandit 12→ Bandit 13 (Click Me)</summary>

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

* first, we will create a directory inside /tmp
*   cp data.txt to our directory

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 17.png" alt="Untitled" data-size="original">

    ***
* alright, let's search for any program to deal with hexdump
*   we can use `**apropos hexdump**`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 18.png" alt="Untitled" data-size="original">
* great, it seems `xxd` will help us here
*   lets learn more about it using `--help` option

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 19.png" alt="Untitled" data-size="original">

    * we found `-r` option allow us to reverse
    * `xxd -r data.txt > data` reverse the hexdump and redirect the output to “data” file

    ***
*   let’s check the file type using `file data` command, it’s gzip compressed data, so we will rename the file to “data.gz”

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 20.png" alt="Untitled" data-size="original">

    * unzip “data.gz” using `gzip --decompress data.gz`

    ***
*   there are three steps we will do after any decompress

    1. Chck the file format using `**file <file name>**`
    2. rename the file with it’s format extention (gzip → .gz, bzip2 → bz2, POSIX → tar.gz)
    3. decompress the file (`gzip -d` or `tar -xvf` or `bzip2 -d`)

    ***
*   gzip decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 21.png" alt="Untitled" data-size="original">

    ***
* bzip2 decompress
*   after checking the file type again we will see it is bzip2 file, so let’s rename the file to “data.bz2”

    * `**bandit12@bandit:/tmp/juba$ mv compressed.bz compressed.bz2**`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 22.png" alt="Untitled" data-size="original">

    ***
*   gzip decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 23.png" alt="Untitled" data-size="original">

    ***
*   Tar decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 24.png" alt="Untitled" data-size="original">

    ***
*   POSIX tar decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 25.png" alt="Untitled" data-size="original">

    ***
*   bzip2 decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 26.png" alt="Untitled" data-size="original">

    ***
*   tar decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 27.png" alt="Untitled" data-size="original">

    ***
*   gzip decompress

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 28.png" alt="Untitled" data-size="original">

    ***
* Password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

***

</details>

<details>

<summary>Bandit 13 → Bandit 14 (Click Me)</summary>

* The password for the next level is stored in **/etc/bandit\_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on
* We don’t need the Bandit14 password, we have his ssh private key, so we can use it to login
* `**ssh -i <ssh key> <username>@<host>**`

```
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----
```

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 29.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 14 → Bandit 15 (Click Me)</summary>

* The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.
*   we know from the previous task that bandit14 password is stored in /etc/bandit\_pass/bandit14

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 30.png" alt="Untitled" data-size="original">
* Bandit14 password: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
*   as we can see if we get the content of the website we can’t see the password unless we submit our password

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 31.png" alt="Untitled" data-size="original">
*   we can use netcat to submit our password

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 32.png" alt="Untitled" data-size="original">

Password: BfMYroe26WYalil77FoDi9qh59eK5xNr

***

</details>

<details>

<summary>Bandit 15 → Bandit 16 (Click Me)</summary>

* The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.
* **Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign\_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**
*   Let’s check the manual page for netcat using `man` command

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 33.png" alt="Untitled" data-size="original">

    * can’t find any helpful option
*   let’s try ncat

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 34.png" alt="Untitled" data-size="original">

    * Great point, now we can use ncat
*   `**ncat --ssl 127.0.0.1 30001**`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 35.png" alt="Untitled" data-size="original">
* Password: cluFn7wTiGryunymYOu4RcffSxQluehd

***

</details>

<details>

<summary>Bandit 16 → Bandit 17 (Click Me)</summary>

* The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**
* First, find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
*   Start nmap scan using -p to specify the ports

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 36.png" alt="Untitled" data-size="original">
*   we can check them manually

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 37.png" alt="Untitled" data-size="original">

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 38.png" alt="Untitled" data-size="original">

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 39.png" alt="Untitled" data-size="original">

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 40.png" alt="Untitled" data-size="original">

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 41.png" alt="Untitled" data-size="original">
*   as we can see there are two ports that use SSL (31518, 31790), Let’s check them

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 42.png" alt="Untitled" data-size="original">

    * it seems this is the wrong one
*   port 31790

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 43.png" alt="Untitled" data-size="original">

```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

***

</details>

<details>

<summary>Bandit 17 → Bandit 18 (Click Me)</summary>

* There are 2 files in the home directory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**
* **NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19**
* we can use many tools to compare two files like:
  * `vimdiff`
  * `comm`
  * `diff`
*   I’m going to use `vimdiff`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 44.png" alt="Untitled" data-size="original">

    * we can see line number 42 is different
    * to close vimdiff you type`:qa`
*   let’s connect to bandit 18 using the password we found

    > Password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
* as we can see “Byebye !” indicates that’s we have succeeded

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 45.png" alt="Untitled" data-size="original">

***

</details>

<details>

<summary>Bandit 18 → Bandit 19 (Click Me)</summary>

* The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.
* Let’s search for any option helps us to connect using another shell

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 46.png" alt="Untitled" data-size="original">

* We can see `-t` option could help us
* Let’s try to connect using `**-t <shell>**`

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 47.png" alt="Untitled" data-size="original">

* the `-t sh` is to change the default shell to the shell because the .bashrc has been changed to exit after starting bash

Password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

***

</details>

<details>

<summary>Bandit 19 → Bandit 20 (Click Me)</summary>

* To gain access to the next level, you should use the setuid binary in the home directory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit\_pass) after you have used the setuid binary.
*   if we check `**whoami` we can see bandit20 like below:\*\*

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 48.png" alt="Untitled" data-size="original">
*   Let’s get bandit20 password by viewing the /etc/bandit\_pass/bandit20 file content

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 49.png" alt="Untitled" data-size="original">

    > Password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j

***

</details>

<details>

<summary>Bandit 20 → Bandit 21 (Click Me)</summary>

* There is a setuid binary in the home directory that does the following: it makes a connection to localhost on the port you specify as a command line argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password to the next level (bandit21).
*   **NOTE:** Try connecting to your own network daemon to see if it works as you think

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 50.png" alt="Untitled" data-size="original">
* great, we can start listening port with `nc` (netcat)
*   Let’s use suconnect to connect to our listening port, then enter bandit20 password

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 51.png" alt="Untitled" data-size="original">

Password: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr

***

</details>

<details>

<summary>Bandit 21 → Bandit 22 (Click Me)</summary>

* A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
*   Let’s check cron.d directory

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 52.png" alt="Untitled" data-size="original">
*   we can see that bandit22 cronjob in /usr/bin/cronjob\_bandit22.sh, so let’s check it

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 53.png" alt="Untitled" data-size="original">
*   as we can see this script will change the mode to 644 for a file called “t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv” in /tmp, then will cat bandit22 password and redirect it to this file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 54.png" alt="Untitled" data-size="original">
*   It’s very easy to access the password, just read the file “/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv”

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 55.png" alt="Untitled" data-size="original">

Password: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI

***

</details>

<details>

<summary>Bandit 22 → Bandit 23 (Click Me)</summary>

* A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
* **NOTE:** Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
*   we can remember cron.d directory from the previous level

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 52.png" alt="Untitled" data-size="original">
*   let’s check the cronjob\_bandit23 file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 56.png" alt="Untitled" data-size="original">
*   view /usr/bin/cronjob\_bandit23.sh

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 57.png" alt="Untitled" data-size="original">

    * line 1: shebang
    * line4: save the user name in a variable called myname
    * line5: hash the text “I am user username“ using md5sum hash algorithm then split the output and save the output in a variable called mytarget
      *   to demonstrate this we will try it by ourself

          <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 58.png" alt="Untitled" data-size="original">
      *   if we don’t cut the output we will see this output:

          <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 59.png" alt="Untitled" data-size="original">
    * line 7: print “Copying password file /etc/bandit\_pass/$myname to /tmp/$mytarget”
    *   line 9: cat his password and redirect it to /tmp/$mytarget

        ***
* we know that bandit23 is running this cronjob, so it’s obvious that myname variable is “bandit23”, Let’s assign this value using `**myname=bandit23**`
*   let’s continue the script by assigning mytarget variable using `mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 60.png" alt="Untitled" data-size="original">
*   now we know the file name, let’s get the password

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 61.png" alt="Untitled" data-size="original">

Password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n

***

</details>

<details>

<summary>Bandit 23 → Bandit 24 (Click Me)</summary>

* A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
* **NOTE:** This level requires you to create your own first shell script. This is a very big step and you should be proud of yourself when you beat this level!
* **NOTE 2:** Keep in mind that your shell script is **removed** **once executed**, so you may want to keep a copy around…
*   Let’s navigate to /etc/cron.d to see all cron jobs

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 62.png" alt="Untitled" data-size="original">

    * well, let’s show cronjob\_bandit24 content

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 63.png" alt="Untitled" data-size="original">
*   let’s check /usr/bin/cronjob\_bandit24.sh

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 64.png" alt="Untitled" data-size="original">

    * the main functionality of this script is executing all the files in /var/spool/$myname and deleting them, in our case $myname is bandit24 he executes this script
* let’s write our script and save it in /tmp/our\_dir because the script will remove it automatically
* we can create our script by typing `touch <script name>.sh`
*   all we need is bandit24 password, so we can type this small script

    ```bash
    #!/bin/bash 
    cat /etc/bandit_pass/bandit24 > /tmp/juba/done  
    ```
* before coping this script to /var/spool/bandit24 we need to give it executable permissions by typing `chmod a+x get_pass.sh`
* if bandit24 executes this script he can’t write on /tmp/juba/done so we should give him write permissions `touch done ; chmod a+w done`
* coping the file `cp get_pass.sh /var/spool/bandit24/`
*   great, we have got the password

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 65.png" alt="Untitled" data-size="original">

Password: UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ

***

</details>

<details>

<summary>Bandit 24 → Bandit 25 (Click Me)</summary>

* A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
* First, we should generate all the possible combinations of 4 digits, we can generate it using this simple script `for i in {0000..9999}; do echo $i >> wordlist.txt ; done`
* great, now we have all the possible combinations let’s try to get the password by connecting to port 30002 using netcat
*   if we connected without any input we will see the following

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 66.png" alt="Untitled" data-size="original">
* sorry, it seems we need bandit24 password too, let’s get it using `cat /etc/bandit_pass/bandit24` and regenerate the list using `for i in {0000..9999}; do echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $i" >> list ; done`
*   if we tried to brute force the PIN code we will see this

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 67.png" alt="Untitled" data-size="original">
*   so, let's remove these lines by adding `**| grep -v 'Try again'**`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 68.png" alt="Untitled" data-size="original">

Password: uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

***

</details>

<details>

<summary>Bandit 25 → Bandit 26 (Click Me)</summary>

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not **/bin/bash**, but something else. Find out what it is, how it works, and how to break out of it.

*   we found bandit26 ssh key in bandit 25 home directory

    ```bash
    bandit25@bandit:~$ ls 
    bandit26.sshkey
    ```
*   we can check the shell for user bandit26 by viewing /etc/passwd file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 69.png" alt="Untitled" data-size="original">
* as we can see bandit26 uses /usr/bin/showtext shell
*   let’s try to login using this ssh key

    ```bash
    bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost 
    Could not create directory '/home/bandit25/.ssh'.
    The authenticity of host 'localhost (127.0.0.1)' can't be established.
    ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
    Are you sure you want to continue connecting (yes/no)? yes
    Failed to add the host to the list of known hosts (/home/bandit25/.ssh/known_hosts).
    This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

    Linux bandit.otw.local 5.4.8 x86_64 GNU/Linux

          ,----..            ,----,          .---.
         /   /   \         ,/   .`|         /. ./|
        /   .     :      ,`   .'  :     .--'.  ' ;
       .   /   ;.  \   ;    ;     /    /__./ \ : |
      .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
      ;   |  ; \ ; | |    :     | /___/ \ |    ' '
      |   :  | ; | ' ;    |.';  ; ;   \  \;      :
      .   |  ' ' ' : `----'  |  |  \   ;  `      |
      '   ;  \; /  |     '   :  ;   .   \    .\  ;
       \   \  ',  /      |   |  '    \   \   ' \ |
        ;   :    /       '   :  |     :   '  |--"
         \   \ .'        ;   |.'       \   \ ;
      www. `---` ver     '---' he       '---" ire.org

    Welcome to OverTheWire!

    If you find any problems, please report them to Steven or morla on
    irc.overthewire.org.

    --[ Playing the games ]--

      This machine might hold several wargames.
      If you are playing "somegame", then:

        * USERNAMES are somegame0, somegame1, ...
        * Most LEVELS are stored in /somegame/.
        * PASSWORDS for each level are stored in /etc/somegame_pass/.

      Write-access to homedirectories is disabled. It is advised to create a
      working directory with a hard-to-guess name in /tmp/.  You can use the
      command "mktemp -d" in order to generate a random and hard to guess
      directory in /tmp/.  Read-access to both /tmp/ and /proc/ is disabled
      so that users can not snoop on eachother. Files and directories with
      easily guessable or short names will be periodically deleted!

      Please play nice:

        * don't leave orphan processes running
        * don't leave exploit-files laying around
        * don't annoy other players
        * don't post passwords or spoilers
        * again, DONT POST SPOILERS!
          This includes writeups of your solution on your blog or website!

    --[ Tips ]--

      This machine has a 64bit processor and many security-features enabled
      by default, although ASLR has been switched off.  The following
      compiler flags might be interesting:

        -m32                    compile for 32bit
        -fno-stack-protector    disable ProPolice
        -Wl,-z,norelro          disable relro

      In addition, the execstack tool can be used to flag the stack as
      executable on ELF binaries.

      Finally, network-access is limited for most levels by a local
      firewall.

    --[ Tools ]--

     For your convenience we have installed a few usefull tools which you can find
     in the following locations:

        * gef (https://github.com/hugsy/gef) in /usr/local/gef/
        * pwndbg (https://github.com/pwndbg/pwndbg) in /usr/local/pwndbg/
        * peda (https://github.com/longld/peda.git) in /usr/local/peda/
        * gdbinit (https://github.com/gdbinit/Gdbinit) in /usr/local/gdbinit/
        * pwntools (https://github.com/Gallopsled/pwntools)
        * radare2 (http://www.radare.org/)
        * checksec.sh (http://www.trapkit.de/tools/checksec.html) in /usr/local/bin/checksec.sh

    --[ More Information ]--

      For more information regarding individual wargames, visit
      http://www.overthewire.org/wargames/

      For support, questions or comments, contact us through IRC on
      irc.overthewire.org #wargames.

      Enjoy your stay!

      _                     _ _ _   ___   __  
     | |                   | (_) | |__ \ / /  
     | |__   __ _ _ __   __| |_| |_   ) / /_  
     | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
     | |_) | (_| | | | | (_| | | |_ / /| (_) |
     |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/ 
    Connection to localhost closed.
    ```
*   it seems showtext shell is printing this banner and exit to let’s try to use another shell, so let’s check /usr/bin/showtext

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 70.png" alt="Untitled" data-size="original">
*   Great, it’s not a binary file, let’s check if we can read it

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 71.png" alt="Untitled" data-size="original">

    * this script makes our $TERM env equal to Linux and shows the content of /home/bandit26/text.txt using more
*   we can open an editor while using more by pressing `v` (vi by default), just make the terminal as small as possible you can, and you will find more tools

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 72.png" alt="Untitled" data-size="original">
*   great, press v

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 73.png" alt="Untitled" data-size="original">
* now we are using vim, so let’s get the password using vim command mode
*   `**:e /etc/bandit_pass/bandit26**`

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 74.png" alt="Untitled" data-size="original">

Password: 5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z

* Great, now we should change bandit 26 shell, we can do it using vim
  * `**:set shell=/bin/bash**`
* we can start bandit26 shell now
  * `**:shell**`

***

</details>

<details>

<summary>Bandit 26 → Bandit 27 (Click Me)</summary>

Good job getting a shell! Now hurry and grab the password for bandit27!

*   list files

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 75.png" alt="Untitled" data-size="original">
*   we have ‘bandit27-do’ binary file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 76.png" alt="Untitled" data-size="original">
*   let’s check our privileges

    ```bash
    bandit26@bandit:~$ ls -l bandit27-do 
    -rwsr-x--- 1 bandit27 bandit26 7296 May  7  2020 bandit27-do
    ```
*   It’s a SUID file, let’s try to run it

    ```bash
    bandit26@bandit:~$ ./bandit27-do whoami
    bandit27
    ```
*   great, we can view bandit 27 pass using this file

    ```bash
    bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
    3ba3118a22e93127a4ed485be72ef5ea
    ```

Password: 3ba3118a22e93127a4ed485be72ef5ea

***

</details>

<details>

<summary>Bandit 27 → Bandit 28 (Click Me)</summary>

There is a git repository at `ssh://bandit27-git@localhost/home/bandit27-git/repo`. The password for the user `bandit27-git` is the same as for the user `bandit27`.

*   we can’t clone the repository in our home directory, so we should navigate to /tmp and create a directory we can write in

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 77.png" alt="Untitled" data-size="original">
*   now we can clone the repository with bandit27 password

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 78.png" alt="Untitled" data-size="original">
*   the password is easy to get, just navigate to the repository and read ‘README’ file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 79.png" alt="Untitled" data-size="original">

Password: 0ef186ac70e04ea33b4c1853d2526fa2

***

</details>

<details>

<summary>Bandit 28 → Bandit 29 (Click Me)</summary>

There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

* The same first steps for bandit27
  * navigate to /tmp
  * create a directory
  *   clone the repository using bandit28 password

      <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 80.png" alt="Untitled" data-size="original">
*   README.md content

    ```bash
    bandit28@bandit:/tmp/bandit28_juba/repo$ cat README.md 
    # Bandit Notes
    Some notes for level29 of bandit.

    ## credentials

    - username: bandit29
    - password: xxxxxxxxxx
    ```
*   nothing interesting, but we can see git commits history

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 81.png" alt="Untitled" data-size="original">
*   the third commit have an interesting comment ‘fix info leak’, so let’s check it

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 82.png" alt="Untitled" data-size="original">

    * Gotcha! 😀

Password: bbc96594b4e001778eee9975372716b2

***

</details>

<details>

<summary>Bandit 29 → Bandit 30 (Click Me)</summary>

There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

* the same steps as the previous two levels.
*   README.md content

    ```bash
    bandit29@bandit:/tmp/bandit29_juba/repo$ cat README.md 
    # Bandit Notes
    Some notes for bandit30 of bandit.

    ## credentials

    - username: bandit30
    - password: <no passwords in production!>
    ```
*   checking commits

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 83.png" alt="Untitled" data-size="original">
*   checking branches

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 84.png" alt="Untitled" data-size="original">
* great, there are other branches
*   switch the branch

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 85.png" alt="Untitled" data-size="original">

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 86.png" alt="Untitled" data-size="original">

Password: 5b90576bedb2cc04c86a9e924ce42faf

***

</details>

<details>

<summary>Bandit 30 → Bandit 31 (Click Me)</summary>

There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo`. The password for the user `bandit30-git` is the same as for the user `bandit30`.

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 87.png" alt="Untitled" data-size="original">

*   checking commits and branches

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 88.png" alt="Untitled" data-size="original">
*   after switching to master branch I did not find anything interesting, so let’s check the tags

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 89.png" alt="Untitled" data-size="original">

    > Password: 47e603bb428404d265f59c42920d81e5

***

</details>

<details>

<summary>Bandit 31 → Bandit 32 (Click Me)</summary>

There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

<img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 90.png" alt="Untitled" data-size="original">

*   create and add key.txt file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 91.png" alt="Untitled" data-size="original">
*   commit and push the file

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 92.png" alt="Untitled" data-size="original">

**Password: 56a9bf19c63d650ce78e6ec0354ee45e**

***

</details>

<details>

<summary>Bandit 32 → Bandit 33 (Click Me)</summary>

After all this `git` stuff it's time for another escape. Good luck!

*   login banner

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 93.png" alt="Untitled" data-size="original">

    * as we can see at the button it’s UPPERCASE SHELL
*   Let’s search for the next password the system

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 94.png" alt="Untitled" data-size="original">
*   we can’t use the basic commands, let’s try it with uppercase

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 95.png" alt="Untitled" data-size="original">
* I think that UPPERCASE shell makes our PATH env equal to ‘’ (null), so we can’t use any command
*   the following is a demonstration of this

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 96.png" alt="Untitled" data-size="original">
* we still can use BASH special variables like (\$$, $#, $\*, $!, $0, $1,.., etc.), if you don’t bash special variable [google it](https://www.google.com/search?q=bash+special+variables&)
* we can use `$0` to get the first argument I think that UPPERCASE runs using `bash UPPERCASE.sh`, so `$0` will refer to bash
*   demo:

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 97.png" alt="Untitled" data-size="original">
*   great, let’s to this

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 98.png" alt="Untitled" data-size="original">
*   Let’s search for any interesting information

    <img src="Bandit-OverTheWire 4aed9ce84c6a4f3da2fcf804b250aedf/Untitled 99.png" alt="Untitled" data-size="original">

Congratulations on solving the last level of this game! At this moment, there are no more levels to play in this game. However, we are constantly working on new levels and will most likely expand this game with more levels soon. Keep an eye out for an announcement on our usual communication channels! In the meantime, you could play some of our other wargames. If you have an idea for an awesome new level, please let us know!

**At this moment, level 34 does not exist yet.**

***

</details>

## Thank your for reading my write up

* [My TryHackMe Account](https://tryhackme.com/p/Juba0x430x55)
* [My Twitter Account](https://twitter.com/Juba0x00)
