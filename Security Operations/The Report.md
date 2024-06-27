# <a href="https://blueteamlabs.online/home/challenge/the-report-a6dd340dba">The Report</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** You are working in a newly established SOC where still there is lot of work to do to make it a fully functional one. As part of gathering intel you were assigned a task to study a threat report released in 2022 and suggest some useful outcomes for your SOC.

**Category:** Security Operations

**Type:** Challenge

**Difficulty:** Easy

**File:** `2022_ThreatDetectionReport_RedCanary.pdf`

**Tools:** `PDF Reader`

---

## **Questions and Answers:**

***1. Name the supply chain attack related to Java logging library in the end of 2021 (Format: AttackNickname)***

- `Log4j` is a popular Java logging library underlying many third-party applications that was hit with a remote code execution vulnerability in December 2021. 

  **Answer: `Log4j`**

***2. Mention the MITRE Technique ID which effected more than 50% of the customers (Format: TXXXX)***

- Adversaries may abuse command and script interpreters to execute commands, scripts, or binaries. These interfaces and languages provide ways of interacting with computer systems and are a common feature across many different platforms.

  > https://attack.mitre.org/techniques/T1059/
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/14e67f30-c941-43a1-875b-817a9d428388)

  **Answer: `T1059`**

***3. Submit the names of 2 vulnerabilities belonging to Exchange Servers (Format: VulnNickname, VulnNickname)***

- `ProxyLogon` and `ProxyShell` targeted MicrosoftExchange servers and affected a massive number of systems, sometimes leading to ransomware deployment.

  **Answer: `ProxyLogon` `ProxyShell`**

***4. Submit the CVE of the zero day vulnerability of a driver which led to RCE and gain SYSTEM privileges (Format: CVE-XXXX-XXXXX)***

- In July 2021, researchers `Zhiniang Peng` and `Xuefeng Li` disclosed a Windows vulnerability called `PrintNightmare` `CVE 2021-34527` that enabled adversaries to perform remote code execution and privilege escalation in two different ways.

  **Answer: `CVE 2021-34527`**
  
***5. Mention the 2 adversary groups that leverage SEO to gain initial access (Format: Group1, Group2)***

- Adversaries behind both Gootkit and Yellow Cockatoo abuse search engine optimization (SEO) to display malicious content at the top of a victim’s search results.

  **Answer: `Gootkit` `Yellow Cockatoo`**

***6. In the detection rule, what should be mentioned as parent process if we are looking for execution of malicious js files [Hint: Not CMD] (Format: ParentProcessName.exe)***

- Executing script contents from within a ZIP file is unusual, especially when that script is making external network connections.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/af55aeed-67f2-43db-893c-3789c5601b01)

  **Answer: `wscript.exe`**

***7. Ransomware gangs started using affiliate model to gain initial access. Name the precursors used by affiliates of Conti ransomware group (Format: Affiliate1, Affiliate2, Afilliate3)***

- Red Canary carefully tracks affiliates of ransomware groups and the malware they use, since these adversaries are the ones who sometimes gain initial access to an environment.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/2b31826a-1239-4cf3-b237-aef532848353)

  **Answer: `Qbot` `Bazar` `IcedID`**

***8. The main target of coin miners was outdated software. Mention the 2 outdated software mentioned in the report (Format: Software1, Software2)***

- The best defense against many of the coinminer compromises we observed is patch management. Many of the coinminers we saw exploited flaws in outdated applications like `JBoss` and `WebLogic`, so keeping systems updated will deter adversaries who are simply scanning for applications with known vulnerabilities. 

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/2b31826a-1239-4cf3-b237-aef532848353)

  **Answer: `JBoss` `WebLogic`**

***9. Name the ransomware group which threatened to conduct DDoS if they didn't pay ransom (Format: GroupName)***

- An adversary known as `Fancy Lazarus` (no affiliation with Fancy Bear or Lazarus Group) extorted victims by threatening to conduct a distributed denial of service (DDoS) intrusion if they didn’t pay.

  **Answer: `Fancy Lazarus`**

***10. What is the security measure we need to enable for RDP connections in order to safeguard from ransomware attacks? (Format: XXX)***

- Internet-facing remote desktop protocol (RDP) connections without multi-factor authentication (MFA) are a common ransomware vector, making MFA for any accounts that can log in via RDP a high priority

  **Answer: `MFA`**

---

## **Additional Analysis/Artifacts**

### Useful Links

https://redcanary.com/threat-detection-report/
