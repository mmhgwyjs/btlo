## <a href="https://blueteamlabs.online/home/challenge/powershell-analysis-keylogger-9f4ab9a11c">PowerShell Analysis - Keylogger</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** A suspicious PowerShell script was found on one of our endpoints. Can you work out what it does?

**Category:** Reverse Engineering

**Type:** Challenge

**Difficulty:** Easy

**File:** HDWallpaperEngine.txt

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you do not have it yet, you can follow this malware analysis lab guide for your setup.

**Tools:** Text Editor (Notepad++), PowerShell

---

**Questions and Answers:**

***1. What is the SHA256 hash value for the PowerShell script file?***
- Use Powershell with the following command:
  `Get-FileHash .\HDWallpaperEngine.ps1`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/7fddd9fd-5174-4168-8a79-d52d03cc23b0)
- Make sure that you are in the directory where the file is located.

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

- a
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/52114301-4ff5-49e8-96b4-1971345e913e)

  **Answer: `user32.dll`**

  > Note:

***6. What directory is the generated txt file put in?***

 - a

   ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/aefb7760-9fa8-4c6c-805d-3c35119efb7d)

   **Answer: `temp`**

---

**Additional**
