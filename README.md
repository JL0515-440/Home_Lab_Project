# Home Lab Project
This Repository is being made by me (JL0515-440), because I wanted to do research regarding on how some Cybersecurity "Penetration testing" Tools work, and how to defend my own machine against them. By doing this I'm creating a personal network so that way I do not affect my own machine, and any other external device.

I took inspiration from a lot of videos to do this project, as well as, some AI (ChatGPT and Gemini) bots to research ideas, but the one that encouraged me to do this project was this one in Youtube: 

**CyberDojo**: https://www.youtube.com/watch?v=ZpFticDPEkw&list=PLtW3uHVuf_vgwHht2JTm_UUklczqz_PX7&index=76&t=523s

(Original Creator of the video I took inspiration from and many of the steps I have done in the project)

**I AM NOT RESPONSIBLE FROM ALL THE THINGS I HAVE SAID IN THIS REPOSITORY THIS IS A PROJECT FOR CYBERSECURITY TO TEST THE EFFICIENCY OF A HOME LAB. I DO NOT FOMENT ANY TYPE OF BEHAVIOR OR ANY TYPE MISSUSE OF ALL THE THINGS I HAVE BEEN REPORTING IN THIS REPOSITORY. ALL OF THIS DOCUMENTATION IT IS ONLY INTEND TO BE FOR EDUCATIONAL PURPOSES ONLY**

# Different Operating Systems and Virtual Machines
In this project I was using **Virtual Box** which is one of the most used VMs besides VMware. Here is the link of the website https://www.virtualbox.org/ I liked this VM because is free and it's easy to use if you don't know too much about Virtualization.

## Linux Operating Systems

In the Home Lab you can use whichever Operating System (OS) you prefer. In this Home Lab we are using **Ubuntu** and **Parrot OS (in this case the security version)**. Both are Linux Operating Systems which are used for different purposes. Ubuntu being as a one of the best options for general uses that an OS could have, as well as, being extremely light-weight, and Parrot OS - Security Version is an Operating System that has multiple tools from all the fields such as: Programming, Data Analysis, and Cybersecurity.

 These are the links for the Operating Systems that I'm using:

Ubuntu: https://ubuntu.com/download/desktop<br/>
Parrot OS: https://parrotsec.org/<br/>

Kali Linux (Although I didn't use it, in **CyberDojo**'s video he uses it to penetrate into Ubuntu's IP Address): https://www.kali.org/

# Setting Up the VMs

## Installing the OS in their respective VMs

Once we finished downloading everything we need to set up our OSs in their respective VMs. We need to select the right .iso file, so that way the VMs can create a connection and then start using them.

## Configuration of each OS, and the creation of the NAT Network

This is the configuration of each OS that I decided to use in order to make them run, and be able to work as much as possible. 

**Ubuntu Configuration**<br/>
![image](https://github.com/user-attachments/assets/ed29a510-d1df-4c25-921a-07906ad90b16)
<br/>
Storage: 25.00 GB<br/>

**Parrot OS Configuration**<br/>
![image](https://github.com/user-attachments/assets/ed29a510-d1df-4c25-921a-07906ad90b16)
<br/>
Storage: 25:00 HB<br/>

(Yes, it the same configuration for some reason when I tried to add or substract more from each VM it had some issues, that's why I tried to do the same configuration for all of them.)

Once we have all the OS already created and configurated we need to stablish a NAT Network that would allow us to work with both VMs together. 

# Stablishing the NAT Network

**THIS STEP IS HIGHLY IMPORTANT BECAUSE WITHOUT THE CREATION OF OUR OWN NAT NETWORK WE COULD AFFECT ANY OTHER EXTERNAL MACHINE AND THAT WOULD INVOLVE A MAJOR ISSUE ON OUR HOME LAB. AS WELL AS A POTENTIAL LEGAL RISK IF WE DO NOT CREATE THE NAT NETWORK**
(There are different types of methods to avoid this inconvenient, if you want to take a look I suggest to start a chat with any AI and it will tell you the best ways to avoid this inconvenient.)

We go to "Tools" all the way in the left top, and then we select the option called "Network". After that we go to "Nat Network" and then we create a new Nat Network you can call it whichever name you find more attractive to you.

![image](https://github.com/user-attachments/assets/5a02f1cd-6204-42f6-8b31-bbb6f061ebb2)<br/>

(I created one called "Home_Lab_Cybersecurity_Network" just for reference)


## Update & download of essential tools in our Operating Systems

After having the VMs already setted up we must check if the OS have their systems updated and with all the necessary tools for our activities. Using the following command: 
```bash
sudo apt update && sudo apt upgrade -y
``` 
On each terminal (in this case Parrot OS & Ubuntu) so that way we can update and upgrade our OSs. I'm going to use the next command to install the essential tools that we will use for our Home Lab.
```bash
sudo apt install -y build essential git wget
```
# Simulate an Attack, and responding to it.

Now we are going to simulate an attack using Nmap (An app that scans the IP addresses from any device to search for any vulnerabilities). First we need to see know the IP address of our **Ubuntu VM** in order to perform the attack. by using the command:
```bash
ip a
```
We can see our IP address, from our VM. In this case our IP address is: ![Screenshot 2025-03-26 193621](https://github.com/user-attachments/assets/59d2ce2d-6fb9-448e-89f1-f65c7886330b)<br/>
(All the blue drawing is information is not relevant, but still can be comprimising and the one that is in yellow is the IP address).<br/>

After knowing the IP address we use the next command on the app Nmap, in our **Parrot OS** to track the address.
```bash
Nmap -A (IP address that we tracked)
```
After clicking enter a message will pop out saying this: 

![Screenshot 2025-03-26 200724](https://github.com/user-attachments/assets/65e66ca7-c2e1-47da-8737-ec9e1b542d58)<br/>
(The one drawing in blue is Ubuntu's VM IP address)<br/>

As you can see Nmap already scanned the IP address saying that there is 1 host up. It says how many times did scanned the address, where did the scan happened and how much time did it take to find a vulnerability. That's how we perform an Attack using Nmap as a pentesting tool.

## Defending ourselves from the attack from our Ubuntu's VM

To be able to defend ourselves or device we need to install a firewall by using the next commands:

```bash
sudo apt install ufw
```
```bash
sudo ufw enable
```
```bash
sudo ufw allow ssh
```
These commands would create a defense for our systems that would regulate who ever tries to penetrate it. Finally, using the next command we would deny the access of our information (in this case our IP address). To do this we need the IP address of the attacker so that way we can deny the entrance to them (we can use the same command to see the IP address of the VM that is attacking).

```bash
sudo ufw allow from "Attacker's IP address"
```
Now that we have this done we can check our VM's firewall status by doing the next command:
```bash
sudo ufw status
``` 
It should appear something like this: 

![Screenshot 2025-03-26 222000](https://github.com/user-attachments/assets/a22dc867-691a-4702-b668-ef471a435e79)<br/>
(Our IP address is the one that is all drawn in blue)<br/>

# Analyzing The Network Traffic Of Our Home Lab
To analyze the network traffic of our VM we just need to install Wireshark (An app that tracks all type of data that enters into our network, this is helpful to see if we are being targeted by any other hacking tool). By writing the next command we would be able to install wireshark in our Ubuntu VM.

```bash
sudo apt install wireshark
```
After installing Wireshark now we are going to be able to capture, as well as, analyze the data that our network receives in order to catch anyone who is trying to get access or penetrate it. Using the following command we can run the program **Wireshark**:

```bash
sudo wireshark
```
After entering the command on the terminal, a window will pop out.
![Screenshot 2025-03-27 092759](https://github.com/user-attachments/assets/b6711b84-ee6a-4399-8847-d87ad81530f5)<br/>

We need to click the button "Capture" in order to begin the process of the Network Analysis. Once we clicked that button another window will pop out, to begin the process of capture network data we need to click the button that is all the way down that says "Start".

![Screenshot 2025-03-27 093728](https://github.com/user-attachments/assets/a861bc9e-e772-49e9-93ad-0a46c56c4cd0)<br/>

After doing the program will run and now we can capture all the data that tries to penetrate our network. At this point we can repeat the attack to check if the program is doing all right.

![image](https://github.com/user-attachments/assets/22790138-185b-49c1-a84f-1e4ce4c8ae2f)<br/>
(Wireshark running in Ubuntu's VM without getting attacked by Parrot OS)


![image](https://github.com/user-attachments/assets/9a096784-33ab-4aa6-be98-c4cf4f82e2a4)<br/>
(Wireshark running in Ubuntu's VM getting attacked by Nmap performed by Parrot OS)

All of those numbers are the multiple ways Nmap tried to scanned the IP address of Ubuntu's VM and what is surprising is how much time did it take to Nmap to do all of those attacks to a single IP address. 

# Conclusion of the Project

By doing this project we could notice how set up a home lab, a network that gives us the opportunity to analyze a variety of tools without getting exposed to any potential legal risk for trespassing any external device. In this project we analyzed how to set up our personal NAT network, how to install different Linux Operating Systems (Ubuntu and Parrot OS), as well installing and updating all of them. We also perform a Cyberattack in another device (Ubuntu's VM), and we defend ourselves by installing a firewall and a ssh to deny the access of the app Nmap (the one that we used to realize the cyberattack to the IP address of Ubuntu's VM). Lastly, we also installed an app (Wireshark) that allowed us to capture all the data that tried to harm our device.

I hope this helps anyone to start their portfolio just like me. 


