# <a href="https://blueteamlabs.online/home/challenge/secrets-85aa2bb3a9">Secrets</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** You’re a senior cyber security engineer and during your shift, we have intercepted/noticed a high privilege actions from unknown source that could be identified as malicious. We have got you the ticket that made these actions.
You are the one who created the secret for these tickets. Please fix this and submit the low privilege ticket so we can make sure that you deserve this position.
Here is the ticket:
`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmbGFnIjoiQlRMe180X0V5ZXN9IiwiaWF0Ijo5MDAwMDAwMCwibmFtZSI6IkdyZWF0RXhwIiwiYWRtaW4iOnRydWV9.jbkZHll_W17BOALT95JQ17glHBj9nY-oWhT1uiahtv8`

**Category:** Incident Response

**Type:** Challenge

**Difficulty:** Easy

**File:** `N/A`

**Tools:** `Cyberchef` `Hashcat`

> [CyberChef](https://cyberchef.org/) is a simple, intuitive web app for analysing and decoding data without having to deal with complex tools or programming languages.
> 
> [Hashcat](https://github.com/hashcat/hashcat) is the world's fastest and most advanced password recovery utility, supporting five unique modes of attack for over 300 highly-optimized hashing algorithms.

**Note:** For this walkthrough, I have spun up a Kali Linux virtual machine to utilize its tools. If you haven't set it up yet, I highly suggest following this [pentest lab](https://github.com/mmhgwyjs/pentest-lab) guide for your setup.

---

## **Questions and Answers:**

***1. Can you identify the name of the token? (Format: String)***

- We will use `cyberchef` to decode base64.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/b54ff7d7-d0de-47a9-a72f-5f43f4398894)

  **Answer: `jwt`**

  > `JSON Web Token (JWT)` is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. 

***2. What is the structure of this token? (Format: Section.Section.Section)***

- In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are: `Header` `Payload` `Signature`

  Therefore, a JWT typically looks like the following. `xxxxx.yyyyy.zzzzz`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a3e3fbda-85e7-458d-872f-a7907012b8c0)

  **Answer: `header.payload.signature`**

***3. What is the hint you found from this token? (Format: String)***

- By checking the payload section in the decoded string, we can find the flag.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a006cc56-36e3-49ea-a0ad-946a09488434)

  **Answer: `_4_Eyes`**

***4. What is the Secret? (Format: String)***

- We will be using a tool called `hashcat`. Since we do not know the length of the secret, we will proceed with trial and error until we crack the password.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/915f6f7e-9b4e-4294-9a80-33b3aab59ac9)

  > If we see 'Exhausted' as the result, it means we need to try a different method to crack the password.

  > More information about the tool can be found by using this command `man hashcat`. This will display the manual for the tool.

- Using the command `hashcat secret.txt -a 3 ?a?a?a?a`
  
  > `secret.txt` - This file contains the token that we will crack.
  >
  > `-a 3` - Attack mode - Brute force.
  > 
  > ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/bf83f068-3198-4ff7-8738-7dcc5d72fcc6)
  >
  > `?a?a?a?a` - Built-in Charsets. Each `?a` corresponds to one character, so overall we are trying to crack a 4-character password.
  > 
  > ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/fbc176f0-6a54-4bbb-ab4a-48a83e0dde60)
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/5031fdeb-b0a4-4252-be9f-3cffc526f294)

  > This consumes memory, so make sure you have a spare. I use 8GB of RAM.
  
  **Answer: `bT!0`**
  
***5. Can you generate a new verified signature ticket with a low privilege? (Format: String.String.String)***

- We will use `JWT.io` to generate a new token.

  > This can also be used to decode the token instead of using `CyberChef`.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/3427508d-ece4-4a65-8364-65e0c3e31590)

  > Change the admin to false and input the secret we cracked earlier.

  **Answer: `eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmbGFnIjoiQlRMe180X0V5ZXN9IiwiaWF0Ijo5MDAwMDAwMCwibmFtZSI6IkdyZWF0RXhwIiwiYWRtaW4iOmZhbHNlfQ.nMXNFvttCvtDcpswOQA8u_LpURwv6ZrCJ-ftIXegtX4`**
  
---

## **Additional Analysis/Artifacts**

N/A
