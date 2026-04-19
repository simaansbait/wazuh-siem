# Setup Process

## Wazuh Server Installation

* The Wazuh server was installed using the official installation guide from the Wazuh website

* An automated installation script (curl command) was executed on the Ubuntu VM

* The script installed all required components:

  * Wazuh Manager
  * Wazuh API
  * Wazuh Dashboard

* Wazuh can be installed from the official website according to the operating system in use.  
  For a Linux-based machine (Ubuntu/Debian), the Wazuh repository can be added using the following commands:

apt-get install gnupg apt-transport-https
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | apt-key add -
echo "deb https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list
apt-get update
sudo systemctl start wazuh-manager

* The installation process automatically downloaded all required packages

---

## Service Verification

* After installation, Wazuh services were started using the provided commands
* If installation was incomplete or incorrect, errors were returned when starting the service
* This was used as an initial verification method

---

## Dashboard Access

* The Wazuh dashboard was accessed through a web browser using:

  * https://localhost
  * or https://192.168.37.130

* Access was performed from within the Ubuntu VM

---

## Authentication

* Default login credentials were generated automatically during installation

* These credentials were displayed in the terminal output

* If needed, credentials can be retrieved using:
  sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt

---

## Agent Installation (Windows Endpoints)

* Agent installation was performed through the Wazuh dashboard

### Process:

1. Logged into the dashboard
2. Navigated to the “Add Agent” section
3. Entered endpoint details (agent name, group)
4. Generated a ready-to-use installation command

* The generated command was executed on each Windows endpoint

### Result:

* Agents were automatically:

  * Installed
  * Connected to the Wazuh server
  * Registered in the dashboard

---

## Sysmon Installation

* Sysmon was installed on each Windows endpoint using Microsoft Sysinternals

* A configuration file was used and modified to control logging behavior

---

## Sysmon Verification

* After installation, Sysmon logs were verified using Windows Event Viewer
* Confirmed that logs were being generated successfully

---

## Log Integration with Wazuh

* The Wazuh agent configuration was modified to collect Sysmon logs
* The Wazuh server was configured to accept and process these logs

---

## Log Flow Verification

### Method 1 – Dashboard

* Simulated events (e.g., failed login attempts)
* Verified alerts appeared in the Wazuh dashboard

### Method 2 – Server Logs

* Monitored logs directly on the server using:
  tail -f /var/ossec/logs/alerts/alerts.json

* Confirmed logs were being received and processed in real time

---

## Notes

* In this setup, the dashboard was accessed from within the VM
* External access from other machines was not confirmed and may depend on network configuration (NAT/Bridged mode)
