- Image gồm các tầng, khi tạo container thì sẽ add thêm một tầng nữa là container layer.
- Image layers sẽ bao gồm các tầng trong Dockerfile bao gồm base image, sourcecode, entry point, ...
- Khi muốn chỉnh sửa một file trong container (file đã có trong image), thì docker sẽ copy file thành một file mới và chỉnh sửa trên đó (Cơ chế Copy-on-write)
- The default folder in container for data storage is `/var/lib/mysql`
- Các **storage driver** phụ trách tạo layer in application, mount data folder, …
    - AUFS
    - ZFS
    - BTRFS
    - Device Mapper
    - Overlay
    - Overlay2

```bash
# Create a folder for storage in docker host: /var/lib/docker/volumes/data_volume
docker volumn create data_volume

# Inspect volume
docker vlume inspect data_volume

# Map data folder in container to folder in host (using mysql)
# Old style
docker run -v data_volume:/var/lib/mysql mysql
# New style
docker run --mount type=bind,source=data_volume,target=/var/lib/mysql mysql

# Delete volume
docker volume rm volume_name

# Delete all volumes
docker volume prune
```