# Windows 11 Lock Screen Slideshow Remediation

## Overview

This project focused on disabling lock screen slideshow functionality on Windows 11 systems to align with DISA STIG compliance requirements.

The remediation process included registry-based hardening, PowerShell automation, and compliance validation to reduce unnecessary lock screen exposure and improve endpoint security posture.

---

## STIG Information

| Category | Details |
|---|---|
| STIG ID | WN10-CC-000010 |
| Severity | Medium |
| Platform | Windows 11 |
| Remediation Type | Registry Hardening & PowerShell Automation |

---

## Requirement

Windows systems must prevent lock screen slideshow functionality to reduce unnecessary exposure of system information and improve overall security configuration standards.

---

## Manual Remediation Solution

### Step 1 — Open Local Group Policy Editor

Open:

```powershell
gpedit.msc
```

---

### Step 2 — Navigate to the Policy Location

```powershell
Computer Configuration → Administrative Templates → Control Panel → Personalization
```

---

### Step 3 — Configure the Policy

Enable the following policy:

```powershell
Prevent enabling lock screen slide show
```

---

### Step 4 — Apply Policy Changes

Save and apply the updated policy configuration.

---

### Step 5 — Update Group Policy

Run:

```powershell
gpupdate /force
```

to apply updated policy settings.

---

### Step 6 — Validate the Configuration

Verify the following registry path:

```powershell
HKLM\Software\Policies\Microsoft\Windows\Personalization
```

Confirm the following registry value exists:

```powershell
NoLockScreenSlideshow = 1
```

---

## PowerShell Remediation Solution

The PowerShell remediation automated the registry configuration process to disable lock screen slideshow functionality.

### PowerShell Actions Performed

- Verified registry policy paths
- Created missing registry keys
- Configured slideshow restriction settings
- Applied compliance registry values
- Updated Group Policy settings
- Validated successful configuration

---

### PowerShell Remediation Commands

```powershell
$RegPath = "HKLM:\Software\Policies\Microsoft\Windows\Personalization"

$RegName = "NoLockScreenSlideshow"

$RegValue = 1

Set-ItemProperty -Path $RegPath -Name $RegName -Value $RegValue

gpupdate /force
```

---

## Technologies Used

- Windows 11
- PowerShell
- Windows Registry
- Group Policy
- DISA STIGs
- Vulnerability Management

---

## Skills Demonstrated

- Windows security hardening
- Registry-based remediation
- PowerShell automation
- Compliance auditing
- Vulnerability remediation
- Endpoint security configuration
- Security documentation
