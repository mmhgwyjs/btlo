# <a href="https://blueteamlabs.online/home/challenge/attck-0e4914db5d">ATT&CK</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** You are hired as a Blue Team member for a company. You are assigned to perform threat intelligence for the company. See how you can operationalize the MITRE ATT&CK framework to solve these scenario-based problems.

**Category:** Incident Response

**Type:** Challenge

**Difficulty:** Easy

**File:** `N/A`

**Tools:** `MITRE ATT&CK`

> [MITRE ATT&CK](https://attack.mitre.org/) is a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations.

---

## **Questions and Answers:**

This is a pretty straightforward challenge. We will simply utilize the MITRE ATT&CK framework to answer all the questions.

***1. Your company heavily relies on cloud services like Azure AD, and Office 365 publicly. What technique should you focus on mitigating, to prevent an attacker performing Discovery activities if they have obtained valid credentials? (Hint: Not using an API to interact with the cloud environment!)***

- Use the D3FEND lookup.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/e27f4c2e-3728-4fdb-8822-c764cbd1ea8c)

  **Answer: `System Daemon Monitoring`**

***2. You were analyzing a log and found uncommon data flow on port 4050. What APT group might this be?***

- From the main page, we can see the six available tactics, but we only need the first five.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/c061d7f5-62b7-458b-aa0b-9f6729c09799)

  **Answer: `harden,detect,isolate,deceive,evict`**
  
***3. The framework has a list of 9 techniques that falls under the tactic to try to get into your network. What is the tactic ID?***

- Just google it.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/913f009d-464c-44e8-a4f1-2ea93084ff92)

  > https://github.com/Intellisec-Solutions/Sentinel2D3FEND

  **Answer: `Sentinel2D3FEND`**

  
***4. A software prohibits users from accessing their account by deleting, locking the user account, changing password etc. What such software has been documented by the framework?***

- Use the D3FEND lookup.

  **Answer: `Analyzing the files accessed by a process to identify unauthorized activity.`**
  
***5. Using ‘Pass the Hash’ technique to enter and control remote systems on a network is common. How would you detect it in your company?***

- Search D3F3ND's artifacts.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/7722f4db-b24b-4b42-bc74-8ebd970e8fc5)

    **Answer: `Ephemeral digital artifact comprising a request of a local resource and any response from that resource.`**
---

## **Additional Analysis/Artifacts**

N/A
