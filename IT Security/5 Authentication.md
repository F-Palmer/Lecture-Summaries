Prev: [[4 Kryptographie]] Next: [[6 Malware]]

Authentication vs Authorization see [[1 Concepts, Principles & Terminology]] 

### Authentication Goals
- No false negatives (No falsely denying access)
- No false positives (No falsely allowing access)

## Authentifizierungsfaktoren
- something you know
- something you have
- something you are
## Passwords
not a strong defence on its own, because:
- people use weak passwords
- Human memory limitations

> Weak password: 
> easy to guess/ predict
> Characteristics: 
> - short
> - Use a common word
> - predictable sequence of characters
> - personal information in a password

### Threats against Password Authentication
- offline cracking
- keylogging
- social engineering

> Replay Attack: 
> Attacker sniffs the hash from a true message and blocks it from reaching the recipient
> Attacker can then replay the message at a later time
> For example password when he needs it

### Brute Force Attack: 
- offline
- use program to automatically try every possible combination
- can be reduced with parameters 
$62^6$ possible passwords takes about 10 min (upper/ lower case + digits)
- use rainbow table to reduce search time (common words and passwords)
- users use upper case letters at the beginning and numbers at the end

### Salting

add a random salt to the password before hashing -> defeats rainbow tables 
store the salt in plain text with the password hash
		Why plain text? 
		 Salts are not secrets -> does not help to reverse the hash
		 salts force the attackers to use a new rainbow table for every salt/ user -> hashes differ between users even if passwords are the same
-> choose a relatively slow hash function so that cracking becomes more difficult

### Peppering

add a random pepper to the password before hashing
store the pepper in another physically/ virtually separated location 

### Linux password security
previously stored as hash in `/etc/passwd`, which was publicly available to all users, only superuser could change
now stored in `/etc/shadow` only visible to the superuser

## Something you are 
Examples: 
- Fingerprint
- Retina scans
- Keystroke dynamics

Advantages: 
- cannot be disclosed, lost, forgotten

Disadvantages: 
- cost for installation and maintenance
- reliability
- can possibly be forged

## Something you have

Examples: 
- Tokens, hardware keys

## Challenge Response

Simple Challenge-Response
![[simple challenge response.png| 550]]
Prevents replay attacks is used only once and is random
Problem: 
- Bob could malicious

Two-way Challenge-Response
![[two way challenge.png|550]]
prevents MiM attacks, as both sides authenticate
Problem: 
- Vulnerable against reflection attacks, if initiator does not respond before target

> Reflection Attack: 
> when an attacker takes a challenge meant for them and **reflects it back** to the legitimate party so  the legitimate party ends up solving its own challenge 

how this effects two-way challenge response: 
- **Alice → Eve:** “Challenge: NA”
- **Eve → Alice:** “Challenge: NA” (reflected)
- **Alice → Eve:** “Response: f(NA, K)”
- **Eve → Alice:** “Response: f(NA, K)” (reflected back)

more efficient two-way challenge response: 
![[fast two way challenge.png|550]]

## One time Passwords (OTP)
- not vulnerable to replay attacks 
- avoids the problem of same password on many systems

Challenges: 
- Time synchronisation
- Delivery of OTP

Time-Synchronised OTP Generation
- Token clock is synchronised with authentication server
- generate new OTP based on current time

OTP with Security Token
- generates a random number that changes every 60 sec
- Seed shared with the server

new OTPs are created from the past OTP
Lamport's OTP algorithm

## Multifactor Authentication (MFA)
- must include unique factors
- Attackers must defeat both to compromise the authentication

## Authentication over a Network
- Public Key Interfaces (PKI)

![[Linux File Permission.png]]

## Discretionary Access Control (DAC)
The owner of the Ressource controls how has which permissions on it

Problem: 
- If a user has access to data, they can often **copy it**, **re-share it**, or **forward it** to others.
- The system can’t stop the data from flowing to people who shouldn’t have it.
- DAC assumes users will: behave responsibly
- In real organisations: Employees don’t decide who gets access to HR data.

## Mandatory Access Control (MAC)
- Access level is based on security clearance levels 
- Every object gets a classification (Public, confidential, top secret...)
- Admin grats rights according to access level
