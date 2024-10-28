# Remote Window

## How to setup remote patching:

- Turn off the firewall of both machines (the remote and destiny machine).
- Create a new policy at destiny machine by using the command line: `reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v LocalAccountTokenFilterPolicy /t REG_DWORD /d 1 /f`
- Using the command to remote as **admin**:

```bash
.\PsExec.exe \\IP_destiny_machine -h -u username -p password powershell.exe

# Example:
.\PsExec.exe \\10.40.164.77 -h -u admin -p admin powershell.exe
```

- Using the command to remote as **system**:

```bash
.\PsExec.exe \\IP_destiny_machine -s -h powershell.exe

# Example:
.\PsExec.exe \\10.40.164.77 -s -h powershell.exe

```

- Note: can only remote the machine that has user admin.