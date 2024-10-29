<img src="https://punksecurity.co.uk/images/blog/docker-banner.png">

## Docker
- Docker là một công cụ quản lý giúp tự động hóa việc triển khai (deploy) phần mềm dựa vào các container. Chúng giúp phần mềm có thể hoạt động được một cách hiệu quả trong môi trường (hệ điều hành, ...) khác nhau.

## Docker container
- Docker container là một môi trường ảo gọn nhẹ, nó có thể tạo, chạy, và triển khai (deploy) ứng dụng một cách độc lập với phần cứng hay hệ điều hành bên dưới.
- Các Docker container có tất cả các dependencies cần thiết để chạy được phần mềm.
- 
## Docker image
- Docker image là một bản mẫu, được build lên từ Dockerfile, được dùng để build lên Docker container. 
- Ta có thể xem Docker image là một snapshot của một Docker container tại một thời điểm. Từ snapshot này có thể tạo dựng lại được một container. 
- Docker image có thể được sử dụng lại nhiều lần, bởi vì khi chạy container thì Docker image không hề bị ảnh hưởng hoặc thay đổi.
- Docker image gồm có nhiều tầng, dựa trên tầng thấp nhất là base
- 
## Docker file
- Dockerfile là một text file chứa các chỉ dẫn để build ra Docker image.
- 
## Docker và làm bánh
- Chúng ta hãy liên tưởng các khái niệm này trong Docker với quy trình tạo ra một cái bánh thơm ngon. 
- Dockerfile chính là bản hướng dẫn trong đó có ghi chi tiết nguyên liệu cần có, cách làm, ...
- Docker image là nguyên liệu mà ta dựa vào bản hướng dẫn đó mua về, và cả cách làm mà ta đã lĩnh hội được từ nó. Tới đây là ta có thể làm bánh mà không cần dựa vào hướng dẫn đó nữa :). Quá trình mua nguyên liệu tương tự như lệnh `Docker build` 
- Có nguyên liệu và cách làm rồi thì ta chỉ việc dựa vào đó mà triển hoi, thành quả là được một cái bánh hoàn chỉnh, đó chính là Docker container. Quán trình làm bánh tương tự như lệnh `Docker run`