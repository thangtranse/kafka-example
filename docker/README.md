# Triển khai Kafka với Docker

## 1. Yêu cầu trước khi thực hiện

1. Đã thiết lập môi trường Docker & Docker compose
1. Đảm bảo các `port 9092 & 2181` chưa được sử dụng hoặc bạn có thể thay đổi trong file `docker-compose.yml`

> Demo này được thực hiện trên `Macos version 11.2.2` với sersion Docker `2.4.0.0`, bạn có thể thực hiện theo hướng dẫn này với các phiên bản khác, tuy nhiên có thể có vài sự khác biệt.

## 2. Triển khai thực hiện

1. Bước 1: 
    
    Khơi chạy `container`

        ```sh
        docker-compose up
        ```
1. Bước 2:

    Kiểm tra `container` đang chạy & truy cập vào `container` đó

        ```sh
        docker exec -it < ID container wurstmeister/kafka >  /bin/sh; exit
        ```

    Trong đó `< ID container wurstmeister/kafka >` là ID container đang chạy Kafka (không phải container wurstmeister/zookeeper)

1. Bước 3:

    Bạn mở thêm 1 terminal mới thực hiện tương tự `bước 2` sau đó bạn có thể `thực hiện tạo topic gửi message đến topic` đó và một bên `terminal để đóng vai là một con consumer` để lắng nghe message mới