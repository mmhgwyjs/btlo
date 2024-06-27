# <a href="https://blueteamlabs.online/home/challenge/powershell-analysis-keylogger-9f4ab9a11c">PowerShell Analysis - Keylogger</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** A suspicious PowerShell script was found on one of our endpoints. Can you work out what it does?

**Category:** Reverse Engineering

**Type:** Challenge

**Difficulty:** Easy

**File:** `HDWallpaperEngine.txt`

**Tools:** `Text Editor (Notepad++)` `PowerShell`

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. What is the SHA256 hash value for the PowerShell script file?***
- Use Powershell with the following command:
  `Get-FileHash .\HDWallpaperEngine.ps1`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/7fddd9fd-5174-4168-8a79-d52d03cc23b0)
  > Make sure that you are in the directory where the file is located.

  **Answer: `E0B7A2AD2320AC32C262AEB6FE2C6C0D75449C6E34D0D18A531157C827B9754E`**


***2. What email address is used to send and receive emails?***
- Open HDWallpaperEngine.txt in any text editor. You can change it to .ps1 to view syntax highlights, but proceed at your own risk and ensure not to execute it.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/fc686f7b-d84b-4a1f-b280-31326e79b847)

  **Answer: `chaudhariparth454@gmail.com`**
  
***3. What is the password for this email account?***
   
- Refer to the image above under the $Pass variable.
  
  **Answer: `yjghfdafsd5464562!`**
 
***4. What port is used for SMTP?***
   
- Refer to the image above under the $SMTPPort variable.
  
  **Answer: `587`**
  
  > Originally, the Simple Mail Transfer Protocol (SMTP) used port 25. Today, SMTP should instead use port 587 — this is the port for encrypted email transmissions using SMTP Secure (SMTPS).
  >
  > Reference: <a href="https://www.cloudflare.com/learning/email-security/smtp-port-25-587/">What SMTP port should be used? Port 25 or 587?</a>

***5. What DLL is imported to help record keystrokes?***

- These functions are imported from `user32.dll`:
  
  `GetAsyncKeyState` `GetKeyboardState` `MapVirtualKey` `ToUnicode`
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/52114301-4ff5-49e8-96b4-1971345e913e)

  **Answer: `user32.dll`**

  > I am not knowledgeable yet in creating a script for a keylogger, but this may be helpful for reference:
  >
  > [How to make a keylogger in PowerShell?](https://www.tarlogic.com/blog/how-to-make-keylogger-in-powershell/)

***6. What directory is the generated txt file put in?***

- It will be under %temp%.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/f6168103-19f7-4292-96e3-c9c92db49b9b)

   **Answer: `temp`**

---

## **Additional Analysis/Artifacts**

### Static Analysis

**VirusTotal:** [e0b7a2ad2320ac32c262aeb6fe2c6c0d75449c6e34d0d18a531157c827b9754e](https://www.virustotal.com/gui/file/e0b7a2ad2320ac32c262aeb6fe2c6c0d75449c6e34d0d18a531157c827b9754e/relations)

### Dynamic Analysis

***1. I ran the .ps1 script as administrator while process explorer and inetsim were running.***

  ![Screenshot 2024-06-16 011446](https://github.com/mmhgwyjs/btlo/assets/159692853/8123b480-1f07-40bd-ab3f-2af31d77fb1e)


***2. To test the keylogger, I typed in the browser, Windows Explorer, Command Prompt (cmd), Notepad, and Notepad++.***

***3. To stop the script, type `CTRL + C`.***

- **Process Monitor:**
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/27aefed2-d27c-4256-8d2e-143ac22bb78a)

- **Created file:**

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/73bc9f62-5a20-4aea-9b0c-b59dd3da5c06)

- **File Contents:**

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/35f344ab-5a86-4bc3-aa14-ca430abdee8a)

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/21fb40b5-02a0-42c5-9ac3-f2cd9d561197)

  > I tried multiple times and noticed that it stops logging after a while. I'm not sure if it will start logging again.

- **Inetsim Logs:**

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/5696b243-c0e2-41fa-83f8-a51846375ae4)
  
  > No SMTP server was configured.
