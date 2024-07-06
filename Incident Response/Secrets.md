# <a href="https://blueteamlabs.online/home/challenge/secrets-85aa2bb3a9">Secrets</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** You’re a senior cyber security engineer and during your shift, we have intercepted/noticed a high privilege actions from unknown source that could be identified as malicious. We have got you the ticket that made these actions.
You are the one who created the secret for these tickets. Please fix this and submit the low privilege ticket so we can make sure that you deserve this position.
Here is the ticket:
`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmbGFnIjoiQlRMe180X0V5ZXN9IiwiaWF0Ijo5MDAwMDAwMCwibmFtZSI6IkdyZWF0RXhwIiwiYWRtaW4iOnRydWV9.jbkZHll_W17BOALT95JQ17glHBj9nY-oWhT1uiahtv8`

**Category:** Incident Response

**Type:** Challenge

**Difficulty:** Easy

**File:** `file`

**Tools:** `Cyberchef`

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

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

***4. What is the Secret? (Format: String) ***

- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***5. Can you generate a new verified signature ticket with a low privilege? (Format: String.String.String)***

- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**
  
---

## **Additional Analysis/Artifacts**

- We can also use `JWT.io` to decode the token.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/01c6fee7-b2c1-44a8-a23e-5cb053b0cbd8)

  > https://jwt.io/introduction/
