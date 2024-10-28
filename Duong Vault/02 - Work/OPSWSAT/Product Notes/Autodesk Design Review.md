- Vendor không còn hỗ trợ Design Review nữa (version chính thức mới nhất từ năm 2017), nhưng vẫn cung cấp các bản hotfix cho version mới nhất (vẫn nâng version cao hơn)
- Phải cài đặt bản mới nhất trên web (14.0.0.177) mới dùng file .msp được (14.0.7.205)
- **Download link:** [https://download.autodesk.com/us/support/files/designreview/2018/EXE/enu/SetupDesignReview.exe](https://download.autodesk.com/us/support/files/designreview/2018/EXE/enu/SetupDesignReview.exe)
- **Languages**
    - Brazilian Portuguese
    - English
    - French
    - German
    - Italian
    - Japanese
    - Korean
    - Polish
    - Russian
    - Simplified Chinese
    - Spanish
- Ids

```
Patch on Win: 423
Patch association on Win: 5000424
Version feed for Win: 1000341
Version/Av/defunct association for Win: 1000837
```

- Debug in source code

![image.png](02%20-%20Work/OPSWSAT/Product%20Notes/Autodesk%20Design%20Review/image.png)

## Patching

- Silent install:
    
    ```bash
    # Silent install base
    ./Setup.exe /W /q /I Setup.ini /language en-us
    
    # Silent install patch
    msiexec.exe /p ADR2018SP7.msp /qn
    ```