# <a href="https://blueteamlabs.online/home/challenge/spectrum-d6ff2a32b9">Spectrum</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Scotland yard have intercepted information about one of the biggest drug deals to go down in the city of London. Someone we believe is linked to the deal was arrested. The only item they had in their possession was a USB thumb drive. Unfortunately, one of our junior analysts was unable to find anything of interest. Before we let this suspect go, we would like one of our DF experts to see if they can find anything about the deal before it goes down. Can you find out where and when the deal is expected to go down?
              Note: Once you have the coordinates, you can use https://www.gps-coordinates.net/ to view the location.

**Category:** Digital Forensics

**Type:** Challenge

**Difficulty:** Easy

**File:** `image.dd`

**Tools:** `tool1` `tool2`

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

---
## **Preparations**

To answer the provided questions, we need to complete several necessary steps.

- 

## **Questions and Answers:**

***1. What time is the meeting happening?***

- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***2. What are the supposed coordinates for the deal?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

***3. Looking into these coordinates, what is the name of this location?***
- Use this to explain:
  `good for commandlets`

  > comments

  **Answer: `answer1`**

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
 
