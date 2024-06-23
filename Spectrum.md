# <a href="https://blueteamlabs.online/home/challenge/spectrum-d6ff2a32b9">Spectrum</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Scotland yard have intercepted information about one of the biggest drug deals to go down in the city of London. Someone we believe is linked to the deal was arrested. The only item they had in their possession was a USB thumb drive. Unfortunately, one of our junior analysts was unable to find anything of interest. Before we let this suspect go, we would like one of our DF experts to see if they can find anything about the deal before it goes down. Can you find out where and when the deal is expected to go down? Note: Once you have the coordinates, you can use https://www.gps-coordinates.net/ to view the location.

**Category:** Digital Forensics

**Type:** Challenge

**Difficulty:** Easy

**File:** `image.dd`

**Tools:** `Photorec` `Exiftool` `Steghide` `Fcrackzip` `CyberChef` `Audacity`

> [PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec) is file data recovery software designed to recover lost files including video, documents and archives from hard disks, CD-ROMs, and lost pictures from     digital camera memory.
>
> [ExifTool](https://exiftool.org/) is a platform-independent Perl library plus a command-line application for reading, writing and editing meta information in a wide variety of files.
>
> [Steghide](https://steghide.sourceforge.net/) is a steganography program that is able to hide data in various kinds of image- and audio-files.
>
> [Fcrackzip](https://www.kali.org/tools/fcrackzip/) is a fast password cracker partly written in assembler. It is able to crack password protected zip files with brute force or dictionary based attacks, optionally testing with unzip its results.
>
> [CyberChef](https://cyberchef.org/) is a simple, intuitive web app for analysing and decoding data without having to deal with complex tools or programming languages.
>
> [Audacity](https://www.audacityteam.org/FAQ/) is the world’s most popular free software for recording and editing audio.

---
## **Preparations**

To answer the provided questions, we need to complete several necessary steps. For this challenge, we will use Kali Linux. If you have not set it up yet, you can refer to the instructions [here](https://github.com/mmhgwyjs/pentest-lab/blob/main/README.md).

- Since the given file is an disk image file (.dd), we will use `photorec` to analyze the disk image. We chose `photorec` because it is included in the tags for this challenge, although there are other tools available for analyzing disk images.

- Use the command `photorec image.dd`. 

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/3ffa4755-a788-4d98-9e59-1f2ab381a312)

- Once done, it should create a directory called `recup_dir.1`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/e2c46d66-2736-4019-a937-ecc9a851df8d)

- Let's check all the image files using `exiftool`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a9efcc72-e0a5-42a1-8c07-ef942881ccab)

  > The name of the challenge is `Spectrum`, but it is not the answer on the given question. Let's set that aside for now.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/09b1e74f-8038-4e6c-a023-e7b28d3fd600)
 
  > It mentioned `steghide`. It is a tool used to hide data in various types of image and audio files.
  
 - To use steghide, use the command `steghide extract -sf filename` to extract any embedded data or files.

   ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/b49f825e-5eb6-4e5c-972b-6e449dbcb847)

   > I tried using it on all the image files, but had no success.

- The password we have is not working for the `f0000240_brown.zip` file either.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/9e3feded-eae4-4882-b3b4-7ee2f5592fce)

- We are stuck now, but luckily BTLO provides the tools that we can use for each challenge, so we can use them as clues. Personally, I am not familiar with all the available tools.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/6a1a837a-d54e-4da2-9e4b-17f7638ed2c3)

  > So far, we haven't used the tool called `fcrackzip`. It is capable of cracking password-protected ZIP files using brute-force or dictionary-based attacks.
  
- We will use the command `fcrackzip -uDp /usr/share/wordlists/rockyou.txt f0000240_brown.zip`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/e85deb3f-ba85-4aaf-ae4f-d864e37c9518)

  > I did some trial and error on this one and found that Kali has a wordlist called `rockyou.txt`, which contains many passwords that we can utilize for our brute force attempts.

- Now that we have the password, we can proceed to unzip the f0000240_brown.zip file.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/3cc68c27-27aa-4538-935d-5cf8ce54f5ed)

- Let's try using steghide on these newly extracted audio files.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/d8941b42-08f7-41f5-92a8-29b75eb2f15f)

  > Remember that we have the `steghide` password from earlier, which is `cheese on toast`.

- Open the extracted text file `stardate.txt`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/dffc1b6e-b041-4d2c-93db-38ff9dafe264)

  > It shows `56inrkS7AcAXatqrFM`, which appears to be encoded.

- We will use `CyberChef` to decode this. Through trial and error, we found out that it is encoded in Base58.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/bbc72558-890c-407f-8f4b-4156106f9683)

#### ***I guess that's all we need to answer the questions below.***
  
## **Questions and Answers:**

***1. What time is the meeting happening?***

- Based on what we decoded earlier, we can see that it's in a time format, but the word `time` is reversed. It seems to be a clue, so let's try reversing our time as well.

  **Answer: `00:10:51`**

***2. What are the supposed coordinates for the deal?***

- And we're stuck again. However, upon checking the challenge's tags again, we noticed `Audio Software`. I guess we need to check the audio files we have.

  > Upon doing some research, we found that `Audacity` is one of the recommended tools for Kali. You can explore alternative tools [here](https://itsfoss.com/best-audio-editors-linux/).
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/050fc3a6-ae3a-4a56-8568-435aa844fa85)

- The `location.wav` produces a Morse code-like sound, but upon conversion, it doesn't seem to provide relevant results. All the other audio files produce garbled sound.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/89cce454-23bb-431a-87b2-8d2113e676a9)

  > We're stuck again.
  
- And then we recall the `exiftool` results from `f0047516.jpg`, where we noted that the `location` is `name of the challenge` which we can identify as `Spectrum`. Let's use that as our clue.
  
- We can google `audacity + spectrum` and the first result we can found is about [Spectral analysis](https://support.audacityteam.org/audio-analysis/spectral-analysis).

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/91c0802b-5f9a-4375-b409-a3a111d5e261)

- Based on that documentation, there's a functionality called `Spectrogram` view and that will lead us to the coordinates we need. 

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/ffa522e1-f839-47b5-bcf5-4e52f74b0bd7)

  > I tried all the audio files, and we found the needed answer from `white.wav`.

  **Answer: `51.505278`, `0.055278`**

***3. Looking into these coordinates, what is the name of this location?***

- Referencing back to the note in the scenario, we will use `https://www.gps-coordinates.net/` to check the coordinates.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/14583718-6af7-4e8e-9230-83356f66835d)

  **Answer: `London City Airport`**

---

## **Additional Analysis/Artifacts**

### Mounting an image in Windows

> There are multiple tools available to mount a disk image, but I chose to use the [Arsenal Mount Imager](https://arsenalrecon.com/products/arsenal-image-mounter).

- To mount an image, select `Mount disk image`.
  
  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/3c90d1aa-af7a-40f8-b6f6-2b83f76ebe5b)

- I use the following mounting options.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/aa5262de-84df-44eb-8770-bf6ee248a871)

  > I select `Create removable disk device` because it doesn't work if I don't, though I'm not sure why.

 - It will then create a removable disk drive that we can use for investigation.

   ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/25c3142c-c7a9-4c8a-ab13-e23b62f798a6)
 
