# <a href="https://blueteamlabs.online/home/challenge/follina-f1a3452f34">Follina</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** On a Friday evening when you were in a mood to celebrate your weekend, your team was alerted with a new RCE vulnerability actively being exploited in the wild. You have been tasked with analyzing and researching the sample to collect information for the weekend team.

**Category:** Incident Response

**Type:** Challenge

**Difficulty:** Easy

**File:** `sample.doc`

**Tools:** `VirusTotal` `oleobj`

> [VirusTotal](https://www.virustotal.com/gui/home/upload) is a tool that inspects items with over 70 antivirus scanners and URL/domain blocklisting services, in addition to a myriad of tools to extract signals from the studied content.
>
> [Oletools](https://github.com/decalage2/oletools?tab=readme-ov-file) is a package of python tools to analyze Microsoft OLE2 files, such as Microsoft Office documents or Outlook messages, mainly for malware analysis, forensics and debugging.

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

- Check using `oleobj` from `oletools`. Use the command `oleobj filename`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/bc959165-d2f6-4161-bd24-d114820940e6)

  > `oletools` can be downloaded and used on both Windows and Linux-based systems.
  
- It can also be checked under the `Relations` tab on `VirusTotal`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/effbbae5-d1dc-4f9d-af1f-8a16dc100a49)

  **Answer: `https://www.xmlformats.com/office/word/2022/wordprocessingDrawing/RDF842l.html!`**

***4. What is the name of the XML file that is storing the extracted URL? (Format: file.name.ext)***

- We can extract the `.doc` file by changing the extension to `.zip`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/1081ed5f-3c5e-49b7-8d77-c7f23a4b23ad)

- Look for the XML file that contains the URL we found earlier.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/7a8f0cff-fa59-4bde-89f2-472c1f2bbda6)

  **Answer: `document.xml.rels`**

***5. The extracted URL accesses a HTML file that triggers the vulnerability to execute a malicious payload. According to the HTML processing functions, any files with fewer than <Number> bytes would not invoke the payload. Submit the <Number>. (Format: Number of Bytes)***

- Since I am not yet an expert on this, let's try to find available analysis reports. To start, we can search for the URL we found and look it up on `VirusTotal`.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/4418684d-2cd1-4cd9-a1bb-f401b8afa239)

- Under the `Community` tab, we can see different users who provide available reports for deeper analysis. One of the articles provides the answer that we are looking for.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/ad8a9ef3-485e-4f62-ae6f-93c3358d6905)

  > https://www.huntress.com/blog/microsoft-office-remote-code-execution-follina-msdt-bug

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/faf9056a-6531-42d2-80a6-bbed24603cfa)

  > https://twitter.com/_JohnHammond/status/1531170265039781888

  **Answer: `4096`**

***6. After execution, the sample will try to kill a process if it is already running. What is the name of this process? (Format: filename.ext)***

- Using the same article we found.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/c0eee801-6fc8-486e-9c8f-70a7ab14f7db)

  **Answer: `msdt.exe`**

***7. You were asked to write a process-based detection rule using Windows Event ID 4688. What would be the ProcessName and ParentProcessname used in this detection rule? [Hint: OSINT time!] (Format: ProcessName, ParentProcessName)***

- We will still be using the same article.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/5e587d1a-fdab-48fc-b101-58cfe06561b3)

  **Answer: `msdt.exe, winword.exe`**
  
***8. Submit the MITRE technique ID used by the sample for Execution. [Hint: Online sandbox platforms can help!] (Format: TXXXX)***

- Let's go back to the `Community` tab in `VirusTotal` and we can find a report from `JoeSandbox`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/90a37aac-837c-4c27-a68d-5a36670ef774)

  > https://www.joesandbox.com/analysis/818698/0/html

- By checking all the techniques used in `MITRE ATT&CK`, we can find the `technique ID` we need.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a782ab21-4c65-4205-9c61-c185859d2a33)

  **Answer: `T1055`**

***9. Submit the CVE associated with the vulnerability that is being exploited. (Format: CVE-XXXX-XXXXX)***

- Using the article from earlier, we can retrieve the CVE details.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/e569d4d3-0d85-4171-bd39-57911924294b)

  **Answer: `CVE-2022-30190`**
---

## **Additional Analysis/Artifacts**

### Useful Links

https://msrc-blog.microsoft.com/2022/05/30/guidance-for-cve-2022-30190-microsoft-support-diagnostic-tool-vulnerability/

https://msrc.microsoft.com/update-guide/en-US/vulnerability/CVE-2022-30190

https://thedfirreport.com/2022/10/31/follina-exploit-leads-to-domain-compromise/
