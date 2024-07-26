# <a href="https://blueteamlabs.online/home/challenge/squid-game-12b0862d18">Squid Game</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Will you survive the Squid Games?

**Category:** CTF-Like

**Type:** Challenge

**Difficulty:** Medium

**File:** `Invitation Card.jpg`

**Tools:** `Steghide` ``

> [Steghide](https://steghide.sourceforge.net/) is a steganography program that is able to hide data in various kinds of image- and audio-files.
>
> [Stegsolve](https://github.com/Giotino/stegsolve/releases) is an immensly useful program for many steganography challenges, allowing you to go through dozens of color filters to try to uncover hidden text.

**Note:** For this walkthrough, I have spun up a Kali Linux virtual machine to utilize its tools. If you haven't set it up yet, I highly suggest following this [pentest lab](https://github.com/mmhgwyjs/pentest-lab) guide for your setup.

---

## **Questions and Answers**

***1. What is the phone number on the invitation card in Squid Game? (Research this online!)***

- Let's use our `Google` skills.

  **Answer: `8650 4006`**

  > Tip: Check images.

***2. Can you extract something from the invitation card file? What is the name of the file?***

- We will use a tool called `steghide`. It will require a passphrase; use the number we obtained earlier.

  ![image](https://github.com/user-attachments/assets/b12e370e-7ede-4b1f-a422-601f24c510da)

  > `steghide extract -sf filename`

  **Answer: `Dalgona.png`**

***3. What hint text can be discovered in the final file?***

- Let's use the tool called `stegsolve`. Run the command `java -jar StegSolve-1.4.jar`.

  ![image](https://github.com/user-attachments/assets/7eebe56a-9238-44fe-8983-de24bad428dd)

- Open the extracted `PNG` file and run it through `stegsolve` to reveal the hidden text.

  ![image](https://github.com/user-attachments/assets/f442b98b-683a-40ce-be1b-dab2de487dec)

***4. What is the final flag?***

---

## **Additional Analysis/Artifacts**

### Static Analysis

**VirusTotal:** 

![image](https://github.com/user-attachments/assets/d40db1fb-538d-4517-b2b4-af3134d901d6)


### Dynamic Analysis

***1. sample testing.***
