# networkWalks-B082-week3-password-cracking_JTR_NetworkWalksTools

<div align="center">

  **# 🔐 Cybersecurity Lab Report: Password Cracking with JTR & Networkwalks Tools**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/JTR%20-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Password%20Cracking-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Mishal%20Haider%20-C00000?style=flat-square" />
</p>


---

## 1. Purpose of Lab
The primary objective of this hands-on lab is to demonstrate practical password recovery and hash cracking methodologies applied to password-protected PDF documents. The lab explores two distinct workflows:
1. **Offline Hash Cracking (Module 1):** Extracting document hashes using online/offline utilities and performing local brute-force/dictionary attacks using **John the Ripper (JTR)** and its graphical front-end **Johnny** on a Windows environment.
2. **Web-Based Hash & Password Cracking (Module 2):** Utilizing specialized **Networkwalks Tools** (Hash Calculator & Password Cracker) to extract hash signatures and recover cleartext passwords directly through web interfaces.

---

## 2. Step-by-Step Process of Both Modules

### Module 1: Password Cracking with JTR & Johnny

#### **Step 1: Environment & Tool Setup**
1. Downloaded the latest release of **John the Ripper (JTR)** for Windows.
2. Downloaded and installed **Johnny** (the GUI wrapper for John the Ripper).
3. Launched Johnny with **Administrator privileges** (`Run as administrator`).
4. Configured Johnny's settings by setting the executable path pointing to the installed `john.exe` binary.

#### **Step 2: PDF File Acquisition & Hash Extraction**
1. Downloaded the target locked files: `My Locked PDF1.pdf`, `My Locked PDF2.pdf`, and `My Locked PDF3.pdf`.
2. Opened the online PDF Hash Extractor tool (`onlinehashcrack.com`).
3. Uploaded `My Locked PDF1.pdf` to extract its raw cryptographic password hash string (e.g., `$pdf$1*...`).
4. Copied the extracted hash output into a plain text file (`hash1.txt`) using Notepad and saved it locally.
5. Repeated the hash extraction process for `My Locked PDF2.pdf` and `My Locked PDF3.pdf`, saving their respective hash values into `hash2.txt` and `hash3.txt`.

#### **Step 3: Executing Hash Attack in Johnny**
1. Opened the Johnny GUI interface.
2. Clicked **Open Passwd File** / **Import** and loaded the saved `.txt` hash file (e.g., `hash1.txt`).
3. Selected the appropriate attack mode (Default / Dictionary / Brute-force).
4. Clicked **Start Attack** to initiate local multi-threaded cracking via JTR.
5. Monitored the console output until the cleartext password was successfully cracked and displayed in Johnny's session log.

#### **Step 4: Verification & Unlocking**
1. Copied the recovered plaintext password.
2. Opened `My Locked PDF1.pdf` using Adobe Acrobat / Web Browser.
3. Entered the recovered password to successfully unlock and view the PDF contents.
4. Repeated Steps 3–4 for `My Locked PDF2.pdf` and `My Locked PDF3.pdf`.

---

### Module 2: Password Cracking with Networkwalks Tools

#### **Step 1: Hash Calculation**
1. Navigated to the **Networkwalks Hash Calculator** web application (`networkwalks.com/hash-calculator/`).
2. Uploaded the target file `My Locked PDF1.pdf`.
3. The tool processed the file header and calculated/extracted the corresponding document hash string.
4. Copied the generated hash string to the clipboard.

#### **Step 2: Web-Based Password Recovery**
1. Opened the **Networkwalks Password Cracker** tool interface.
2. Pasted the previously calculated PDF hash into the input field.
3. Initiated the decryption/crack action.
4. Retained the recovered cleartext password displayed on screen.

#### **Step 3: Verification**
1. Opened `My Locked PDF1.pdf` on the local Windows PC.
2. Inputted the cracked password provided by Networkwalks Password Cracker.
3. Confirmed full access to the target document.

---

## 3. Tools and Links

| Tool / Resource | Purpose / Functionality | Link / Reference |
| :--- | :--- | :--- |
| **John the Ripper (JTR)** | Core open-source offline password security auditing and hash cracking tool. | [Openwall JTR](https://www.openwall.com/john/) |
| **Johnny** | GUI front-end for John the Ripper to streamline session management. | [Openwall Johnny](https://www.openwall.com/johnny/) |
| **Online Hash Crack** | Online utility to extract password hashes from PDF documents. | [Online PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) |
| **Networkwalks Hash Calculator** | Web tool for calculating and extracting file hashes. | [Networkwalks Hash Calculator](https://networkwalks.com/hash-calculator/) |
| **Networkwalks Password Cracker** | Dedicated web application for cracking extracted security hashes. | Networkwalks Academy Portal |

---

## 4. What I Learned

1. **Hash Extraction vs. Password Cracking:** PDF encryption does not store plain text passwords; it relies on hash verification. Modern attacks isolate the document's hash header first, allowing offline processing without locking or modifying the original file.
2. **Offline Attack Speed & Flexibility:** Using local command-line / GUI tools like JTR & Johnny provides complete control over attack modes (wordlists, rules, mask attacks) and leverages CPU/GPU hardware efficiency.
3. **GUI Wrappers for Security Tools:** Graphical wrappers like Johnny simplify session handling, hash importing, and progress monitoring without losing the raw power of JTR's underlying execution engine.
4. **Impact of Password Complexity:** Weak passwords on standard PDF encryption algorithms can be recovered quickly using dictionary or rule-based attacks.
5. **Mitigation Strategies:** To prevent successful hash cracking attacks, organizations must enforce long, complex passphrase policies and adopt robust encryption schemes (such as AES-256 with strong key derivation functions).

---
## 5. Problem faced
It kept making the font red , showing that the path is incorrect.

<img width="425" height="270" alt="Screenshot 2026-08-24 165631" src="https://github.com/user-attachments/assets/d47090ed-2e12-4a52-b6c1-2e90bac63c80" />

**Solution**
It was only because Johnny wasn't opened in the administrative mode.

<img width="442" height="350" alt="Screenshot 2026-08-24 200541" src="https://github.com/user-attachments/assets/92f3666f-e670-40c4-bb49-7e130455a4db" />


---

## 6. Liability Disclaimer

> **DISCLAIMER:**  
> This document and the activities described herein are intended strictly for **educational, academic, and authorized defensive testing purposes**. All testing was executed in a controlled laboratory environment on test files provided explicitly for this learning module.  
> 
> Unauthorized access, cracking, or unauthorized attempts to bypass security controls on files, systems, or data without explicit written consent from the owner is strictly prohibited and illegal under computer crime legislation. The author and affiliated institutions accept no responsibility or liability for misuse or illegal application of the information contained in this report.

---


# 👤 Author

**Mishal Haider**\

Cybersecurity Professional 

LinkedIn: [www.linkedin.com/in/mishal-haider-9b750b37a)

---

# 👤 Mentor

**Waqas Karim CCIE**\

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 03 | **Project:** Cybersecurity & Password Cracking Lab | **Repository:** GitHub

