# VPN + TOR Automatic Launcher

## Overview

This Python script is designed to automatically initialize **OpenVPN** and **TOR** services, monitor connection status, and securely terminate processes in case of disconnection.

The objective is to **not launch TOR unless the VPN connection is successful** and to cleanly shut down all services upon connection loss.

The script begins with a visual ASCII banner and executes each service in a **separate terminal window**.

<img width="1265" height="976" alt="Screenshot 2026-01-07 161823" src="https://github.com/user-attachments/assets/7960072b-1a6f-48dc-b076-dafaed6d1921" />

---

## Core Features

- Automatically initiates OpenVPN connection
- Actively monitors VPN (tun0) interface
- Launches TOR service upon successful VPN connection
- Automatically terminates TOR if VPN disconnects
- All processes are safely stopped with CTRL+C
- Root / sudo verification is performed automatically
- No additional user input is required

---

## Requirements

The following components must be installed on the system:

- Python 3.x
- OpenVPN
- TOR
- GNOME Terminal
- Linux-based operating system

---

## File Structure

The following files must be located in the **home directory** for the script to function properly:

- `~/proton.ovpn` → VPN configuration file
- `~/proton_pass.txt` → VPN username / password file

---

## Installation

Make the script file executable:
```bash
chmod +x vpn_tor_launcher.py
```

## Usage

The script must be executed with **root** privileges:
```bash
sudo python3 owl.py
```

## Upon Execution

- OpenVPN is launched in the left terminal
- VPN connection is verified (`tun0`)
- TOR is launched in the right terminal
- If VPN connection is lost, TOR automatically terminates

---

## Workflow

- Screen is cleared and ASCII banner is displayed
- Presence of required files is verified
- OpenVPN is launched in a separate terminal window
- `tun0` network interface is continuously monitored
- Upon successful VPN connection, TOR service is initiated
- Upon VPN disconnection, all services are safely terminated

---

## Error Conditions

- Script halts if VPN configuration files are not found
- TOR is not launched if VPN connection fails
- TOR automatically terminates if `tun0` interface is lost

---

## Security Notes

- TOR is **never** launched without an active VPN connection
- Connection status is actively monitored
- Processes are not left running unattended in the background

---

## Legal Notice

This tool is developed exclusively for use in **educational**, **laboratory**, **CTF**, and **authorized** environments.

Use on unauthorized networks or systems is **illegal** and incurs legal liability.

The developer assumes **no responsibility** for any legal or technical damages resulting from misuse of this tool.
