# <a href="https://blueteamlabs.online/home/challenge/the-planets-prestige-e5beb8e545">The Planet's Prestige</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** CoCanDa, a planet known as 'The Heaven of the Universe' has been having a bad year. A series of riots have taken place across the planet due to the frequent abduction of citizens, known as CoCanDians, by a mysterious force. CoCanDa’s Planetary President arranged a war-room with the best brains and military leaders to work on a solution. After the meeting concluded the President was informed his daughter had disappeared. CoCanDa agents spread across multiple planets were working day and night to locate her. Two days later and there’s no update on the situation, no demand for ransom, not even a single clue regarding the whereabouts of the missing people. On the third day a CoCanDa representative, an Army Major on Earth, received an email.

**Category:** CTF-Like

**Type:** Challenge

**Difficulty:** Easy

**Files:** `A Hope to CoCanDa.eml` `PuzzleToCoCanDa.pdf`

**Tools:** `Text Editor` `Mail Client` `Exiftool` `CyberChef`

> [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.
>
> [CyberChef](https://cyberchef.org/) is a simple, intuitive web app for analysing and decoding data without having to deal with complex tools or programming languages.

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. What is the email service used by the malicious actor?***

- We can open the eml file using any email client. Alternatively, opening it in a text editor will display the email headers, but we can't view attachments.

  ![image](https://github.com/user-attachments/assets/09f0127e-6d5a-4358-b497-260758db35be)

  > The `Received:` fields correspond to every mail server that an email passes through, which are also called `hops`. They are normally read from bottom to top.

  **Answer: `emkei.cz`**

***2. What is the Reply-To email address?***

- The most common field to spoof is the `From:` field.  

  ![image](https://github.com/user-attachments/assets/e203982b-4bf7-4b72-905e-1b186023a859)

  > Note that the `Return-Path:` and `Reply-To:` fields can also be spoofed, depending on whether the spammer wants to receive replies. Sometimes, the `To:` field is altered to hide the intended recipient’s address.

  **Answer: `negeja3921@pashter.com`**

***3. What is the filetype of the received attachment which helped to continue the investigation?***

- We can notice that there's an attachment; however, we cannot view it if we only open the eml file through a text editor.

  ![image](https://github.com/user-attachments/assets/9fa4d7b0-2fae-40bb-a120-cd464974ef30)

- Let's try to open it using the mail client called `Mozilla Thunderbird`.

  ![image](https://github.com/user-attachments/assets/78ca75a2-1ec4-46cb-b04d-fb2912d5311d)

- We're unable to open the attached PDF file. Let's use `exiftool` to investigate the file further. We'll use the command `exiftool filename`.

  ![image](https://github.com/user-attachments/assets/934bad3d-b994-4de9-b966-ee9494901a71)

  > We can see that the true file type is `ZIP` instead of `PDF`.

  **Answer: `.zip`**

- Let's rename the attachment to a `ZIP` file and extract it.

  ![image](https://github.com/user-attachments/assets/0a647dd0-b247-41f5-82f7-064b2a06a432)
 
***4. What is the name of the malicious actor?***

- Let's use `exiftool` again on all the extracted files.

  ![image](https://github.com/user-attachments/assets/d5bdce5c-ae7d-47be-a8c2-ba9995fc838f)

  > We can see that the true file type is JPEG, but there is no other important information.

  ![image](https://github.com/user-attachments/assets/bc4705c0-40a4-4257-b75c-343d9afc5d31)

  > We can see here that it is a PDF file, and there's another field that shows us the author.  
  
  **Answer: `Pestero Negeja`**

- `GoodJobMajor.pdf` gives us a clue about the attacker's location.

   ![image](https://github.com/user-attachments/assets/5c6f9c16-66e6-4c52-8022-267a2b8a4514)

***5. What is the location of the attacker in this Universe?***

- From one of the extracted files, let's check the `Money.xlsx` file.

  ![image](https://github.com/user-attachments/assets/dc05cd7e-41e9-407c-92a7-2b70bd8b4b85)

  > Make sure to show hidden files.

- At first glance, we can only see the attacker's message, but there appears to be another sheet.

  ![image](https://github.com/user-attachments/assets/a716eadb-8c35-457b-b021-065964556549)

- Again, we only see a blank sheet, but let's try using the `Find` tool.

  ![image](https://github.com/user-attachments/assets/25803023-1bc9-435c-a4fa-3ffb9caf5e5c)

  > I started searching for the letters 'A' then 'E' until I found the somewhat hidden text.
  
- We can also rename the `.xlsx` file to `.zip` to extract its contents. By checking the `sharedStrings.xml` file, we can uncover hidden text.

  ![image](https://github.com/user-attachments/assets/a5a64405-d118-4b1e-8074-ecf00d14d884)
  
- It appears to be in `base64` format; we can decode it using `CyberChef`.

  ![image](https://github.com/user-attachments/assets/65905f0d-9654-47d9-bd67-1a60d53cdbeb)

  > `VGhlIE1hcnRpYW4gQ29sb255LCBCZXNpZGUgSW50ZXJwbGFuZXRhcnkgU3BhY2Vwb3J0Lg==`

  **Answer: `The Martian Colony, Beside Interplanetary Spaceport.`**

***6. What could be the probable C&C domain to control the attacker’s autonomous bots?***

- We'll revisit the email address we identified earlier, which shows the attacker's email.

  **Answer: `pashter.com`**
  
---

## **Additional Analysis/Artifacts**

**VirusTotal:** 
- `A Hope to CoCanDa.eml`
  
  ![image](https://github.com/user-attachments/assets/1eda2cd1-4649-49af-bc65-f9ccd988968d)

- `emkei.cz`

  ![image](https://github.com/user-attachments/assets/b6b8c0e6-d1a1-4065-8fc4-586efbbbb231)
  
- `93.99.104.210`
  
  ![image](https://github.com/user-attachments/assets/9042765e-1bf8-4a44-83ca-7f7db9b2a719)

- `pashter.com`

  ![image](https://github.com/user-attachments/assets/d4029f88-e812-4005-be07-d6033a21cf9f)
  

#### Useful Links

https://alyninc.com/2018/11/10/email-headers-what-can-they-tell-the-forensic-investigator/
