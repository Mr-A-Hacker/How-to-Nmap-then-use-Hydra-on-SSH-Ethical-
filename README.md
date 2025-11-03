# How-to-Nmap-then-use-Hydra-on-SSH-Ethical-
How to use Nmap and Hydra for noobs 
To ethically test SSH security using Nmap and Hydra, first scan for open SSH ports with Nmap, then use Hydra to attempt password brute-forcing — only on systems you own or have explicit permission to test.

Here’s a beginner-friendly breakdown of how to use these tools responsibly and effectively:
![Nmap-Service-Detection](https://github.com/user-attachments/assets/1ef342b0-d77a-4c7e-b610-aca3de5c6412)

🛡️ Ethical Reminder
Before you begin: Never scan or brute-force systems without permission. These tools are powerful and must be used only for educational or authorized penetration testing.

🔍 Step 1: Scan with Nmap
Goal: Identify hosts with SSH (port 22) open.

Command:

bash
nmap -p 22 -sV <target-IP>
-p 22: Scan port 22 (SSH)

-sV: Detect service version

<target-IP>: Replace with the IP address of your target system

Example Output:

Code
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3
This confirms SSH is running and gives you the version info.

🧨 Step 2: Brute-force with Hydra
Goal: Test SSH login credentials using a wordlist.

Command:

bash
hydra -l <username> -P <password-list.txt> ssh://<target-IP>
-l <username>: The username to test

-P <password-list.txt>: Path to your password wordlist (e.g., rockyou.txt)

ssh://<target-IP>: Target IP address

Example:

bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.10
Hydra will try each password in the list for the given username. If successful, it will show the correct credentials.

🧠 Tips for Noobs
Use Kali Linux or Parrot OS — both come with Nmap and Hydra pre-installed.

Start with your own virtual machine or Raspberry Pi for safe testing.

Use small wordlists first to avoid long brute-force sessions.

Always log your results and respect ethical boundaries.

📚 Learn More
GitHub guide: catgamer19’s How-to-Nmap-then-use-Hydra-on-SSH-Ethical

Hydra basics: GeeksforGeeks tutorial

Ethical usage: Cyberly’s guide
