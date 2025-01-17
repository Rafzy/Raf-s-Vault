# Security problems

- A system is secured if noone can access resources, and all of the resources are used as intended
- Some buzzwords:
	- Intruders -> Actors that attempt to breach secrutiy
	- Threat -> Potential security violation
	- Attack -> An active attempt to breach security violation


**Categories**
- Breach of confidentiality
	Unauthorized personel has access to private files
- Breach of integrity
	Modification of data
- Breach of availability
	Destruction of data
- Theft of service
	Use of resources
- Denial of service (DOS)
	Prevention of legitimate use

**Methods**
- Masquerading (Breach authentication)
	Pretends to be an authorized user
- Replay attack
	Man in the middle cuts of a communication line, and sends a replay of the message as if it's sent by the original sender
- Man-in-the-middle attack 
	Intruder sits in data flow, masquerading as sender to receiver
- Session hijacking
	Intercept an established session to bypass authentication
- Privilege escalation
	Attack type with access beyond what a user or resource is supposed to have



## Security Measure levels

>It's impossible to have absolute security, but we make cost to perpetrator sufficiently high to deter most intruders

Security must occur at four levels to be effective:
- Physical
	Data centers, servers, connected terminals
- Application
	Benign or malicious apps can cause security problems
- OS
	Protection mechanism
- Network
	Intercepted communications


## Program Threats

1. **Malware (Malicious Software)**
	Software designed to exploit, damage, or disable computers
2. **Trojan horse**
	Acts as a legitimate program, but malicious in nature
	- Spyware - Capture user data
	- Ransomware - Locks up data via encryption
3. Others:
	- Trap doors
	- Logic bombs


## Implement Security threats

- Defense in depth
- Security policy
- Vulnerability assessment compares real state of system
- Intrusion detection methods:
	- Signature based detection
	- Anomaly detection
	- False-positives and false-negatives a problem
- Virus protection
	- Searching all programs at execution for known virus pattern
	- Run in **sandbox** so cannot damage system
- Auditing, accounting, and logging all system or network activities
- Practice safe computing


## Firewall

- A network firewall is placed between **trusted** and **untrusted** hosts
	Aims to limit access between the two security domains
- Can be tunneled or spoofed
	- Tunneling allowed protocol to travel within an allowed protocol
	- Firewall rules are typically based off domain name or IP address which can be spoofed
- Personal firewall is software layer on given host
	It can monitor/limit traffic to and from host
- Application proxy firewall
	Understands application protocol and can control them (i.e., SMTP Simple Mail Transfer Protocol)
- System-call firewall
	Monitors all important system calls and apply rules to them (i.e., this program can execute that system call)


## Access Control

- Implements a security policy that governs who can access each specific system resource, and the type of access (Read only, read and write, etc) that is permitted in each instance

## Access Control Policy

Can be grouped into these categories:
- Discretionary access Control (DAC)
	Controls access based on the identity of the requestor
- Mandatory Access Control (MAC)
	Controls access based on comparing security labels with security clearance
- Role-based access control (RBAC)
	Controls access based on the roles that users have within the system, and on rules stating what accesses are allowed to users
- Attribute-based access control (ABAC)
	Controls access based on attributes of the user, the resource to be accessed, and current environmental conditions