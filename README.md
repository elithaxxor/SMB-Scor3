

```markdown
# SMB-Scor3

SMB-Scor3 is a comprehensive tool designed for network enumeration, vulnerability assessment, and reporting, specifically targeting SMB (Server Message Block) services. This script integrates various functionalities to log activities, discover SMB hosts, perform enumeration, run advanced Nmap scans, integrate with Metasploit, and calculate vulnerability scores.
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/05436e17-5476-4ff7-8ae4-baa40362a189" alt="02logo" width="200"/>
</p>
```
# SMB-Scor3

A comprehensive SMB network enumeration, vulnerability assessment, and scoring tool.

<p align="center">
  <img src="https://github.com/user-attachments/assets/05436e17-5476-4ff7-8ae4-baa40362a189" alt="SMB-Scor3 Logo" width="200"/>
</p>

## 🔍 Overview

SMB-Scor3 is an advanced security assessment utility designed specifically for SMB (Server Message Block) services. It integrates multiple scanning techniques, vulnerability assessment tools, and scoring algorithms into a single consolidated framework, allowing security professionals to quickly identify and quantify security risks across network environments.

## ✨ Key Features

- **Comprehensive Logging System**: All activities and findings are recorded to both console and SQLite database
- **Network Discovery**: Automated SMB host discovery across specified network ranges
- **Multi-Tiered Enumeration**:
  - Basic SMB host information collection
  - Share enumeration (including anonymous access attempts)
  - User account discovery
  - NTLM hash detection and pattern matching
- **Intensity-Based Assessment**: Three configurable scanning levels (LOW, MEDIUM, HIGH)
- **Parallel Processing**: Multi-threaded Nmap scanning for efficient network assessment
- **Metasploit Integration**: Non-interactive execution of Metasploit modules for vulnerability verification
- **Advanced Vulnerability Scoring**: Mathematical scoring algorithm that considers:
  - Detected vulnerabilities
  - Open port counts
  - High-risk service exposure
  - Plaintext credential discovery
  - Missing security patches
- **Visual Reporting**: Generates line plots of vulnerability scores for comparison

## 📋 Requirements

### External Tools
- Nmap
- CrackMapExec
- Enum4linux
- Metasploit Framework
- Impacket

### Python Libraries
- matplotlib
- impacket
- sqlite3
- concurrent.futures
- logging

## 🚀 Installation

1. **Clone the Repository**:
```bash
git clone https://github.com/elithaxxor/SMB-Scor3.git
cd SMB-Scor3
```

2. **Install Required Python Libraries**:
```bash
pip install impacket matplotlib
```

3. **Install External Dependencies** (Debian/Ubuntu):
```bash
sudo apt update
sudo apt install -y nmap crackmapexec enum4linux metasploit-framework
```

## 💻 Usage

Run the main script and follow the interactive prompts:

```bash
python3 smb_score.py
```

The tool will guide you through:
1. Network discovery (enter CIDR range)
2. Intensity-based enumeration configuration
3. Advanced Nmap scanning options
4. Metasploit module selection
5. Vulnerability scoring and visualization

## 📊 Output

- **SQLite Database**: `smb_enum.db` contains tables for:
  - Activity logs
  - Nmap scan results
  - Metasploit findings
  - Vulnerability scores
- **Visualization**: `vulnerability_scores_line.png` displays comparative scoring results
- **Console Output**: Real-time scanning and assessment information

## 🔧 Customizing Vulnerability Scoring

SMB-Scor3 uses a weighted scoring algorithm to assess the security posture of scanned hosts. The default scoring parameters can be customized to match your organization's specific risk profile:

### Default Scoring Weights
- Base score: 100 points (perfect security)
- Each vulnerability: -15 points
- Each open port: -5 points
- Each plaintext credential: -10 points
- Each missing patch: -5 points
- Each high-risk port: -3 additional points

### Risk Categories
- **Low Risk**: 80-100 points
- **Medium Risk**: 50-79 points
- **High Risk**: 20-49 points
- **Critical Risk**: 0-19 points

### Customization Options

To modify the scoring algorithm, edit the `calculate_vulnerability_score()` function in `smb_score.py`:

```python
# Adjust these values to customize scoring weights
VULN_PENALTY = 15        # Points deducted per vulnerability
PORT_PENALTY = 5         # Points deducted per open port
CREDS_PENALTY = 10       # Points deducted per plaintext credential
PATCH_PENALTY = 5        # Points deducted per missing patch
HIGH_RISK_PENALTY = 3    # Additional points deducted per high-risk port

# Modify this list to redefine high-risk ports for your environment
high_risk_list = [21, 22, 23, 25, 53, 139, 445, 1433, 3306, 3389, 5900]

# Adjust these thresholds to customize risk categories
LOW_THRESHOLD = 80
MEDIUM_THRESHOLD = 50
HIGH_THRESHOLD = 20
```

You can also extend the scoring system by adding new risk factors, such as:
- Weak encryption detection
- Outdated software versions
- Access control issues
- Password policy violations

## 📝 Example Workflow

```
=== SMB Enumeration, Scanning, Metasploit, Vulnerability Scoring ===
Enter the network CIDR to scan (e.g. 192.168.1.0/24) or blank to skip: 192.168.1.0/24
[*] Scanning network 192.168.1.0/24 for SMB hosts...
Host 192.168.1.10 has SMB service.
Host 192.168.1.25 has SMB service.
[*] Enumerating 192.168.1.10 (LAN-wide logic)...
[crackmapexec info]
SMB         192.168.1.10    445    WORKSTATION      [*] Windows 10 Pro 1909 x64 (name:WORKSTATION) (domain:WORKGROUP) (signing:False) (SMBv1:True)
[Shares (anonymous) via Impacket]:
  ADMIN$
  C$
  IPC$
  Users
...
```

## ⚠️ Disclaimer

This tool is intended for security professionals to perform authorized security assessments only. Unauthorized scanning of networks may violate local, state, and federal laws. The author is not responsible for misuse or damage caused by this tool.

@copyleft my mistakes yours. feel free to incorporate it into your work. however, I'm not responsible for your actions. do not be unethical. do not harm others. do the right thing.
