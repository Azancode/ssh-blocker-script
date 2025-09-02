# SSH Blocker 🔒

A lightweight Bash script to automatically block IP addresses after multiple failed SSH login attempts.  
It monitors `/var/log/auth.log`, detects repeated failures, and adds the attacker’s IP to `iptables` for protection.  

---

## ✨ Features
- Monitors SSH failed login attempts from `/var/log/auth.log`
- Blocks attacker IPs using `iptables`
- Custom logging of blocked IPs (`/var/log/ssh-blocker.log`)
- Simple and minimal – no external dependencies like Fail2Ban

---

## 📜 Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/ssh-blocker.git
   cd ssh-blocker
2. Make the script executable:
   ```bash
   chmod +x log.sh
3. Run manually:
   ```bash
   sudo ./log.sh
4. (Optional) Run as a background service with systemd:
   Create /etc/systemd/system/ssh-blocker.service:
   [Unit]
Description=SSH Blocker Script
After=network.target

[Service]
ExecStart=/path/to/log.sh
Restart=always

[Install]
WantedBy=multi-user.target

5. Then enable and start it:
   ```bash
   sudo systemctl enable log
   sudo systemctl start log
