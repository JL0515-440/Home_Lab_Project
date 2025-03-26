# Home Lab Project
This Repository is being made by me (JL0515-440), because I wanted to do research regarding on how some Cybersecurity "Penetration testing" Tools work. By doing this I'm creating a personal network so that way I do not affect my own machine, and any other external device.

I took inspiration from a lot of videos to do this project, as well as, some AI (ChatGPT and Gemini) bots to research ideas, but the one that encouraged me to do this project was this one in Youtube: 

**CyberDojo**: https://www.youtube.com/watch?v=ZpFticDPEkw&list=PLtW3uHVuf_vgwHht2JTm_UUklczqz_PX7&index=76&t=523s

(Original Creator of the video I took inspiration from and many of the steps I have done in the project)

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

## Stablishing the NAT Network

**THIS STEP IS HIGHLY IMPORTANT BECAUSE WITHOUT THE CREATION OF OUR OWN NAT NETWORK WE COULD AFFECT ANY OTHER EXTERNAL MACHINE AND THAT WOULD INVOLVE A MAJOR ISSUE ON OUR HOME LAB. AS WELL AS A POTENTIAL LEGAL RISK IF WE DO NOT SECURE THIS**

We go to "Tools" all the way in the left top, and then we select the option called "Network". After that we go to "Nat Network" and then we create a new Nat Network you can call it whichever name you find more attractive to you.

![image](https://github.com/user-attachments/assets/5a02f1cd-6204-42f6-8b31-bbb6f061ebb2)<br/>

(I created one called "Home_Lab_Cybersecurity_Network" just for reference)


## Update & download of essential tools

After having the VMs already setted up we must check if the OS have their systems updated and with all the necessary tools for our activities. Using the following command: 
```bash
sudo apt update && sudo apt upgrade -y
``` 
On each terminal (in this case Parrot OS & Ubuntu) so that way we can update and upgrade our OSs. I'm going to use the next command to install the essential tools that we will use for our Home Lab.
```bash
sudo apt install -y build essential git wget
```
# Simulate an Attack

Now we are going to simulate an Attack using Nmap (An app that scans the IP Adress from any device)

