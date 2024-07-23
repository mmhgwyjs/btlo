# <a href="https://blueteamlabs.online/home/challenge/employee-of-the-year-df16bc36f3">Employee of the Year</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** John received the 'Best Employee of the Year' award for his hard work at FakeCompany Ltd. Unfortunately, today John deleted some important files (typical John!). It’s your job to recover the deleted files and capture all the flags contained within!

**Category:** CTF-Like

**Type:** Challenge

**Difficulty:** Easy

**File:** `recoverfiles.dd`

**Tools:** `Photorec` `Exiftool` `CyberChef` `TestDisk`

> [PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec) is file data recovery software designed to recover lost files including video, documents and archives from hard disks, CD-ROMs, and lost pictures from     digital camera memory.
>
> [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.
>
> [CyberChef](https://cyberchef.org/) is a simple, intuitive web app for analysing and decoding data without having to deal with complex tools or programming languages.
>
> [TestDisk](https://www.cgsecurity.org/testdisk_doc/) can be used to recover lost partitions, fix boot sectors, and recover files from damaged or deleted file systems. 

**Note:** For this walkthrough, I have spun up a Kali Linux virtual machine to utilize its tools. If you haven't set it up yet, I highly suggest following this [pentest lab](https://github.com/mmhgwyjs/pentest-lab) guide for your setup.

---

## **Preparations**

To answer the questions, we'll use Kali Linux. If you haven't set it up yet, check out the instructions [here](https://github.com/mmhgwyjs/pentest-lab/blob/main/README.md).

- Since the file provided is a disk image with a `.dd` extension, we'll use `photorec` to analyze it.

  ![image](https://github.com/user-attachments/assets/bd9a31e3-95aa-4d19-881c-33b9988d8a4b)

  > `photorec filename`
  
- It should create a directory.

  ![image](https://github.com/user-attachments/assets/e2c18b99-a558-444d-85e4-22ba5b75aedb)

  ![image](https://github.com/user-attachments/assets/8ba3f311-95c5-4595-82ec-0bfc4b8cdcc7)

## **Questions and Answers**

***1. What is the text written on the recovered gif image?***

- Since there's only one `GIF` among the extracted files, we can simply use the command `display filename` to view it.

  ![image](https://github.com/user-attachments/assets/b7b9ab11-7a95-4b4d-afde-ae0781fe5ad8)

  ![image](https://github.com/user-attachments/assets/71977a62-e431-40b5-a8b8-59502de9863a)

  **Answer: `GoodJobDefender`**

***2. Submit Flag1.***

- Open the `f0017848.png` file.

  ![image](https://github.com/user-attachments/assets/1f65ff6b-ccdc-44f7-a460-74b9acf8d3c1)

  > `display filename`

  ![image](https://github.com/user-attachments/assets/4ab6019d-507a-4f34-861a-bc25c0b04bc9)

  **Answer: `FLAG1:WELOVEBTLO`**

***3. Submit Flag2.***

- Microsoft Office documents can be considered as ZIP files that we can extract.

  ![image](https://github.com/user-attachments/assets/329a8d0d-1d97-46f4-86fa-c1808a57f764)

- We can view the XML files using the `cat` command, but they are not very user-friendly to read.

  ![image](https://github.com/user-attachments/assets/f95eca8c-65ce-47fe-bada-97118fc52e69)

 - Let's use the command `xmllint` to view it better.
 
   ![image](https://github.com/user-attachments/assets/78477157-8864-4409-969a-823f067cce2f)

   > I used the `tail` command to view the last lines for a better representation, but I ended up skimming through the entire XML file to find what we are looking for.

- We'll use `CyberChef` to decode the base64 string `RkxBRzI6QVNPTElEREVGRU5ERVI=`.

  ![image](https://github.com/user-attachments/assets/9ef7735f-5e9a-40fe-979a-c58db2176526)

- We can also decode it in `Kali` using the command `echo "string" | base64 -d`

  ![image](https://github.com/user-attachments/assets/bb5cf642-9dfc-4c9d-8e10-1e666ce3ea40)
  
  **Answer: `FLAG2:ASOLIDDEFENDER`**

***4. Submit Flag3.***

- Using `exiftool` on `f0009040.pdf`.

  ![image](https://github.com/user-attachments/assets/314fd354-84cb-436f-a6c9-805a2c238797)

  > FLAG3%3A%40BLU3T3AM%240LDI3R

- It appears to be encoded, so let's decode it using `CyberChef`.

  ![image](https://github.com/user-attachments/assets/ed76c688-a227-4151-a0a6-d601b3561b5f)

  > Use `URL Decode` as the recipe.

  **Answer: `FLAG3:@BLU3T3AM$0LDI3R`**

***5. What is the filesystem of the provided disk image?***

- Let's use the tool called `testdisk`. Although there are multiple tools available to obtain the answer, such as `parted` and `fdisk`, we will use `testdisk` for this.
  
  ![image](https://github.com/user-attachments/assets/2d972919-9bb9-4867-9531-d177e082b734)

  > https://www.geeksforgeeks.org/file-systems-in-operating-system/

  **Answer: `ext4`**

***6. What is the original filename of the recovered mp4 file?***

- We can use the `strings` command to examine the raw `dd` file.

  ![image](https://github.com/user-attachments/assets/d1249802-c42b-479f-a77d-6623f651835e)

  > We can also see some clues for flags 1-3. I guess this should be our first step!

  **Answer: `SBTCertifications.mp4`**

---

## **Additional Analysis/Artifacts**

N/A
