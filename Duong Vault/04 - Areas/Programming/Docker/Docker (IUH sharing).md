# Docker (IUH sharing)

---

1. Docker là gì?
    - Là nền tảng giúp building, deploying, running dễ dàng hơn bằng cách sử dụng các container
2. Docker và VM
    
    
    VM
    
    - Ảo hóa phần cứng
    - Khó gặp lỗi bảo mật hơn
    - Tốn tài nguyên hơn
    - Tính di động không cao
    
    Docker
    
    - Ảo hóa hệ điều hành
    - Dễ gặp lỗi bảo mật hơn hơn
    - Ít tốn tài nguyên hơn
    - Tính di động cao
    - Thời gian khởi động nhanh
3. Kiến trúc Docker
    1. Client
    2. DOCKER_HOST
    3. Registry
4. Lợi ích
    1. Vận chuyển phần mềm nhiều và nhanh hơn
    2. Tiêu chuẩn hóa quy trình vận hành
    3. Di chuyển trơn tru, hiệu quả
    4. Tiết kiệm tối đa chi phí
5. Đối tượng
    1. Lập trình viên
        1. Tính đóng gói
        2. Tính cô lập
        3. Tính di động
        4. Có thể kịch bản hóa
    2. DevOps
        - Dễ dàng quản lý
        - Loại bỏ xung đột giữa các môi trường
        - Cải thiện tốc độ và độ tin cậy
        - Tiết kiệm thời gian và tài nguyên
6. Một số khái niệm
    1. Docker container
        1. Là runtime environment mà ở đó người dùng có thể chạy 1 ứng dụng một cách độc lập
    2. Docker Image
        1. Là 1 template chứa hướng dẫn tạo ra container
        2. Nó là 1 file (read-only)
        
        ![Untitled](Docker%20(IUH%20sharing)%2008feb1e0b20247cf984291a5b149b59b/Untitled.png)
        
    3. Docker file (.yaml)
        1. Là file text để docker đọc và build thành image
            
            ![Untitled](Docker%20(IUH%20sharing)%2008feb1e0b20247cf984291a5b149b59b/Untitled%201.png)
            
    4. Docker compose 
        1. Để run tạo docker