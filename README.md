VirusTotal IP Checker
Automatically checks a list of IP addresses against VirusTotal and generates a formatted Excel report with the results.

What it does

Takes a list of IPs you paste into the script
Checks each one against the VirusTotal API
Saves the results to an Excel file with 3 columns:

Source Address — the IP
Status — Malicious or Clean
VT Rating — e.g. 5//94 (how many of 94 engines flagged it)


If the daily API limit runs out mid-run, it saves progress automatically and resumes the next day from where it stopped


Requirements

Python 3
A free VirusTotal API key — get one at https://www.virustotal.com


1.Installation — Mac
Step 1 — Install Homebrew
bash/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Step 2 — If Terminal says "brew not found" after installing
bashexport PATH="/opt/homebrew/bin:$PATH"

Step 3 — Install Python
bashbrew install python

Step 4 — Create a virtual environment
bashpython3 -m venv ~/vt_env

Step 5 — Activate the virtual environment
bashsource ~/vt_env/bin/activate
You will see (vt_env) appear at the start of your terminal line.

Step 6 — Install required libraries
bashpip install requests openpyxl

2.Installation — Windows

Step 1 — Download Python
Go to https://www.python.org/downloads/ and click the Download button. Run the installer.

Important: tick "Add Python to PATH" at the bottom of the installer before clicking Install.

Step 2 — Open Command Prompt
Press Windows key + R, type cmd, press Enter.

Step 3 — Verify Python installed
python --version

Step 4 — Install required libraries
pip install requests openpyxl

How to use:
Step 1 — Add your API key
Open vt_ip_checker.py and paste your VirusTotal API key here:
pythonVT_API_KEY = "your_api_key_here"

Step 2 — Paste your IPs
Replace the IPs inside IP_LIST with your list, one IP per line:
pythonIP_LIST = """
1.2.3.4
5.6.7.8
9.10.11.12
""".strip()

Step 3 — Run the script

On Mac:
bashsource ~/vt_env/bin/activate
python3 vt_ip_checker.py

On Windows:
python vt_ip_checker.py

Step 4 — Get your Excel file
The file is saved automatically in the same folder as the script, named:
IP_Threat_Analysis_2026-03-20.xlsx

If the daily limit runs out mid-run
The free VirusTotal API allows 500 requests per day. If you have more than 500 IPs the script will stop automatically when the limit hits and save progress to progress.json. The remaining IPs will be marked as Pending in the Excel file.
The next day, just run the script again — it will resume from exactly where it stopped. Once all IPs are done, progress.json is deleted automatically.

Daily usage — Mac
Every day you only need two commands:
bashsource ~/vt_env/bin/activate
python3 vt_ip_checker.py
Daily usage — Windows
Every day you only need:
python vt_ip_checker.py

Notes

Keep the repository Private since your API key is stored in the script
VT scores may vary slightly between runs as VirusTotal updates in real time — this is normal
The script preserves the exact order of IPs as pasted