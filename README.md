# SSH Brute Force Script

This script automates the process of running an Nmap scan and conducting an SSH brute-force attack using the `ssh-brute.nse` script.


## Features

- Performs an Nmap scan on a specified target IP address.
- Runs an SSH brute-force attack using the `ssh-brute.nse` script from Nmap.
- Attempts to connect to SSH with valid credentials if found during the brute-force attack.

## Prerequisites

- [Nmap](https://nmap.org/) must be installed on your system.
- Ensure that you have the necessary permissions to conduct security testing on the target.

## Usage

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/ssh-brute-force-script.git
   cd ssh-brute-force-script
   python script.py

Review Results:

    Nmap scan results are saved to nmap_results_{target_ip}.txt.
    SSH brute-force results are saved to nmap_ssh_brute_results_{target_ip}_{port}.txt.
