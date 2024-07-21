# <a href="https://blueteamlabs.online/home/challenge/bruteforce-16629bf9a2">Bruteforce</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Can you analyze logs from an attempted RDP bruteforce attack? One of our system administrators identified a large number of Audit Failure events in the Windows Security Event log. There are a number of different ways to approach the analysis of these logs! Consider the suggested tools, but there are many others out there!

**Category:** Incident Response

**Type:** Challenge

**Difficulty:** Medium

**Files:** `BTLO_Bruteforce_Challenge.csv` `BTLO_Bruteforce_Challenge.evtx` `BTLO_Bruteforce_Challenge.txt`

**Tools:** `Timeline Explorer` `Hayabusa` `Windows Event Viewer` `VirusTotal`

> [Timeline Explorer](https://www.sans.org/tools/timeline-explorer/) is a tool used to view CSV and Excel files, filter, group, sort, etc. with ease.
>
> [Hayabusa](https://github.com/Yamato-Security/hayabusa/blob/main/README.md) is a Windows event log fast forensics timeline generator and threat hunting tool created by the `Yamato Security` group in Japan.
>
> [Windows Event Viewer](https://www.howtogeek.com/123646/htg-explains-what-the-windows-event-viewer-is-and-how-you-can-use-it/) shows a log of application and system messages, including errors, information messages, and warnings.
>
> [VirusTotal](https://www.virustotal.com/gui/home/upload) is a tool that inspects items with over 70 antivirus scanners and URL/domain blocklisting services, in addition to a myriad of tools to extract signals from the studied content.

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. How many Audit Failure events are there? (Format: Count of Events)***

- Open `BTLO_Bruteforce_Challenge.csv`. I use `Timeline Explorer` because it is much easier for me to use than Excel.

  ![image](https://github.com/user-attachments/assets/3aa187c8-7c86-4911-b90c-691f0fdb6049)

  **Answer: `3103`**

***2. What is the username of the local account that is being targeted? (Format: Username)***

- There are multiple ways to check the logs, but here we'll use a tool called `Hayabusa`, which is particularly effective for handling a large number of event logs.

  ![image](https://github.com/user-attachments/assets/e3f85593-b904-4321-ac7b-397feb0e7103)

  > `hayabusa-2.11.0-win-x64.exe logon-summary -d C:\Users\flrvm2\Documents\BTLO\Bruteforce -U -o bruteforce_haya.csv`
  > - Use the `logon-summary` command to output a summary of logon information;
  > - `-d` means directory;
  > - `-U` means the output time will be in UTC format;
  > - `-o` means the output file will be in CSV format;
  
- Next, we'll open the output file in `Timeline Explorer`.

  ![image](https://github.com/user-attachments/assets/c2ecba8e-12b6-4a7b-b06b-418d86951f37)

  > If you are using a Windows machine, we can use the `Windows Event Viewer` to view the event by simply double-clicking it.
  >
  > ![image](https://github.com/user-attachments/assets/fc4f82ac-f0b5-4829-9147-25fe1b4b2163)

  **Answer: `administrator`**

 ***3. What is the failure reason related to the Audit Failure logs? (Format: String)***

 - Using `Event Viewer`.

   ![image](https://github.com/user-attachments/assets/383ab991-7a72-4de8-8f11-82e550f62577)

   **Answer: `Unknown user name or bad password.`**

 ***4. What is the Windows Event ID associated with these logon failures? (Format: ID)***

 - Still using `Event Viewer`.

   ![image](https://github.com/user-attachments/assets/9471825e-f51e-4076-b0c5-3d7ec1eac031)

   **Answer: `4625`**

 ***5. What is the source IP conducting this attack? (Format: X.X.X.X)***

  - Using `Event Viewer`, go to `Details` tab and expand the `EventData` section.

    ![image](https://github.com/user-attachments/assets/e67cf82c-197b-44a0-95d0-c0a54956193e)

  - We can also use the output file we got earlier from `Hayabusa`.

    ![image](https://github.com/user-attachments/assets/ed59bc93-ecfe-4cd6-9d05-44a0d024b5be)

   **Answer: `113.161.192.227`**

 ***6. What country is this IP address associated with? (Format: Country)***

 - Let's use `VirusTotal` to check the location of our IP address.

   ![image](https://github.com/user-attachments/assets/8051d0c6-adad-48e2-b9ac-4457bd4c70fc)

   **Answer: `Vietnam`**

 ***7. What is the range of source ports that were used by the attacker to make these login requests? (LowestPort-HighestPort - Ex: 100-541)***

  - Open the `BTLO_Bruteforce_Challenge.txt`. You can still use `Timeline Explorer` even for text files, but it's up to you to decide which method you find easier for analyzing a text file.

   ![image](https://github.com/user-attachments/assets/abb6d707-2e5a-4d28-959d-e5b2d95e93d8)

   > I used the filter as shown to view all ports available.

   **Answer: `49162-65534`**

---

## **Additional Analysis/Artifacts**

N/A
