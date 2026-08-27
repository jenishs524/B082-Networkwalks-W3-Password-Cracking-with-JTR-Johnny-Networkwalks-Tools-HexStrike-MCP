# B082 - Networkwalks W3 - Password Cracking with John the Ripper, Johnny, Networkwalks Tools & HexStrike MCP

---

| **Batch** | B082 |
| :--- | :--- |
| **Intern Name** | Jenik Shrestha |
| **Program** | Cybersecurity Training at Networkwalks Academy |
| **Date** | 27 August 2026 |
| **Modules** | W3-PM1 | W3-PM2 | W3-PM-FINAL |

---

## 📌 Table of Contents

1. [Project Overview](#-project-overview)
2. [Tools Used](#-tools-used)
3. [Module 1: JTR John + Johnny (W3-PM1)](#-module-1-jtr-john--johnny-w3-pm1)
4. [Module 2: Networkwalks Tools (W3-PM2)](#-module-2-networkwalks-tools-w3-pm2)
5. [Module 3: AI-Assisted Cracking (W3-PM-FINAL)](#-module-3-ai-assisted-cracking-with-hexstrike-mcp--claude-desktop-w3-pm-final)
6. [Summary of Results](#-summary-of-results)
7. [Flags Captured](#-flags-captured)
8. [Key Learnings](#-key-learnings)
9. [Conclusion](#-conclusion)

---

## 📌 Project Overview

This project covers three password cracking lab modules completed during Week 3 of the Cybersecurity Training program at **Networkwalks Academy**.

| Module | Title | Tool/Method |
| :--- | :--- | :--- |
| **W3-PM1** | Password Cracking with JTR | JTR John (Terminal) + Johnny (GUI) |
| **W3-PM2** | Password Cracking with Networkwalks Tools | Hash Calculator + Password Cracker (Online) |
| **W3-PM-FINAL** | AI-Assisted Password Cracking | HexStrike MCP + Claude Desktop + JTR |

### Target Files

| File | Source |
| :--- | :--- |
| My Locked PDF1.pdf | Main lab target |
| My Locked PDF2.pdf | Trainer provided |
| My Locked PDF3.pdf | Trainer provided |
| networkwalks_flag1.pdf | AI Module target |

---

## 📌 Tools Used

| Tool | Purpose |
| :--- | :--- |
| **Kali Linux** | Operating system used for all activities |
| **John the Ripper (JTR)** | Terminal-based password cracking tool |
| **Johnny** | Graphical user interface for JTR |
| **pdf2john.pl / pdf2john** | Extract crackable hashes from PDF files |
| **rockyou.txt** | Default wordlist in Kali Linux |
| **Networkwalks Hash Calculator** | Online tool to extract PDF hashes |
| **Networkwalks Password Cracker** | Online tool for dictionary attacks |
| **HexStrike MCP Server** | AI-powered MCP server |
| **Claude Desktop** | AI assistant interface |
| **JTR_default_password.txt** | Custom wordlist (3,546 words) |

---

## 📌 Module 1: JTR John + Johnny (W3-PM1)

### Task

Crack the password of `My Locked PDF1.pdf` using **JTR John (Terminal)** and **Johnny (GUI)**.

---

### Step 1: Locate the Target PDF File

The target file `My Locked PDF1.pdf` was located in the Downloads folder.

![Lock PDF](evidences/module-1/1-lock-pdf.png)

**Figure 1:** Target PDF file in Downloads folder.

---

### Step 2: Extract the Hash

The hash was extracted using `pdf2john.pl`:

```bash
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt
```

![Hash Extraction](evidences/module-1/2-hash-extraction.png)

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

![Hash Displayed](evidences/module-1/3-hash-displayed.png)

**Figure 3:** Extracted hash displayed.

---

### Step 4: Crack with John the Ripper

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt
```

**Output:**
```
good-luck        (My Locked PDF1.pdf)
1g 0:00:00:10 DONE (2026-08-26 22:34)
```

![JTR Cracking](evidences/module-1/4-jtr-cracking.png)

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

![Cracked Password](evidences/module-1/5-cracked-password.png)

**Figure 5:** Cracked password displayed as `good-luck`.

---

### Step 6: Crack with Johnny (GUI)

Johnny GUI was opened and the hash was loaded. The attack was started and the password was displayed.

![Johnny GUI](evidences/module-1/6-johnny-gui.png)

**Figure 6:** Johnny GUI cracking the password.

---

### Step 7: Verify the Password

The PDF was opened using `good-luck`.

![PDF Opened](evidences/module-1/7-pdf-opened.png)

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

Crack the password of `My Locked PDF1.pdf` using **Networkwalks Hash Calculator** and **Password Cracker**.

---

### Step 1: Open Hash Calculator

* **URL:** https://networkwalks.com/hash-calculator/

![Hash Calculator](evidences/module-2/1-hash-calculator.png)

**Figure 8:** Networkwalks Hash Calculator opened.

---

### Step 2: Select PDF Tab and Upload File

The PDF tab was selected and `My Locked PDF1.pdf` was uploaded.

![Hash Extracted](evidences/module-2/2-hash-extracted.png)

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

![Password Cracker](evidences/module-2/3-password-cracker.png)

**Figure 10:** Networkwalks Password Cracker opened.

---

### Step 5: Upload Wordlist and Start Attack

The custom wordlist `JTR_default_password.txt` (3,546 words) was uploaded and the attack was started.

![Attack Running](evidences/module-2/4-attack-running.png)

**Figure 11:** Dictionary attack in progress.

---

### Step 6: Password Cracked

**PASSWORD: `good-luck`**

![Password Cracked](evidences/module-2/5-password-cracked.png)

**Figure 12:** Password `good-luck` successfully cracked.

---

### Step 7: Verify the Password

The PDF was opened using `good-luck`.

![PDF Opened](evidences/module-2/6-pdf-opened.png)

**Figure 13:** PDF successfully unlocked.

---

### Results – Module 2

| Item | Details |
| :--- | :--- |
| **Target File** | My Locked PDF1.pdf |
| **Cracked Password** | **good-luck** |
| **Tool Used** | Networkwalks Hash Calculator & Password Cracker |
| **Wordlist Used** | JTR_default_password.txt (3,546 words) |
| **Time Taken** | ~5 seconds |

---

## 📌 Module 3: AI-Assisted Cracking with HexStrike MCP + Claude Desktop (W3-PM-FINAL)

### Task

Setup HexStrike MCP Server with Claude Desktop and crack `networkwalks_flag1.pdf` using AI assistance.

---

### Part A: HexStrike MCP Server Setup

#### Step 1: Install Claude Desktop

```bash
# Add GPG key
curl -fsSL https://pkg.claude-desktop-debian.dev/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/claude-desktop.gpg

# Add repository
echo "deb [signed-by=/usr/share/keyrings/claude-desktop.gpg arch=amd64,arm64] https://pkg.claude-desktop-debian.dev stable main" | sudo tee /etc/apt/sources.list.d/claude-desktop.list

# Update and install
sudo apt update
sudo apt install claude-desktop
```

![Claude Desktop Installed](evidences/module-3/1-claude-installed.png)

**Figure 14:** Claude Desktop installed.

---

#### Step 2: Clone HexStrike Repository

```bash
git clone https://github.com/0x4m4/hexstrike-ai.git
cd hexstrike-ai
```

![HexStrike Cloned](evidences/module-3/2-hexstrike-cloned.png)

**Figure 15:** HexStrike repository cloned.

---

#### Step 3: Create Virtual Environment

```bash
python3 -m venv hexstrike-env
source hexstrike-env/bin/activate
```

![Virtual Environment](evidences/module-3/3-virtual-env.png)

**Figure 16:** Virtual environment created.

---

#### Step 4: Install Python Dependencies

```bash
pip3 install -r requirements.txt
```

![Pip List](evidences/module-3/4-pip-list.png)

**Figure 17:** Python dependencies installed.

---

#### Step 5: Configure MCP Server

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

![Claude JSON](evidences/module-3/5-claude-json.png)

**Figure 18:** MCP Server configured.

---

#### Step 6: Run the Server

```bash
cd ~/Downloads/hexstrike-ai
source hexstrike-env/bin/activate
python3 hexstrike_mcp.py --server http://localhost:8888
```

**Output:**
```
[🔥 HexStrike MCP] ✅ 🚀 Starting HexStrike AI MCP Client v6.0
[🔥 HexStrike MCP] ✅ 🎯 Successfully connected to HexStrike AI API Server
[🔥 HexStrike MCP] ✅ 🏥 Server health status: healthy
[🔥 HexStrike MCP] ✅ 🤖 Ready to serve AI agents with enhanced cybersecurity capabilities
```

![HexStrike Running](evidences/module-3/6-hexstrike-running.png)

**Figure 19:** HexStrike MCP Server running.

---

### Part B: AI-Assisted Password Cracking

#### Step 1: Download Target PDF

`networkwalks_flag1.pdf` was downloaded and placed on Desktop.

![Target PDF](evidences/module-3/7-target-pdf.png)

**Figure 20:** Target PDF on Desktop.

---

#### Step 2: AI Prompt 1 – Check JTR Installation

**Prompt:**
```
Check if John the Ripper is installed in this Hexstrike MCP and show me its version
```

**Response:**
```
John the Ripper is installed on the HexStrike server, at /usr/sbin/john.

Version: 1.9.0-jumbo-1+bleeding-aec1328d6c (built 2021-11-02)
```

![AI Prompt 1](evidences/module-3/8-ai-prompt-1.png)

**Figure 21:** AI confirms JTR is installed.

---

#### Step 3: AI Prompt 2 – Calculate PDF Hash

**Prompt:**
```
Please calculate the hash value of this PDF file: /home/jenishkali/Desktop/networkwalks_flag1.pdf
```

**Response:**
```
SHA256: f569ce5208a64b0f73f5a98f2187eafcd8282641fb27afa0c1a30d83b67ef06
MD5: 7fe04d052b19879aaa9fcac0b5dce138
```

![AI Prompt 2](evidences/module-3/9-ai-prompt-2.png)

**Figure 22:** AI calculates hash.

---

#### Step 4: AI Prompt 3 – Crack the Password

**Prompt:**
```
Please use JTR tool in this hexstrike MCP server to crack the password of this PDF file. Use the rockyou.txt wordlist dictionary.
```

**Response:**
```
Cracked it instantly.

PDF password: password1

John found it in the rockyou.txt wordlist on the first pass.
```

![AI Prompt 3](evidences/module-3/10-ai-prompt-3.png)

**Figure 23:** AI cracks password as `password1`.

---

#### Step 5: Verify the Password

The PDF was opened using `password1`.

![PDF Opened](evidences/module-3/11-pdf-opened.png)

**Figure 24:** PDF successfully unlocked.

---

### Results – Module 3

| Item | Details |
| :--- | :--- |
| **Target File** | networkwalks_flag1.pdf |
| **Cracked Password** | **password1** |
| **Tool Used** | HexStrike MCP + Claude Desktop + JTR |
| **Method** | AI-Assisted Password Cracking |
| **Wordlist Used** | rockyou.txt |

---

## 📌 Summary of Results

| # | File Name | Cracked Password | Method Used |
| :--- | :--- | :--- | :--- |
| 1 | My Locked PDF1.pdf | **good-luck** | JTR John + Johnny (Terminal & GUI) |
| 2 | My Locked PDF1.pdf | **good-luck** | Networkwalks Tools (Online) |
| 3 | My Locked PDF2.pdf | **1qaz2wsx** | Networkwalks Tools (Online) |
| 4 | My Locked PDF3.pdf | **password1** | Networkwalks Tools (Online) |
| 5 | networkwalks_flag1.pdf | **password1** | HexStrike MCP + AI (Claude Desktop) |

---

## 📌 Flags Captured

| # | Flag | Source |
| :--- | :--- | :--- |
| 1 | `nw{cybersecurity_flag_captured_2608}` | My Locked PDF1.pdf |

![Flag 1](evidences/flags/flag1.png)

| # | Flag | Source |
| :--- | :--- | :--- |
| 2 | `nw{networkwalks_flag1_jtr_270521_1}` | networkwalks_flag1.pdf |

![Flag 2](evidences/flags/flag2.png)

| # | Flag | Source |
| :--- | :--- | :--- |
| 3 | `nw{networkwalks_persistence_jtr_270521}` | My Locked PDF2.pdf |

![Flag 3](evidences/flags/flag3.png)

| # | Flag | Source |
| :--- | :--- | :--- |
| 4 | `nw{networkwalks_flag_260821_1}` | My Locked PDF3.pdf |

![Flag 4](evidences/flags/flag4.png)

---

## 📌 Key Learnings

1. **Hash Extraction** – Password-protected files store passwords as hashes, which can be extracted using tools like `pdf2john.pl` or Networkwalks Hash Calculator.

2. **Dictionary Attacks** – Wordlists like `rockyou.txt` and `JTR_default_password.txt` are highly effective against weak/common passwords.

3. **Tool Versatility** – Password cracking can be done via:
   - Terminal (John the Ripper)
   - GUI (Johnny)
   - Online Tools (Networkwalks)
   - AI-Assisted (HexStrike MCP + Claude Desktop)

4. **AI Integration** – Large Language Models can interface with security tools to automate password cracking.

5. **Password Strength** – Weak passwords like `good-luck`, `password1`, and `1qaz2wsx` can be cracked in seconds.

6. **Multiple Methods** – The same password (`good-luck`) was cracked using three different methods.

---

## 📌 Conclusion

During Week 3, I completed three password cracking lab modules:

* **W3-PM1:** Successfully cracked `My Locked PDF1.pdf` using JTR Terminal and Johnny GUI.
* **W3-PM2:** Successfully cracked `My Locked PDF1.pdf` using Networkwalks online tools.
* **W3-PM-FINAL:** Successfully set up HexStrike MCP Server and used AI to crack `networkwalks_flag1.pdf`.

### Final Observations

* Weak passwords are easily compromised
* Multiple tools exist for password cracking
* AI can assist with password cracking
* Strong passwords are essential for security


# -End-

---

## 👤 Author

**Jenik Shrestha**  
Cybersecurity Trainee | B082  
Networkwalks Academy  
*www.linkedin.com/in/jenikshrestha*

---

## 📌 Project Information

| **Program** | Cybersecurity Training at Networkwalks Academy |
| :--- | :--- |
| **Week** | 03 |
| **Modules** | W3-PM1 | W3-PM2 | W3-PM-FINAL |
| **Project Area** | Password Cracking |
| **Tools Used** | JTR, Johnny, Networkwalks Tools, HexStrike MCP, Claude Desktop |

---

<div align="center">

**© Networkwalks Academy. All Rights Reserved.**

*This report is submitted as part of the Cybersecurity Training Program.*

</div>
```
