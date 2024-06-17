# <a href="https://blueteamlabs.online/home/challenge/meta-b976cec9e2">Meta</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** The attached images were posted by a criminal on the run, with the caption "I'm roaming free. You will never catch me". We believe you can assist us in proving him wrong.

**Category:** Digital Forensics

**Type:** Challenge

**Difficulty:** Easy

**Files:** uploaded_1.JPG, uploaded_2.png

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you do not have it yet, you can follow this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

**Tool:** Exiftool
  > [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.

---

## **Questions and Answers:**

***1. What is the camera model?***

- Open the command prompt and type the command `exiftool` `filename`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/5b948531-96df-43b3-8bbf-076a1222913d)

  > We can extract the output to a text file using the command `exiftool filename > sample.txt`.
  >
  > ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/f005e0fa-f812-4b83-a505-8aa3ba98aff2)

  **Answer: `Canon EOS 550D`**

***2. When was the picture taken?***

- Using the same exiftool results.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/b3cd2612-4ede-4fde-8c70-9ce6c0425b29)

  **Answer: `2021:11:02 13:20:23`**

***3. What does the comment on the first image says?***

- Search for the keyword `comment`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/b954297e-71f5-4d2c-b90d-357a86ce2bdc)

  **Answer: `relying on altered metadata to catch me?`**

***4. Where could the criminal be?***

- Open either of the two images and perform an image search using Google Lens or any other tool you can use to search for that image.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/58f64c02-f386-408f-8d1e-e0ddad037d21)

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/62e4d301-6daf-45cd-9cd8-3ca62f93a932)

  **Answer: `kathmandu`**
  
---

## **Additional Analysis/Artifacts**

**VirusTotal:** 

- uploaded_1.JPG: [218190a5924a385e25702b2169a2b8abc1848e971a47d811363f2df322e9b6a0](https://www.virustotal.com/gui/file/218190a5924a385e25702b2169a2b8abc1848e971a47d811363f2df322e9b6a0/details)

- uploaded_2.png: [fdf27c77586f44952890621ea8ba508125219c9bf5e6d4f0c86430eb515e81d8](https://www.virustotal.com/gui/file/fdf27c77586f44952890621ea8ba508125219c9bf5e6d4f0c86430eb515e81d8/details)

> To obtain the hash values using CMD, type the command `certutil -hashfile filename hashalgo`.
>
> ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/73e2fa03-84ca-47f9-b86c-513df82de467)
