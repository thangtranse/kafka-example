# kafka-example
Document R&amp;D and Demo

# Cấu trúc repo

1. README .md: Hướng dẫn cơ bản về Kafka & đặt vấn đề
1. docker: Hướng dẫn triển khai Kafka với docker

# Mục Lục

1. Mục Lục
1. Khái niệm cơ bản
1. Kafka bash
    1. Tạo topic
    1. Lấy thông danh sách Topic
    1. Viết message cho topic
    1. Lắng nghe message từ topic
    1. Consumer topic
1. Tài liệu tham khảo
1. Tài liệu được đóng góp bởi


# Khái niệm cơ bản

**PRODUCER**: Kafka lưu, phân loại message theo topic, sử dụng producer để publish message vào các topic. Dữ liệu được gửi đển partition của topic lưu trữ trên Broker.

**CONSUMER**: Kafka sử dụng consumer để subscribe vào topic, các consumer được định danh bằng các group name. Nhiều consumer có thể cùng đọc một topic.

**TOPIC**: Dữ liệu truyền trong Kafka theo topic, khi cần truyền dữ liệu cho các ứng dụng khác nhau thì sẽ tạo ra cá topic khác nhau.

**PARTITION**: Đây là nơi dữ liệu cho một topic được lưu trữ. Một topic có thể có một hay nhiều partition. Trên mỗi partition thì dữ liệu lưu trữ cố định và được gán cho một ID gọi là offset. Trong một Kafka cluster thì một partition có thể replicate (sao chép) ra nhiều bản. Trong đó có một bản leader chịu trách nhiệm đọc ghi dữ liệu và các bản còn lại gọi là follower. Khi bản leader bị lỗi thì sẽ có một bản follower lên làm leader thay thế. Nếu muốn dùng nhiều consumer đọc song song dữ liệu của một topic thì topic đó cần phải có nhiều partition.

**BROKER**: Kafka cluster là một set các server, mỗi một set này được gọi là 1 broker

**ZOOKEEPER**: được dùng để quản lý và bố trí các broker.

# Kafka bash

1. Tạo topic
    ```sh
    kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
    ```
    
1. Lấy thông danh sách Topic

    ```sh
    kafka-topics.sh --list --zookeeper zookeeper:2181
    ```
    
    ```sh
    kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092
    ```
1. Viết message cho topic

    ```sh
    kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
    ```
    > stop the producer client with Ctrl-C at any time
  
1. Lắng nghe message từ topic

    ```sh
    kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
    ```
    > stop the producer client with Ctrl-C at any time
    > 

1. Consumer topic

    ```sh
    kafka-consumer-groups.sh  --list --bootstrap-server localhost:9092
    ```
    
    ```sh
    kafka-consumer-groups.sh --describe --group mygroup --bootstrap-server localhost:9092
    ```
    
# Tài liệu tham khảo

1. Trang chủ Kafka: https://kafka.apache.org/
1. Câu lệnh cơ bản bắt đầu với Kafka: https://kafka.apache.org/quickstart#quickstart_kafkastreams

# Tài liệu được đóng góp bởi

1. @h999: https://github.com/H999
