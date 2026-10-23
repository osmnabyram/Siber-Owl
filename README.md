<div align="center">

# Owl

### VPN-first launcher: TOR never starts unless the VPN is up, and dies with it.

A Python supervisor for OpenVPN and TOR that enforces one rule — no anonymized traffic without a verified tunnel — and cleans up every process the moment the connection drops.

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![OpenVPN](https://img.shields.io/badge/Uses-OpenVPN%20%2B%20TOR-e53935?style=for-the-badge)
![Root](https://img.shields.io/badge/Requires-root-121212?style=for-the-badge&logo=gnubash&logoColor=white)

</div>

<div align="center">
<img width="1265" alt="Owl interface" src="https://github.com/user-attachments/assets/7960072b-1a6f-48dc-b076-dafaed6d1921" />
</div>

---

<div align="center">
<img src="assets/how-it-works.svg" alt="How it works: an animated diagram of the tool's core flow." width="820" />
</div>

## Overview

Owl removes a common operational mistake: routing traffic through TOR while the VPN is silently down. It starts OpenVPN, waits for the tunnel to come up, and only then launches TOR. It keeps watching the `tun0` interface, and if the VPN drops it shuts TOR down immediately so nothing is left running unprotected. Each service runs in its own terminal window.

---

## Core Features

- Starts the OpenVPN connection automatically
- Actively monitors the VPN (`tun0`) interface
- Launches TOR only after the VPN is confirmed up
- Terminates TOR automatically if the VPN disconnects
- Stops all processes cleanly on Ctrl+C
- Verifies root privileges on startup
- No additional user input required once running

---

## Requirements

| Component | Notes |
|---|---|
| Python 3.x | Interpreter |
| OpenVPN | VPN client |
| TOR | Anonymity service |
| GNOME Terminal | Each service opens in its own window |
| Linux + root | Required to bring up the tunnel |

### Expected files

These must exist in your home directory:

| File | Purpose |
|---|---|
| `~/proton.ovpn` | VPN configuration file |
| `~/proton_pass.txt` | VPN username / password file |

---

## Installation

```bash
git clone https://github.com/osmnabyram/Siber-Owl.git
cd Siber-Owl
chmod +x Owl.py
sudo python3 Owl.py
```

On execution Owl brings up OpenVPN, verifies `tun0`, launches TOR in a second terminal, and keeps monitoring the link until you exit.

---

## Responsible Use

Owl is a privacy and lab automation tool intended for **educational, lab, CTF, and authorized** use. Use it in line with local law and the terms of the services involved. The author accepts no responsibility for misuse.
