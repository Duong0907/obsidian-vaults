# Share folder from Windows host to Ubuntu VM

1. Tải VMware Tools cho Ubuntu: 

```bash
sudo apt update
sudo apt upgrade

sudo apt install open-vm-tools open-vm-tools-desktop

sudo reboot
```

1. Set up shared folder 
- Open VMware Workstation and select your Ubuntu VM.
- Navigate to **`VM`** > **`Settings`** > **`Options`** > **`Shared Folders`**.
- Add a new shared folder and choose the folder path on your Windows machine.
1. Truy cập shared folder

```bash
mkdir ~/shared

sudo vmhgfs-fuse .host:/sharename ~/shared -o allow_other -o uid=1000
```

- Shared folder nằm ở thư mục `~/shared`