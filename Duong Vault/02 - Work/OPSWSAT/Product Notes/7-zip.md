# 7-zip

- silently install
    
    ```bash
    # USE ADMINISTRATOR TERMINAL
    
    # For .exe
    cmd /c 7z2407-x64.exe /S
    
    # For .msi
    cmd /c 7z2407-x64.msi /quiet /norestart ALLUSERS=1
    ```
    

## Testcases for 7zip

### Architecture

|  | 64-bit | 32-bit | ARM64 | **OS Architecture** |
| --- | --- | --- | --- | --- |
| 64-bit | download, install | download | download, install |  |
| 32-bit | download, install | download, install | download, install |  |
| ARM64 | download | download | download, install |  |
| **Installer Architecture** |  |  |  |  |

### Installer’s type

|  | msi | exe | **Base** |
| --- | --- | --- | --- |
| exe | 2 instances | 1 instance |  |
| **Installer**  |  |  |  |