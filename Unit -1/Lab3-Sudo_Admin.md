# Sudo and Admin managment commands


## ✅ 1. **`sudo` – Run Commands as Administrator**

`sudo` (SuperUser DO) allows you to run commands with root privileges.
![alt text](image-6.png)

```bash
sudo command
```

Example:

```bash
sudo apt update      # Run package update as admin
sudo reboot          # Reboot system
```

You'll usually be prompted to enter your password.

---

## ✅ 2. **User Management (Linux/macOS only)**

### 👤 `adduser` – Create a New User
![alt text](image-10.png)
```bash
sudo adduser newusername
```

You’ll be prompted to set a password and user info.

### 🔑 `passwd` – Change User Password

```bash
sudo passwd newusername
```

---

### 👥 `usermod` – Modify User Account

Add a user to a group:

```bash
sudo usermod -aG groupname username
```

Example:

```bash
sudo usermod -aG sudo alice     # Give 'alice' sudo access
```

---

### ❌ `deluser` – Delete a User

```bash
sudo deluser username
```

To remove the user's home directory:

```bash
sudo deluser --remove-home username
```

---

## ✅ 3. **File Permissions with `chmod` and `chown`**

### 🔐 `chmod` – Change File Permissions
![alt text](image-11.png)

Basic syntax:

```bash
chmod [permissions] file
```

#### Common Usage:

```bash
chmod 755 script.sh     # Owner: read/write/execute; others: read/execute
chmod +x file.sh        # Add execute permission
chmod -x file.sh        # Remove execute permission
```

### 🔢 What Do Numbers Mean?

| Number | Permission             |
| ------ | ---------------------- |
| 7      | read + write + execute |
| 6      | read + write           |
| 5      | read + execute         |
| 4      | read only              |
| 0      | no permission          |

Example:

```bash
chmod 644 file.txt
# Owner: read/write, Group: read, Others: read
```

---

### 👑 `chown` – Change File Owner

```bash
sudo chown user:group file
```

Example:

```bash
sudo chown alice:alice myfile.txt
```

---




## ✅ 4. **Networking Commands**

### 🌐 `ping` – Check Network Connectivity

```bash
ping google.com
```

Press `CTRL + C` to stop.

---

### 📶 `ifconfig` or `ip a` – Show IP Address & Network Info

```bash
ip a
```

```bash
ifconfig   # May require sudo or installation
```

---

### 🔍 `netstat` – Show Active Network Connections

```bash
netstat -tuln
```

Or use:

```bash
ss -tuln   # Faster alternative
```

---

## ✅ 5. **Package Management**

### For **Ubuntu/Debian (APT)**:

```bash
sudo apt update            # Refresh package list
sudo apt upgrade           # Upgrade installed packages
sudo apt install git       # Install a package
sudo apt remove git        # Uninstall a package
```

---

### For **macOS (Homebrew)**:

```bash
brew install git
```

---

## ✅ 6. **Process Management**

### 🔎 `ps` – Show Running Processes

```bash
ps aux
```

### 🔫 `kill` – Kill a Process

```bash
kill <PID>
```

Example:

```bash
kill 12345
```

Force kill:

```bash
kill -9 12345
```

---

## ✅ 8. **Shutdown and Reboot**

```bash
sudo shutdown now        # Immediate shutdown
sudo shutdown -r now     # Immediate reboot
```
