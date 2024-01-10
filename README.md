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
Install libsqlcipher-dev:
```
sudo apt-get install libsqlcipher-dev
```
Download adsuit-1.0.deb and install it with dpkg
```
sudo dpkg -i adsuit-1.0.deb

```

# Usage
```
Run the tool with the required flags. Below are some of the common flags and usage examples:
-u: Specify a single username for the scan.
-p: Specify a single password for the scan.
-d: (OPTIONAL) Specify the domain for the scan.
-uf: (OPTIONAL) Specify a file containing a list of usernames.
-pf: (OPTIONAL) Specify a file containing a list of passwords.
-H: (OPTIONAL) Specify an NTLM hash for the scan.
-pr: (OPTIONAL) Specify protocols to check (all(Default), rdp, smb, ssh, winrm).
```
# Demo
https://medium.com/@toneemarqus/go-map-exec-your-ultimate-credentials-spraying-tool-d4a6bfa49bae 
 
# Example Commands
Scan all protocols with a Single Username and Password:
```
./go_map_exec -u username -p password 10.10.10.1
```
Scan customized Protocols:
```
./go_map_exec -pr 'ssh winrm' -u username -p password 10.10.10.1
```
Using a Username and Password File:
```
./go_map_exec -uf users.txt -pf passwords.txt 10.10.10.1
```
Scan a range of IP addresses.
```
./go_map_exec -u admin -p password123 192.168.1.100 192.168.1.101 192.168.1.102
or
./go_map_exec -u admin -p password123 192.168.1.100-3
```
Scan using an NTLM hash instead of a password.
```
./go_map_exec -u admin -H AAD3B435B51404EEAAD3B435B51404EE 192.168.1.100
```
Scan with domain credentials.
```
./go_map_exec -u admin -p password123 -d mydomain 192.168.1.100
```
# Contributing to Go Map Exec

I welcome contributions from everyone! Here are some ways you can contribute:

1. **Reporting Bugs**: If you find a bug, please use the Issues tab to report it, providing as much detail as possible.

2. **Feature Suggestions**: Have an idea to improve Go Map Exec? We'd love to hear it! Submit your suggestions through the Issues tab.

3. **Pull Requests**: Want to directly contribute to the code? Great! Please submit a pull request with a clear description of your changes and any necessary tests or documentation.
Thank you for your interest in improving Go Map Exec!

# Disclaimer
Go Map Exec is intended for legal purposes only. Users are responsible for complying with applicable laws. The developer is not liable for misuse or damage caused by this tool.
