## Mẫu project cho môn SWP391
### Web app sử dụng React, Spring Boot và MySQL

Cấu trúc project
```
.
├── backend
│   ├── Dockerfile
│   ...
├── db
│   └── password.txt
├── compose.yaml
├── frontend
│   ├── ...
│   └── Dockerfile
└── README.md
```
> ℹ️ **_CHÚ Ý_**
> 
> Docker sẽ mở cổng 3000, 8080, 3306 từ các container đến các cổng tương đương trên máy host
> 
> Hãy đảm bảo các cổng 3000, 8080, 3306 trên máy host không được sử dụng

## Chạy docker compose

Đứng từ folder chứa file [_compose.yaml_](compose.yaml), mở cmd và chạy lệnh bên dưới

```
$ docker compose up -d --build
...
Creating swp-template-frontend-1 ... done
Creating swp-template-db-1       ... done
Creating swp-template-backend-1  ... done
```

Hướng dẫn cách điều hướng đến thư mục trên Windows xem tại [Phụ lục 1](#1-phụ-lục-1).

Hướng dẫn copy và dán lệnh trong cmd bằng Crtl-C + Crtl-V xem tại Phụ lục 2.

> ℹ️ **_CHÚ Ý_**
> 
> Mỗi lần có code mới cũng chạy lại lệnh này để update code trong các container

## Kết quả mong muốn

Danh sách các container sau khi chạy

Mở cmd và chạy lệnh bên dưới
```
$ docker ps
ONTAINER ID        IMAGE                       COMMAND                  CREATED             STATUS              PORTS                  NAMES
a63dee74d79e        react-java-mysql-backend    "java -Djava.securit…"   39 seconds ago      Up 37 seconds                              react-java-mysql_backend-1
6a7364c0812e        react-java-mysql-frontend   "docker-entrypoint.s…"   39 seconds ago      Up 33 seconds       0.0.0.0:3000->3000/tcp react-java-mysql_frontend-1
b176b18fbec4        mysql:8.0.19                "docker-entrypoint.s…"   39 seconds ago      Up 37 seconds       3306/tcp, 33060/tcp    react-java-mysql_db-1
```


## Kiểm tra các cổng

Sau khi app chạy, kiểm tra url `http://localhost:3000` trên browser
![page](./tutorials/output.jpg)

Kiểm tra url `http://localhost:8080` trên browser

Kiểm tra cổng 3306 của MySQL bằng MySQL Workbench

Dừng và xoá các containers

Đứng từ folder chứa file [_compose.yaml_](compose.yaml), mở cmd và chạy lệnh bên dưới

Hướng dẫn cách điều hướng đến thư mục trên Windows xem tại Phụ lục 1.
```
$ docker compose down
Stopping swp-template-backend-1  ... done
Stopping swp-template-frontend-1 ... done
Stopping swp-template-db-1       ... done
Removing swp-template-backend-1  ... done
Removing swp-template-frontend-1 ... done
Removing swp-template-db-1       ... done
Removing network swp-template-default
```

## Phụ lục
### 1. Phụ lục 1
### 2. Phụ lục 2
