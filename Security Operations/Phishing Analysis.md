# <a href="https://blueteamlabs.online/home/challenge/phishing-analysis-f92ef500ce">Phishing Analysis</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** A user has received a phishing email and forwarded it to the SOC. Can you investigate the email and attachment to collect useful artifacts?

**Category:** Security Operations

**Type:** Challenge

**Difficulty:** Easy

**File:** `Website contact form submission.eml`

**Tools:** `Thunderbird` `Text Editor`

> [Thunderbird](https://www.thunderbird.net/en-US/) is a free and open-source software project founded in 2003 to make communicating and collaborating better. 

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. Who is the primary recipient of this email?***

- Although we can use any text editor to open the EML file, we will be using Mozilla Thunderbird.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/c4541edf-4008-4142-887c-3ea5e3cf69a1)

  **Answer: `kinnar1975@yahoo.co.uk`**

***2. What is the subject of this email?***

- Using the same details above.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a8f4f83e-85f6-43aa-8d8e-2d6220773c04)

  **Answer: `Undeliverable: Website contact form submission`**

***3. What is the date and time the email was sent?***

- Same details.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/f6d789b6-6843-4d7e-97c2-f59d5d6394e3)

  **Answer: `18 March 2021 04:14`**

***4. What is the Originating IP?***

- We can check it in the email headers.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/3d8cb136-21df-4c16-b6ba-b5f07d3d4c33)

  **Answer: `103.9.171.10`**

***5. Perform reverse DNS on this IP address, what is the resolved host? (whois.domaintools.com)***

- Use `whoisdomaintools`: `https://whois.domaintools.com/`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a00824f1-b89b-41ae-9e25-f1993a369f6f)

  **Answer: `c5s2-1e-syd.hosting-services.net.au`**

***6. What is the name of the attached file?***

- We can see it at the bottom part of Thunderbird client.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a20d50d9-361f-45cd-a4ff-3156999a9084)

  > This can also be checked under `Message` > `Attachments`.
  >
  > ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/2f34dd95-4cb4-434d-8ca4-669a7c113a44)

  
  **Answer: `Website contact form submission.eml`**

***7. What is the URL found inside the attachment?***

- Check the body of the attached email.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/97d8863c-4d1d-4082-9dc6-b9049039401d)

  **Answer: `https://35000usdperwwekpodf.blogspot.sg?p=9swghttps://35000usdperwwekpodf.blogspot.co.il?o=0hnd`**

***8. What service is this webpage hosted on?***

- Using the URL we found.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/393d74a3-4482-46b6-a91e-a3736a135e4c)

  **Answer: `blogspot`**

***9. Using URL2PNG, what is the heading text on this page? (Doesn't matter if the page has been taken down!)***

- `URL2PNG`: `https://www.url2png.com/`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/0671e90f-134b-4ef3-b77a-e89245c52052)

  **Answer: `Blog has been removed`**

---

## **Additional Analysis/Artifacts**

#### Website contact form submission.eml
MD5: 25f8bd3a9a4d5a2cfd1cb03381331836 

SHA1: b593dd7ff2bd891decb596a6423dd74733cc6831 

SHA256: 1dc38b916e59e686933d831a34e6b68ac94b5e7efbeb572861dbf2ec996d3d6e

**VirusTotal:** 

![image](https://github.com/mmhgwyjs/btlo/assets/159692853/de63e75b-e05b-4d99-99b7-aa701f037fae)

**URLScan.io**

`https://35000usdperwwekpodf.blogspot.sg?p=9swghttps://35000usdperwwekpodf.blogspot.co.il?o=0hnd`

![image](https://github.com/mmhgwyjs/btlo/assets/159692853/6b4207ff-4bca-452e-93c8-552d6bb56e72)

