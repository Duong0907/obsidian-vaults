
```bash
# MSI
Start-Process msiexec.exe -Wait -Verb runas -ArgumentList "" -passthru;

# EXE
	Start-Process installer.exe -Wait -Verb runas -ArgumentList "" -passthru;

Start-Process AutoCAD_2023_English_Win_64bit_di_en-US_setup_webinstall -Wait -Verb runas -ArgumentList "" -passthru;

```