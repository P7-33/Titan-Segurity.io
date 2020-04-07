---
title: 'Hashcat Tutorial for Beginners | hackshala.in'
date: 2020-01-07T05:04:00+01:00
draft: false
---

Introduction
------------

Hashcat is a well-known password cracker. It is designed to break even the most complex passwords. To do this, it enables the cracking of a specific password in multiple ways, combined with versatility and speed.

Password representations are primarily associated with hash keys, such as MD5, SHA, WHIRLPOOL, RipeMD, etc. They are also defined as a one-way function — this is a mathematical operation that is easy to perform, but very difficult to reverse engineer.

Hashcat turns readable data into a garbled state (this is a random string of fixed length size). Hashes do not allow someone to decrypt data with a specific key, as standard encryption protocols allow.

Hashcat uses precomputed dictionaries, rainbow tables, and even a brute-force approach to find an effective and efficient way crack passwords. This article provides an introductory tutorial for cracking passwords using the Hashcat software package.

How to Crack Hashes
-------------------

The simplest way to crack a hash is to try first to guess the password. Each attempt is hashed and then is compared to the actual hashed value to see if they are the same.

Dictionary and brute-force attacks are the most common ways of guessing passwords. These techniques make use of a file that contains words, phrases, common passwords, and other strings that are likely to be used as a viable password. ![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/040918_1822_HashcatTuto1.jpg)

It should be noted that there is no 100% way to prevent dictionary attacks or brute force attacks.

Other approaches that are used to crack passwords are as follows:

*   Lookup Tables: Hashes are pre-computed from a dictionary and then stored with their corresponding password into a lookup table structure.
*   Reverse Lookup Tables: This attack allows for a cyber attacker to apply a dictionary or brute-force attack to many hashes at the same time, without having to pre-compute a lookup table.
*   Rainbow Tables: Rainbow tables are a time-memory technique. They are similar to lookup tables, except that they sacrifice hash cracking speed to make the lookup tables smaller.
*   Hashing with Salt: With this technique, the hashes are randomized by appending or prepending a random string, called a “salt.” This is applied to the password before hashing.

Cracking Passwords with Hashcat
-------------------------------

Hashcat can be downloaded [here](https://hashcat.net/hashcat/). It can be used on [Kali Linux](https://www.kali.org/). It possesses the following features:

*   It is multi-threaded;
*   It is multi-hash and multi-OS based (Linux, Windows and OSX native binaries);
*   It is multi-Algorithm based (MD4, MD5, SHA1, DCC, NTLM, MySQL, etc.);
*   All attack-modes can be extended by specialized rules;
*   It is possible to resume or limit sessions automatically. They recognize recovered hashes from the outfile at startup;
*   It can load the salt list from the external file. This can be used as a brute-force attack variant;
*   The number of threads can be configured and executed based on the lowest priority;
*   It supports both hex-charset and hex-salt files;
*   The 90+ Algorithm can be implemented with performance and optimization in mind.

A small laboratory setup of how to crack a password is presented in the next section. A dictionary attack will be simulated for a set of MD5 hashes initially created and stored in a target file. The “rockyou” wordlist found in Kali Linux was used.

How to crack a password via a dictionary attack
-----------------------------------------------

### 1\. Create a dictionary with MBD5 hashes:

To begin this demonstration, we will create multiple hash entries containing several passwords. They will then be outputted to a file called “target\_hashes.” Each command should be executed in the terminal, as demonstrated in the screenshot below:

echo -n “Password” | md5sum | tr -d ” -” >> target\_hashes.txt  
echo -n “HELLO” | md5sum | tr -d ” -” >> target\_hashes.txt  
echo -n “MYSECRET” | md5sum | tr -d ” -” >> target\_hashes.txt  
echo -n “Test1234″ | md5sum | tr -d ” -” >> target\_hashes.txt  
echo -n “P455w0rd” | md5sum | tr -d ” -” >> target\_hashes.txt  
echo -n “GuessMe” | md5sum | tr -d ” -” >> target\_hashes.txt  
echo -n “S3CuReP455Word” | md5sum | tr -d ” -” >> target\_hashes.txt

The \-n option removes the new line added to the end of “Password.” This is important as we don’t want the new line characters to be hashed with our password. The part  
“tr –d ‘ -‘ “removes any characters that are a space or hyphen from the output.  

### 2\. Check password hashes:

To do this, we need to type the following command line in the terminal:

cat target\_hashes.txt.

This is also illustrated in the screenshot below:

root@kali:~/Desktop# cat target\_hashes.txt  
dc647eb65e6711e155375218212b3964  
eb61eead90e3b899c6bcbe27ac581660  
958152288f2d2303ae045cffc43a02cd  
2c9341ca4cf3d87b9e4eb905d6a3ec45  
75b71aa6842e450f12aca00fdf54c51d  
031cbcccd3ba6bd4d1556330995b8d08  
b5af0b804ff7238bce48adef1e0c213f

### 3\. Start Hashcat in Kali Linux:

Hashcat can be started on the Kali console with the following command line:

hashcat -h.

This is illustrated in the screenshot below:

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/040918_1822_HashcatTuto2.png)

Some of the most important hashcat options are \-m (the hashtype) and \-a (attack mode). In general, we need to use both options in most password cracking attempts when using Hashcat.

Hashcat also has specifically designed rules to use on a wordlist file. The character list can be customized to crack the password(s).

Finally, Hashcat provides numerous options for password hashes that can be cracked. This can be seen in the screenshot below:![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/040918_1822_HashcatTuto3.png)

### 4\. Choose the wordlist:

Kali Linux has numerous wordlists built right into it. To find them, use the following command line:

locate wordlists.

This is illustrated in the screenshot below:

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/040918_1822_HashcatTuto4.png)

The “rockyou” wordlist is now used, as illustrated below:  
root@kali:~/Desktop# locate rockyou.txt  
/usr/share/wordlists/rockyou.txt

### 5\. Cracking the hashes:

In the final step, we can now start cracking the hashes contained in the target\_hashes.txt file. We will use the following command line, as illustrated below:

root@kali:~/Desktop# hashcat -m 0 -a 0 -o cracked.txt target\_hashes.txt /usr/share/wordlists/rockyou.txt

*   \-m 0 designates the type of hash we are cracking (MD5);
*   \-a 0 designates a dictionary attack;
*   \-o cracked.txt is the output file for the cracked passwords;
*   target\_hashes.txt is our input file of hashes;
*   /usr/share/wordlists/rockyou.txt  
    is the absolute path to the wordlist file for this dictionary attack.

### 6\. Results:

Finally, we have cracked 5 out of 7 target hashes that were initially proposed. These can be seen below:

root@kali:~/Desktop# cat cracked.txtdc647eb65e6711e155375218212b3964:Password  
eb61eead90e3b899c6bcbe27ac581660:HELLO  
75b71aa6842e450f12aca00fdf54c51d:P455w0rd  
2c9341ca4cf3d87b9e4eb905d6a3ec45:Test1234  
958152288f2d2303ae045cffc43a02cd:MYSECRET

These passwords are weak, and it does not take much effort or time to crack them. It is important to note that the simpler the password is, the easier it will be to detect.

Thus, make your password into a long and complex one. Also, avoid using obvious personal information; never reuse passwords, and change them regularly.

Hackshala.in