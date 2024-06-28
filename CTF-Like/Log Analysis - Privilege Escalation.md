# <a href="https://blueteamlabs.online/home/challenge/log-analysis-privilege-escalation-65ffe8df12">Log Analysis - Privilege Escalation</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** A server with sensitive data was accessed by an attacker and the files were posted on an underground forum. This data was only available to a privileged user, in this case the ‘root’ account. Responders say ‘www-data’ would be the logged in user if the server was remotely accessed, and this user doesn’t have access to the data. The developer stated that the server is hosting a PHP-based website and that proper filtering is in place to prevent php file uploads to gain malicious code execution. The bash history is provided to you but the recorded commands don’t appear to be related to the attack. Can you find what actually happened?

**Category:** CTF-Like

**Type:** Challenge

**Difficulty:** Easy

**File:** `bash_history`

**Tools:** `Text Editor`

---

## **Questions and Answers:**

***1. What user (other than ‘root’) is present on the server?***

- The `/home` directory contains a home folder for each user. For example, if your username is `user1`, you have a home folder located at `/home/user1`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/1da42c97-e442-43de-b4a8-10e9ac77197e)

  **Answer: `daniel`**

***2. What script did the attacker try to download to the server?***

- `Wget` is a command-line utility for downloading files from the web.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/37803e8e-2b5f-418e-8d64-680422a38f46)

  **Answer: `linux-exploit-suggester.sh`**

***3. What packet analyzer tool did the attacker try to use?***

- `Tcpdump` is a command-line utility that you can use to capture and inspect network traffic going to and from your system.

  **Answer: `tcpdump`**

***4. What file extension did the attacker use to bypass the file upload filter implemented by the developer?***

- `rm` is a command-line utility for removing files and directories. 

  > A PHTML file (PHP Web Page) is a special type of web page that combines PHP code with HTML markup. PHP (Hypertext Preprocessor) is a server-side scripting language that allows developers to create dynamic and interactive web pages.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/d6a6e028-d3c0-4079-bd48-f3a92c8ae126)

  **Answer: `phtml`**

***5. Based on the commands run by the attacker before removing the php shell, what misconfiguration was exploited in the ‘python’ binary to gain root-level access? 1- Reverse Shell ; 2- File Upload ; 3- File Write ; 4- SUID ; 5- Library load***

- `SUID` (Set owner User ID up on execution) is a special type of file permissions given to a file. SUID is defined as giving temporary permissions to a user to run a program/file with the permissions of the file owner rather that the user who runs it.

  **Answer: `4`**

---

## **Additional Analysis/Artifacts**

### Useful Links

https://linuxize.com/

https://www.linuxnix.com/suid-set-suid-linuxunix/
