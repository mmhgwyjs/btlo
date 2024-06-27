# <a href="https://blueteamlabs.online/home/challenge/thepackage-0a94313eab">The Package</a>

**Platform:** Blue Team Labs Online (BTLO)

**Scenario:** Authorities are looking for a hacker who is planning to sell a powerful device and the delivery is going to be in a undisclosed but crowded location. It is important to find out what product is and obtain more information about this hacker. This challenge can be solved by the use of google and it’s commands (google dorking).

**Category:** Threat Intelligence

**Type:** Challenge

**Difficulty:** Easy

**File:** `info.txt`

**Tools:** `Google Dork`

> [Google Dorking](https://hackr.io/blog/google-dorks-cheat-sheet), also known as Google hacking, is the method capable of returning the information difficult to locate through simple search queries by providing a search string that uses advanced search operators. 

---

## **Questions and Answers:**

***1. What is the name of the WiFi hacking device? (Format: Wifi X)***

- Using the keywords in the given text file, we will use `allintext:"wifi" "fruit"`.

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/a5bec4bb-e4c5-4ee6-aa0d-fe2a761bc322)

  **Answer: `Wifi Pineapple`**

***2. What is the name of the website containing the information of delivery location? (Format: WebsiteName)***

- `intext: "jllerenac"`

  ![image](https://github.com/mmhgwyjs/btlo/assets/159692853/f6e19d55-bc59-455c-9a18-1bb6d03ff806)

  **Answer: `github`**

> For questions number 3-5, I got stuck and didn't know what to do next. Then, I decided to look for the Discord channel of BTLO and discovered that this challenge is unsolvable because the original repository has been deleted.

> If you still want to complete this challenge, I found a write-up with the answers. You can check it [here](https://medium.com/@desuharshith/the-package-blue-team-labs-25178daae7ae).
  
***3. What is the name of the file containing the information of location? (Format: filename.extension)***
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Answer: `encounter.txt`**

***4. Enter the coordinates of the meeting (Format: value, -value)***

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Answer: `40.73597155853088, -73.99116596577247`**

***5. Where is the delivery going to be? (Format: Location Name)***

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Answer: `Union Square`**
  
---

## **Additional Analysis/Artifacts**

N/A
