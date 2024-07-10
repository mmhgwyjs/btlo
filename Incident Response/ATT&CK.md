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

- Use the MITRE ATT&CK framework. 

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/f0364e06-6dc5-4f47-8a62-cd4ebfe3de7b)

  > Take note of the keywords mentioned in the question.

  **Answer: `T1538`**

***2. You were analyzing a log and found uncommon data flow on port 4050. What APT group might this be?***

- We can use the search button. Let's apply your research skills.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/fa6ad2a9-9491-4839-8e4a-3cffb9ffe583)

  **Answer: `G0099`**
  
***3. The framework has a list of 9 techniques that falls under the tactic to try to get into your network. What is the tactic ID?***

- "Let's go with those research skills again.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/81b9bb6d-f8e5-4d95-b697-e2fdf509048d)

  **Answer: `TA0001`**
  
***4. A software prohibits users from accessing their account by deleting, locking the user account, changing password etc. What such software has been documented by the framework?***

- Tip: Use `google dorking`. 

  **Answer: `S0372`**
  
***5. Using ‘Pass the Hash’ technique to enter and control remote systems on a network is common. How would you detect it in your company?***

- Let's apply your research skills.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/ae6fad05-cf1f-41f6-b077-d68240b94e3b)

    **Answer: `Monitor newly created logons and credentials used in events and review for discrepancies.`**
---

## **Additional Analysis/Artifacts**

N/A
