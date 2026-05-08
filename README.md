# Syca

[![AUR](https://img.shields.io/aur/version/syca?logo=arch-linux&label=AUR&cacheSeconds=5)](https://aur.archlinux.org/packages/syca)
[![License](https://img.shields.io/badge/license-GPLv3-brightgreen)]()
[![Language](https://img.shields.io/badge/language-Ruby-red)]()

A minimal **sudo-like privilege elevation tool for Linux**, written in **Ruby,** **Python + C**  
with **PAM authentication** and **system-wide secure password caching**.

Syca acts as a clean, lightweight alternative to sudo/doas while keeping strict  
security boundaries. Authentication is performed via PAM, and a secure C setuid helper  
executes privileged commands safely.

Syca includes compiling and building tools, similar to base-devel.

Note: Installing Syca will **remove** sudo and base-devel.

---

## Features

- **Authentication Cache**

Syca stores authentication securely using a root-owned state file accessed
through the setuid helper. Once authenticated, you won’t be prompted again until
the cache expires. 



- **PAM-based password authentication**
- **System-wide privilege cache** (shared across all terminals)
- User must be added to **group wheel** to be authorized.
- **Execute commands as root:**
```bash
syca <command>
```


- **Temporary root access** via privilege cache:
- Enable root access for a limited time:
```bash
syca --enable <minutes>
```

- Disable the temporary root access manually:
```bash
syca --disable
```
- Check the current status of the root access cache:
```bash
syca --status
```

## Usage

Run any command as root via Syca:

Update system packages
```bash
syca pacman -Syu
```
Restart a system service
```bash
syca systemctl restart NetworkManager
```

Edit a root-owned file
```bash
syca vim /etc/hosts
```

---

### **Installation from AUR**

## Installation

### From the AUR

Install directly using an AUR helper;

```bash
yay -S syca
```
```bash
paru -S syca
```
```bash
ame ins syca
```

### Manual Installation

Clone the repository and build the package manually:

```bash
git clone https://github.com/xkikiyaa/syca.git
cd syca
makepkg -si
```

### **Known Bugs**
- When changing user using su, then the password wont get accepted.
