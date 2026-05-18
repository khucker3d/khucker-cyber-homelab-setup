# Dedicated Cybersecurity IDE and Lab Workspace Setup
Author: Kellie Hucker  

---

## Overview
This project documents the setup of a dedicated cybersecurity development environment using Visual Studio Code and a structured CyberLab workspace. The goal is to create a clean, reproducible, and scalable environment for scripting, detection engineering, and lab management.

---

## Objective
- Configure a dedicated cybersecurity IDE (VS Code)  
- Establish a structured CyberLab workspace  
- Enable scripting across Python, PowerShell, and Bash  
- Set up version control using Git  
- Create a reproducible and organized lab environment  

---

## Workspace Structure
```
C:\CyberLab\
│
├── Infrastructure\
│   ├── VMs\
│   ├── ISOs\
│   └── NetworkDiagrams\
│
├── BlueTeam\
│   ├── Wazuh\
│   ├── Splunk\
│   ├── Logs\
│   └── Detections\
│
├── RedTeam\
│   ├── Kali\
│   └── AttackScripts\
│
├── AdLab\
│
├── Scripts\
│   ├── Python\
│   ├── PowerShell\
│   └── Bash\
│
├── Tools\
│
├── Wireshark\
│
└── Documentation\
```

---

## Key Actions Taken
- Installed and configured Visual Studio Code
- Installed essential extensions for cybersecurity workflows
- Created a structured CyberLab directory
- Configured VS Code for consistent formatting and terminal usage
- Set up Python virtual environment for isolated scripting
- Verified PowerShell scripting capability
- Installed and configured Git for version control
- Initialized CyberLab as a tracked repository

---

## Key Steps (Technical Summary)
### 1. Install and Configure VS Code
Installed Visual Studio Code and core extensions:
 - Python
 - PowerShell
 - GitLens
 - YAML
 - JSON Tools
 - Markdown All in One
 - Docker
 - Remote SSH

### 2. Create CyberLab Workspace
 - Created structured directory: `C:\CyberLab\`
 - Opened workspace in VS Code: File > Open Folder > `C:\CyberLab`

### 3. Configure VS Code Settings
Applied baseline configuration for formatting, autosave, and terminal usage.
```
{
    "editor.formatOnSave": true,
    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 1000,
    "editor.tabSize": 4,
    "editor.insertSpaces": true,
    "terminal.integrated.defaultProfile.windows": "PowerShell",
    "python.defaultInterpreterPath": "python",
    "security.workspace.trust.enabled": true
}
```

### 4. Configure Python Environment
- Verified Python installation and created a virtual environment.
  - `python --version`
  - `python -m venv .venv`
- Activated environment: `.\.venv\Scripts\activate`
- Installed initial library: `pip install requests`

### 5. Validate Python Environment
Created and executed a test script to confirm environment isolation and package availability.

### 6. Verify PowerShell Integration
- Created and executed a test PowerShell script: `.\test.ps1`
- Adjusted execution policy if required.

### 7. Install and Configure Git
- Verified installation: `git --version`
- Initialized repository:
  - `git init`
  - `git add .`
  - `git commit -m'` _Initial CyberLab setup_
- Configured identity:
    - `git config --global user.name "Your Name"`
    - `git config --global user.email "your-email@example.com"`

---

## Outcome: 
 - Fully configured cybersecurity development environment
 - Structured and scalable lab workspace
 - Functional scripting environment (Python and PowerShell)
 - Version-controlled CyberLab environment
 - Ready for automation, detection engineering, and lab expansion

---

## Skills Demonstrated
 - Environment and workspace design
 - Developer tooling (VS Code)
 - Scripting setup (Python, PowerShell)
 - Virtual environments and dependency management
 - Version control (Git)
 - Security-focused workflow organization

---

## Operational Considerations
 - Use virtual environments for all Python-based lab scripts
 - Maintain a clean folder structure for scalability
 - Keep the Git repository updated for reproducibility
 - Validate PATH and environment variables when installing tools

## Security Notes
- This project is intended for learning, personal security practice, and portfolio demonstration.
