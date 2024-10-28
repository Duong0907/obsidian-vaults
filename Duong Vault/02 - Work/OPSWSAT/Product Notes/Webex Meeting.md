```
Patch on Win: 422
Patch association on Win: 5000423
Version feed for Win: 1000340
Version/Av/defunct association for Win: 1000835
```

## Behavior

- Installer for all user (mặc định): các user truy cập bình thường, app có cả trong thư mục Program File x86 và User/AppData
- Installer for current user:
    - User được cài truy cập bình thường
    - User khác
        - App xuất hiện trong control panel và start menu (không thể mở được do khi mở shortcut bị thiếu file)
        - Không xuất hiện trong OESIS