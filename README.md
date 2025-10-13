# Multiple Methods to Disable Windows Automatic Updates (Windows 10 & 11)

## Multiple Methods to Disable Annoying Windows Updates Without Using Any Third-Party Software (Applicable to Windows 10 & 11)

### 1. Keep Only Driver Updates
This is the “driver-only update” mode. If you only wish Windows to automatically install drivers but not upgrade to a new build, use this method.  
⚠️ If you want to fully disable Windows updates, continue with the following steps.

**Steps:**

1. **Run Command Prompt as Administrator**
2. **Copy and paste the following command to enable Targeted Updates for a specific release:**

```cmd
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate /v TargetReleaseversion /t REG_DWORD /d 1
```

3. **Enter the second command according to your current Windows version:**

- For **21H2**:

```cmd
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate /v TargetReleaseversionInfo /t REG_SZ /d 21H2
```

- For **21H1**:

```cmd
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate /v TargetReleaseversionInfo /t REG_SZ /d 21H1
```

> 📖 Source: [learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/4145332/prevent-windows-10-upgrade-to-version-22h2)
> 💡 Tip: Check your current Windows version by pressing “Ctrl + R” and entering `winver`, then replace the `/d` value in the command with your version.

---

### 2. Set Connection as Metered
This makes Windows treat your network as “metered,” pausing automatic updates.

- **Ethernet:**  
  Settings → Network & Internet → Ethernet → Set as metered connection → On  

- **Wi-Fi:**  
  Settings → Network & Internet → WLAN → (Your Wi-Fi Name) → Properties → Set as metered connection → On  

---

### 3. Turn Off Windows Update Options
Settings → Windows Update → Advanced options  
Turn **off all options** listed.

---

### 4. Adjust Active Hours
Settings → Windows Update → Active Hours → Change active hours → Set to “Manual”  
> Suggested: Set the maximum (18 hours) covering the whole night to prevent late-night automatic updates.

---

### 5. Disable Delivery Optimization
Settings → Windows Update → Advanced options → Delivery Optimization  
Turn off “Allow downloads from other PCs”.

---

### 6. Limit Download Bandwidth
Settings → Windows Update → Advanced options → Download settings  
Choose “Absolute bandwidth”, enable “Limit how much bandwidth is used for downloading updates in the background (or foreground)”, and set to:

```
0.1 Mbps
```

---

### DisclaimerNote: It is generally **not recommended to disable Windows updates**.  
Disabling updates is intended only for specific software environments or particular version requirements.

⚠️Before performing these actions, please be aware of the following risks:

- If your device only uses Windows Defender or no antivirus software, disabling updates may expose your system to greater security risks.  
- The author does not take any responsibility for consequences arising from this operation.  
- Disabling updates may affect stability and normal operation of some programs.

⚠️Please carefully decide whether to disable Windows updates based on your needs.
