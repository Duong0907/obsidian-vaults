1. Cú pháp trong docker-compose file
- version: version của ứng dụng như 1.0.0, ...
- services: các services cần trong ứng dụng như frontend, backend, database, ...
	- build: đường dẫn tương đối của service
	- image: image sẽ được pull từ docker hub
	- ports: định nghĩa các port mapping, cú pháp <port của host>:<port của container>
	- environments: định nghĩa các biến môi trường, cú pháp <tên biến>=<giá trị>
	- volumes: định nghĩa các volumes mapping
- volumes: 