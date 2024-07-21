# <a href="https://blueteamlabs.online/home/challenge/source-7150156727">Source</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** A vulnerability was identified in a widely used product. Download the challenge attachment and review the code to identify it. Vulnerability Categories (Use this list to answer the related question. Example: Path Traversal): 1. Authentication Bypass 2. Buffer Overflow 3. Code Execution 4. Command Execution 5. Cryptographic flaw 6. Cross Origin Resource Sharing bypass 7. File Inclusion 8. Insecure Direct Object Reference 9. Insecure Deserialization 10. Path Traversal 11. Race Condition 12. Server-Side Request Forgery 13. Server-Side Template Injection 14. SQL Injection 15. XML External Entity

**Category:** Reverse Engineering

**Type:** Challenge

**Difficulty:** Medium

**File:** `zlib.c`

**Tools:** `Text Editor`

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

> I am not familiar with PHP, but let's answer the questions through research.

***1. What is the technology affected?***

- Open `zlib.c` in any text editor and let's check the header.

  ![image](https://github.com/user-attachments/assets/3d171e3b-0af6-4f4a-a2a0-57e56c9f7ec3)

  **Answer: `PHP`**

***2. Based on the list of vulnerability categories in the challenge scenario, which one describes the identified vulnerability?***

- It was identified as a `Remote Code Execution`, also known as `Command Injection` or `Command Execution`.

  > https://www.infosecinstitute.com/resources/hacking/command-execution/

  **Answer: `Command Execution`**

 ***3. See the corresponding commit. How many lines of code were added when the vulnerability was introduced?***

 - Based on research.

   ![image](https://github.com/user-attachments/assets/f42b8da7-3a40-4db4-91e9-3b360227990e)

   > https://github.com/php/php-src/commit/c730aa26bd52829a49f2ad284b181b7e82a68d7d
   
   **Answer: `11`**

 ***4. What HTTP head is required to exploit the vulnerability?***

 - It executes PHP code from within the `useragent` HTTP header, if the string starts with `zerodium`.

   > https://www.bleepingcomputer.com/news/security/phps-git-server-hacked-to-add-backdoors-to-php-source-code/

   **Answer: `User-Agent`**

---

## **Additional Analysis/Artifacts**

#### Useful Links

https://news-web.php.net/php.internals/113838
