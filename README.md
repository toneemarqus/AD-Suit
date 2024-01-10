# AD Suit
# Overview
ADSuit is a comprehensive penetration testing suite designed for security professionals and network administrators. It focuses on enhancing the assessment of Active Directory (AD) environments, providing a wide range of tools and functionalities that streamline the process of identifying vulnerabilities, auditing AD setups, and simulating attack scenarios.
# Features
- GUI based tool.
- Hosts, domain, IPs and credentials management
- One click to start a session with WinRM or PSexec.
- One click to start a spraying usernames and passwords agains a host with two different tools (CrackMapExec and GoMapExec).
- Pivot easly from network to network with only a reverse shell.
- Enumerate and attack active directories with one click.
# Installation

Download adsuit-1.0.deb and install it with dpkg:
```
sudo dpkg -i adsuit-1.0.deb

```
To uninstall the tool:
```
sudo apt-get remove adsuit
```
# Usage
Start the tool with root privileges:
```
sudo adsuit
```

 
# Step-By-Step Guide
## Hosts Tab:

Here you will input the IP adresses you are going to test along with the domain if any. Both field supports auto save when changes are made.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/879b2a3c-2ac1-43f9-8ad1-3563563ac96c)

## UserManagement Tab:

In this tab, you will enter all the usernames, passwords and hashes you found, they are important and going to be used in the next tabs.
All the fields supports auto save when change is made.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/64d4ccd5-b8f4-4fb8-8fd0-7dfc8e6eb6b9)

## Sessions Tab:

This tab is used to start sessions using the usernames, password and hashes from the UserManagement tab, when clicking connect button, new terminal will open with the session opened.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/00372325-1977-427b-aee0-10796937aa71)

It supports three session which are:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/121c814f-39e8-4de8-b37f-f8c30eb91f97)

You can also choose between using a password or a hash along with the username:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/c8e9f5c3-0c4c-4e0a-8bda-5ea079f9fab5)

Example: here we used forest machine from hack the box, the user is "svc-alfresco" and password "s3rvice" and the session is made via WinRM:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/3accd9a4-1cc6-4361-8959-88732711c70b)

## Spraying Tab:
In this tab, two tools are used to spray the usernames, password and hashes to a single or multiple IPs.

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/58dcbe83-607a-41b9-83f2-8bc047dfe5ac)

Two tools are used to spray the password which are:
![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/8234485b-2004-47be-95d6-e2e6d62be977)

Example: Here we are spraying usernames agains the password using CrackMapExec with multiple IPs agains SMB protocol on forest machine from hack the box:

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/f46f70b1-37bb-4101-a35b-e17db71151f8)
The attack result:
![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/0a2a7367-3adb-48d5-9c6e-1a9cf053ea2f)

## Pivoting Tab:
This tab is one of the most important tabs, its supports pivoting to new network via reverse shell!

![image](https://github.com/toneemarqus/AD-Suit/assets/85018947/a3e11f8d-f7b9-42ed-b362-ab187c7f9dce)

This tab uses ligolo-ng to reach the goal, it starts proxy internally and configue it, then upload agent to the host that the reverse shell came from, all done automaticlly, just send the reverse shell!

While pentesting, you might face a host with dual interfaces, and the second interface leads you to an internal network, but you still can't access it from kali.
In this tab, you will need to enter the following information before starting the listener:
1: OS: The host that you are sending the reverse shell from operating system.
2: Your IP: Here you need to enter you kali linux ip.
3: Target Network: The IP address of the network that you want to pivot to.
4: Port: The port that you are going to use for listing to the reverse shell.
5: Upload Wait Time: This time is the time that you think it is enough to upload agent file to the machine that the reverse shell will come from, it depents on how fast is the connection, adjust it depending on that.

Windows host example: in this example, we hacked a windows host, then discovered that it's dual interface host, and the other interface might takes as somewhere interesting, so we need to pivot:









# Contributing to Go Map Exec

I welcome contributions from everyone! Here are some ways you can contribute:

1. **Reporting Bugs**: If you find a bug, please use the Issues tab to report it, providing as much detail as possible.

2. **Feature Suggestions**: Have an idea to improve Go Map Exec? We'd love to hear it! Submit your suggestions through the Issues tab.

3. **Pull Requests**: Want to directly contribute to the code? Great! Please submit a pull request with a clear description of your changes and any necessary tests or documentation.
Thank you for your interest in improving Go Map Exec!

# Disclaimer
Go Map Exec is intended for legal purposes only. Users are responsible for complying with applicable laws. The developer is not liable for misuse or damage caused by this tool.
