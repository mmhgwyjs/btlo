# <a href="https://blueteamlabs.online/home/challenge/shiba-insider-5b48123711">Shiba Insider</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Can you uncover the insider?

**Category:** Digital Forensics

**Type:** Challenge

**Difficulty:** Easy

**Files:** `insider.pcap` `README.txt` `ssdog1.jpeg`

**Tools:** `Wireshark` `Exiftool` `CyberChef` `Steghide`

> [Wireshark](https://www.wireshark.org/) is the world's foremost network protocol analyzer. It lets you see what's happening on your network at a microscopic level.
> 
> [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.
>
> [CyberChef](https://cyberchef.org/) is a simple, intuitive web app for analysing and decoding data without having to deal with complex tools or programming languages.
>
> [Steghide](https://steghide.sourceforge.net/) is a steganography program that is able to hide data in various kinds of image- and audio-files.

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---

## **Questions and Answers:**

***1. What is the response message obtained from the PCAP file?***

- Notice the arrows under the `No.` column. They indicate a request and a response. An arrow pointing to the right signifies a request, while one pointing to the left signifies a response. More details can be found [here](https://www.wireshark.org/docs/wsug_html/#ChUsePacketListPaneSection).

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/79aedd48-966b-4f7c-91f0-48e19bca4980)

  > To check the contents of a packet, we have a couple of options. We can `right-click` and choose `Follow HTTP Stream` (blue box), or use the `Packet Details` pane (yellow box).
  
  **Answer: `use your own password`**

***2. What is the password of the ZIP file?***

- Using the same HTTP stream, we can see the `Authorization` header and it uses `Basic authentication`.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/ae8bb593-6327-403a-bec3-ff53a014cb4a)

  > For `Basic authentication`, the credentials are constructed by first combining the username and the password with a colon (username:password), and then by encoding the resulting string in base64.

- We can use the tool called `CyberChef` to decode the base64-encoded string.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/98998d56-4e0f-49aa-8bec-b4d09011bdc8)

  **Answer: `redforever`**

***3. Will more passwords be required?***

- After extracting the file using the password we obtained, we can found a `README.txt` stating that no more passwords will be needed.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/540b2dae-66ea-46fb-b942-22f6262bd2cc)

  **Answer: `No`**

***4. What is the name of a widely-used tool that can be used to obtain file information?***

- [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.

  **Answer: `exiftool`**

***5. What is the name and value of the interesting information obtained from the image file metadata?***

- Using `exiftool`, we can get the metadata of the image.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/907b7954-90b6-4d75-8da4-a684b8c6cbd3)

  > Open the command prompt, navigate to the directory where the file is located, and type the command  `exiftool` `filename`.

  **Answer: `technique.steganography`**

  > `Steganography` is the art of hiding secret data in plain sight. 

***6. Based on the answer from the previous question, what tool needs to be used to retrieve the information hidden in the file?***

- Using the same `exiftool` results.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/45fdda22-4ca6-490a-9860-9374853751e8)

  **Answer: `steghide`**

  > Steghide is a steganography program that is able to hide data in various kinds of image- and audio-files.

***7. Enter the ID retrieved.***

- To use the steghide tool, input the command `steghide` `extract` `-sf` `filename`

  > I copied the image file into the steghide directory before running the command.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/7458df55-ed3e-4077-9cdd-1e6dfb09e352)

  > No passphrase is needed, just press `Enter`.

- It will create a text file named `idInsider.txt`
 
    ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/07270503-8ef2-4357-bcd5-a1e3b21aaa9f)

  **Answer: `0726ba878ea47de571777a`**

***8. What is the profile name of the attacker?***

- This one is tricky. The ID we got from the previous question pertains to his BTLO account.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/4add5594-b3d1-46bd-ac1c-172d15686f13)

  **Answer: `bluetiger`**
  
---

## **Additional Analysis/Artifacts**

### Wireshark `insider.pcap`

> [Wireshark cheat sheet](https://www.comparitech.com/net-admin/wireshark-cheat-sheet/)

- Capture File Properties

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/fd8733e3-2f84-495c-a784-bce50ed1754f)

  > Obtaining the timeframe of the packet capture is important and can be used to cross-reference the event you are investigating.

- Protocol Hierarchy

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/62cef36e-de20-49cd-a5be-4e2bec17d8e2)

  > It lists all the protocols used within the packet capture.

- Conversations

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/c94a4876-1375-4e4c-a2d4-e008c08d04ab)

  > All communications established can be seen here. The bytes column is essential for observing how much traffic is generated between two endpoints.
  
- Export Object

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/0b023511-349c-4350-9211-a0b3342cb4a2)

  > Any files uploaded or downloaded within the packet capture timeframe will be available here for investigation and can be downloaded.


