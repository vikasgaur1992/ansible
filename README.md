Ansible templates for Windows task
# Ansible Automation for Windows Server Setup

This repository contains Ansible playbooks to automate common administrative tasks on Windows servers such as browser installation and Windows updates.

---

## 🔧 Prerequisites

Before running these playbooks from your Ansible control machine (e.g., macOS/Linux), the target Windows machine must be configured to accept SSH connections and have Python installed.

### ✅ 1. Enable OpenSSH on the Windows Server

Run the following PowerShell commands **as Administrator** to download and configure OpenSSH:

```powershell
Invoke-WebRequest -Uri "https://github.com/PowerShell/Win32-OpenSSH/releases/latest/download/OpenSSH-Win64.zip" -OutFile "C:\OpenSSH-Win64.zip"
Expand-Archive -Path "C:\OpenSSH-Win64.zip" -DestinationPath "C:\Program Files\OpenSSH\OpenSSH-Win64\"
Set-Location "C:\Program Files\OpenSSH\OpenSSH-Win64\"
powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1
Start-Service sshd
Set-Service -Name sshd -StartupType 'Automatic'
netstat -an | findstr "22"  # Confirm SSH is listening

✅ 2. Verify Python Installation
Make sure Python is installed on the Windows machine. To verify:

powershell
Copy
Edit
Get-Command py | Select-Object Source
If Python is not installed, install it manually or via Ansible before running other tasks.
