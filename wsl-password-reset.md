# WSL Password Reset Guide

This guide provides the universal steps to reset a forgotten user password on any Windows Subsystem for Linux (WSL) distribution.

---

## 📑 Step-by-Step Instructions

### Step 1: Open Windows PowerShell
1. Close any open Linux/WSL terminal windows.
2. Open the Windows Start Menu.
3. Search for **PowerShell** (or **Command Prompt**) and launch it.

### Step 2: Find Your Linux Distribution Name
Run this command to list all installed Linux systems on your PC:
```powershell
wsl --list
```
*Look at the output and identify the exact name of your system (e.g., `Ubuntu`, `Ubuntu-24.04`, `Debian`).*

### Step 3: Log in as the Root User
Run the following command to bypass the password and log in directly as the system administrator. 
*(Replace `<DistributionName>` with the exact name you found in Step 2)*:
```powershell
wsl -d <DistributionName> -u root
```
*Example: `wsl -d Ubuntu -u root`*

> 💡 **Tip:** If you do not remember your Linux username, type `ls /home` once you are logged in as root to see your user folder name.

### Step 4: Reset the Password
Type the password modification command.
*(Replace `<username>` with your actual Linux account username)*:
```bash
passwd <username>
```
*Example: `passwd john`*

### Step 5: Enter Your New Password
1. Type your new password and press **Enter**.
2. Retype the password to confirm and press **Enter**.

> ⚠️ **Important Note:** The cursor will not move, and no characters (or asterisks) will appear on the screen while you type. This is a standard Linux security feature. Type your password blindly.

### Step 6: Exit
Close the root session and return to Windows PowerShell by running:
```bash
exit
```

---

## ✅ Verification
Open your Linux terminal normally. You can now use your brand-new password whenever a task asks for `sudo` authorization.
```bash
sudo apt update
```
