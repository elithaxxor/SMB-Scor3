<p align="center">
  <img src="https://github.com/user-attachments/assets/05436e17-5476-4ff7-8ae4-baa40362a189" alt="02logo" width="200"/>
</p>


```markdown
# SMB-Scor3

SMB-Scor3 is a comprehensive tool designed for network enumeration, vulnerability assessment, and reporting, specifically targeting SMB (Server Message Block) services. This script integrates various functionalities to log activities, discover SMB hosts, perform enumeration, run advanced Nmap scans, integrate with Metasploit, and calculate vulnerability scores.

## Features

1. **Logging to SQLite**: Logs activities to a SQLite database (`smb_enum.db`) and console.
2. **SMB/Network Enumeration**: Discovers SMB hosts in a specified network range.
3. **Impacket-based Intensity Enumeration**: Performs enumeration based on specified intensity levels (LOW, MEDIUM, HIGH).
4. **Parallel Nmap Scanning**: Runs advanced Nmap scans on multiple targets concurrently.
5. **Metasploit Integration**: Launches Metasploit modules non-interactively and logs the results.
6. **Vulnerability Scoring**: Calculates vulnerability scores based on discovered data and additional criteria.
7. **Charting Final Scores**: Generates a Matplotlib line plot of vulnerability scores.

## Installation

Ensure you have the following tools and libraries installed:

- Python 3
- SQLite3
- Nmap
- Crackmapexec
- Enum4linux
- Metasploit
- Impacket

You can install the required Python libraries using:
```sh
pip install impacket matplotlib
```

## Usage

1. **Clone the Repository**:
```sh
git clone https://github.com/elithaxxor/SMB-Scor3.git
cd SMB-Scor3
```

2. **Run the Script**:
```sh
python3 smb_score.py
```

3. **Follow the Prompts**:
- Enter the network CIDR to scan (e.g., `192.168.1.0/24`).
- Choose whether to run intensity-based enumeration and specify the target IP, username, password, and domain.
- Choose whether to perform advanced parallel Nmap scanning.
- Choose whether to open the Metasploit menu.
- Optionally, define sample data for vulnerability scoring.

## Example Workflow

The main script orchestrates the entire workflow:
1. Optionally discovers SMB hosts in a specified network range.
2. Performs LAN-wide enumeration on discovered SMB hosts.
3. Runs intensity-based enumeration using Impacket.
4. Runs parallel Nmap scans on specified targets.
5. Integrates with Metasploit to run specific modules.
6. Calculates and logs vulnerability scores based on discovered data.
7. Generates a line plot of vulnerability scores.

## Output

The results are logged into the SQLite database (`smb_enum.db`) and include:
- Logs
- Nmap scans
- Metasploit runs
- Vulnerability scores

Additionally, a line plot of vulnerability scores is saved as `vulnerability_scores_line.png`.

@copyleft my mistakes yours. feel free to incorporate it into your work. however, im not responsible for your actions. do not be unethical. do not harm others. do the right thing. 

```
