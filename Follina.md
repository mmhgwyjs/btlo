# <a href="https://blueteamlabs.online/home/challenge/follina-f1a3452f34">Follina</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** On a Friday evening when you were in a mood to celebrate your weekend, your team was alerted with a new RCE vulnerability actively being exploited in the wild. You have been tasked with analyzing and researching the sample to collect information for the weekend team.

**Category:** Incident Response

**Type:** Challenge

**Difficulty:** Easy

**File:** `sample.doc`

**Tools:** `VirusTotal` `tool2`

> [VirusTotal](https://www.virustotal.com/gui/home/upload) is a tool that inspects items with over 70 antivirus scanners and URL/domain blocklisting services, in addition to a myriad of tools to extract signals from the studied content.

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. What is the SHA1 hash value of the sample? (Format: SHA1Hash)***

- Using `powershell`, execute the command `Get-FileHash filename -Algorithm SHA1`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/0d81e82b-4e46-44b8-881d-828250d6eab1)

  **Answer: `SHA106727FFDA60359236A8029E0B3E8A0FD11C23313`**

  > For Linux machines, use the command `sha1sum filename`.

***2. According to VirusTotal, what is the full filetype of the provided sample? (Format: X X X X)***

- Go to `VirusTotal` and search for the hash we obtained.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/8342c602-4ed7-4a6e-901b-4161ba1d00eb)

  **Answer: `Office Open XML Document`**

***3. Extract the URL that is used within the sample and submit it. (Format: https://x.domain.tld/path/to/something)***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***4. What is the name of the XML file that is storing the extracted URL? (Format: file.name.ext)***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***5. The extracted URL accesses a HTML file that triggers the vulnerability to execute a malicious payload. According to the HTML processing functions, any files with fewer than <Number> bytes would not invoke the payload. Submit the <Number>. (Format: Number of Bytes)***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***6. After execution, the sample will try to kill a process if it is already running. What is the name of this process? (Format: filename.ext)***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***7. You were asked to write a process-based detection rule using Windows Event ID 4688. What would be the ProcessName and ParentProcessname used in this detection rule? [Hint: OSINT time!] (Format: ProcessName, ParentProcessName)***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**
  
***8. Submit the MITRE technique ID used by the sample for Execution. [Hint: Online sandbox platforms can help!] (Format: TXXXX)***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***9. Submit the CVE associated with the vulnerability that is being exploited. (Format: CVE-XXXX-XXXXX)***

- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**
---

## **Additional Analysis/Artifacts**

### Static Analysis

**VirusTotal:** 

### Dynamic Analysis

***1. sample testing.***
