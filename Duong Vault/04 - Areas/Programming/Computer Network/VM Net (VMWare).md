---
share_link: https://share.note.sx/pxip6igy#wLCm3EOTAYd2t1aafUj1qBO9v7R/dkJ6NGL37Q1qESY
share_updated: 2024-10-26T20:53:49+07:00
---
- VM Net là những con switch ảo của phần mềm VMWare, các máy ảo sẽ cắm với các switch này
- NAT (Network Address Translation) là gì
    - Do số lượng public IP V4 có hạn mà số lượng máy tính quá lớn nên cần dùng public IP kết hợp với NAT
    - Có 2 loại IP là public IP (IP kết nối với bên ngoài) và private IP (IP nội bộ)
    - Không phải mỗi thiết bị đều có public IP mà chúng sẽ có private IP và sẽ được dịch sang public IP thông qua NAT
- Có 2 loại kiểu kết nối mạng với VM
    - **Bridge**
        - Switch ảo sẽ kết nối trực tiếp với cổng mạng của máy thật và của máy ảo → Máy ảo cùng lớp mạng với máy thật
        - Ví dụ:
            - Máy thật: 192.168.35.50
                - Máy ảo: 192.168.35.70
        
        ![image.png](04%20-%20Areas/Programming/Computer%20Network/VM%20Net%20(VMWare)/image.png)
        
    - **NAT**
        - Có thêm một router ảo
        - Router chia các máy ảo thành NAT inside, máy thật thành NAT outside → khi máy ảo ping ra bên ngoài thì địa chỉ IP của nó sẽ được NAT thành địa chỉ của máy thật
        - Router cắm với máy thật và switch ảo→ máy thật và máy ảo sẽ khác lớp mạng
        
        ![image.png](04%20-%20Areas/Programming/Computer%20Network/VM%20Net%20(VMWare)/image%201.png)
        
    - **Host-only**
        - VMWare sẽ tạo thêm một card mạng để kết nối với VMNet (card mạng này không liên quan tới card mạng thật)
        - Cho nên các máy ảo sẽ không thể truy cập ra mạng bên ngoài
        
        ![image.png](04%20-%20Areas/Programming/Computer%20Network/VM%20Net%20(VMWare)/image%202.png)