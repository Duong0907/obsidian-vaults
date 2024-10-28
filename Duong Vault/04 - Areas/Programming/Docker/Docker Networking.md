# Docker Networking

- Bridge
    - Tương ứng với NAT  trong VMWare
    - Mạng bridge mặc định docker0 (192.17.0.1), các container trong mạng này sẽ có ip 172.17.x.x
    - Các mạng bridge sẽ cô lập với host nên cần port mapping để truy cập từ  bên ngoài
- Host
    - Tương tự với Bridge trong VMWare
    - Không cần port mapping
- None
    - Container không có kết nối gì với bên ngoài hay với container khác

```bash
# Inspect network
docker inspect network_name

# Create custom network
docker network create --driver=bridge --subnet=182.18.0.1/24 --gateway=182.18.0.1 wp-mysql-network
```

- Embeeded DNS Server
    - Các container có thể được gọi bằng tên thay vì địa chỉ