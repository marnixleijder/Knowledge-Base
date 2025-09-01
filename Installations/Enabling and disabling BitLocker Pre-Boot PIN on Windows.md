---
layout: default
title: Enabling and disabling BitLocker Pre-Boot PIN on Windows
#nav_title: "Test Page"  # Custom title for navigation (optional, overrides 'title')
#nav_order: 4           # Order in the sidebar (e.g., 4th position)
#parent: "Test"    # Links this page under a parent item in navigation
---

# Enabling and disabling BitLocker Pre-Boot PIN on Windows

## Introduction
BitLocker is a disk encryption feature in Windows that helps protect your data. Enabling a pre-boot pin adds an extra layer of security by requiring a pin code before the operating system starts.

## Enabling BitLocker Pre-Boot PIN

1. **Open the Local Group Policy Editor**:
   - Press `Windows + R` to open the Run dialog.
   - Type `gpedit.msc` and press `Enter`.

2. **Navigate to the BitLocker Settings**:
   - Go to `Computer Configuration` > `Administrative Templates` > `Windows Components` > `BitLocker Drive Encryption` > `Operating System Drives`.

3. **Enable the Require Additional Authentication at Startup Policy**:
   - Double-click on **Require additional authentication at startup**.
   - Select **Enabled**.
   - Then, click the box under `Configure TPM Startup PIN` and select the **Require Startup PIN With TPM** option.
   - Click **OK**.

4. **Open Command Prompt as Administrator**:
   - Search for "Command Prompt" in the Start menu.
   - Right-click and select **Run as administrator**.

5. **Add a Pre-Boot PIN**:
   - Enter the following command, replacing `C:` with the drive letter of the encrypted drive:
     ```
     manage-bde -protectors -add C: -TPMAndPIN
     ```
   - You will be prompted to enter a pin. Follow the instructions to set a pin.

6. **Restart your computer**:
   - After setting the pin, restart your computer to apply the changes.

---

## Disabling BitLocker Pre-Boot PIN

1. **Open Command Prompt as Administrator**:
   - Repeat the steps to open Command Prompt as administrator.

2. **Remove the Pre-Boot PIN**:
   - Enter the following command, replacing `C:` with the drive letter of the encrypted drive:
     ```
     manage-bde -protectors -delete C: -type TPMAndPIN
     ```

3. **Open the Local Group Policy Editor**:
   - Press `Windows + R` to open the Run dialog.
   - Type `gpedit.msc` and press `Enter`.

4. **Navigate to the BitLocker Settings**:
   - Go to `Computer Configuration` > `Administrative Templates` > `Windows Components` > `BitLocker Drive Encryption` > `Operating System Drives`.

5. **Disable the Require Additional Authentication at Startup Policy**:
   - Double-click on **Require additional authentication at startup**.
   - Select **Disabled** or **Not Configured**.
   - Click **OK**.

6. **Restart your computer**:
   - Restart your computer to apply the changes.

---

## Conclusion
Enabling a pre-boot PIN for BitLocker significantly enhances the security of your data by adding an additional layer of authentication before the operating system loads. When you enable this feature, the system requires you to enter a PIN during the boot process. This means that even if someone has physical access to your device, they cannot access the data on the encrypted drive without knowing the PIN.

This is particularly important in scenarios where a device may be lost or stolen. Without the correct PIN, unauthorized users cannot bypass the encryption, making it much more difficult for them to access sensitive information. Additionally, the pre-boot PIN helps protect against certain types of attacks, such as cold boot attacks, where an attacker attempts to extract data from memory after a system has been powered down.

Overall, the pre-boot PIN serves as a strong deterrent against unauthorized access, ensuring that your data remains secure even in the event of physical theft or tampering.
