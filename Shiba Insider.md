# <a href="https://blueteamlabs.online/home/challenge/shiba-insider-5b48123711">Shiba Insider</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Can you uncover the insider?

**Category:** Digital Forensics

**Type:** Challenge

**Difficulty:** Easy

**Files:** `insider.pcap` `README.txt` `ssdog1.jpeg`

**Tools:** `Wireshark` `Exiftool`

> [Wireshark](https://www.wireshark.org/) is the world's foremost network protocol analyzer. It lets you see what's happening on your network at a microscopic level.
> 
> [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.
>

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. What is the response message obtained from the PCAP file?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***2. What is the password of the ZIP file?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***3. Will more passwords be required?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***4. What is the name of a widely-used tool that can be used to obtain file information?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***5. What is the name and value of the interesting information obtained from the image file metadata?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***6. Based on the answer from the previous question, what tool needs to be used to retrieve the information hidden in the file?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***7. Enter the ID retrieved.***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***8. What is the profile name of the attacker?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**
  
---

## **Additional Analysis/Artifacts**

### Wireshark `insider.pcap`

> [Wireshark cheat sheet](https://www.comparitech.com/net-admin/wireshark-cheat-sheet/)

- Capture File Properties

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/fd8733e3-2f84-495c-a784-bce50ed1754f)

  > Obtaining the timeframe of the packet capture is important and can be used to cross-reference the event you are investigating.

- Protocol Hierarchy

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/62cef36e-de20-49cd-a5be-4e2bec17d8e2)

  > It lists all the protocols used within the packet capture.

- Conversations

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/c94a4876-1375-4e4c-a2d4-e008c08d04ab)

  > All communications established can be seen here. The bytes column is essential for observing how much traffic is generated between two endpoints.
  
- Export Object

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/0b023511-349c-4350-9211-a0b3342cb4a2)

  > Any files uploaded or downloaded within the packet capture timeframe will be available here for investigation and can be downloaded.


