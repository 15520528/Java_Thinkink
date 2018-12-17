Java System Programming
---------------------------

<div style="text-align:center"><img src ="medi/Java-1-Introduction.png" /></div>

# 1. Mục tiêu
- Làm quen với Java
- Nắm cơ bản các thành phần cơ bản trong một service viết bằng Java
  + Logging
  + Unit test
  + Thread, Pooling, ...

# 2. Nội dung
## 2.1 Lý thuyết (40 điểm)

Đọc và viết báo cáo cho các nội dung liệt kê phía dưới. Nội dung báo cáo phải làm rõ được:
 + What? Cái đang tìm hiểu là gì (khái niệm, nội dung chi tiết)?...
 + Why? Tại sao lại cần cái này?, giúp giải quyết được gì? Ý nghĩa?, mục đích?...
 + How? Sử dụng như thế nào?, Áp dụng như thế nào, ở đâu?, Cách thức nó vận hành?...

### 2.1.1 Unit Test/Logging/Perfomance (5 đ)
- Unit test: http://www.vogella.com/tutorials/JUnit/article.html, https://dev.to/ice_lenor/unit-testing-best-practices-27ec
- Logging: 
  + Phân biệt các khái niệm liên quan tới log level
  + Tham khảo: https://logging.apache.org/log4j/2.x/performance.html + keyword phía trên
- Làm rõ khái niệm về thoughput và latency. (ý nghĩa của hai thông số này)

### 2.1.2 Threading (15 đ)
- Khái niệm Thread, multithreading, thread-safe & concurrency?
- Tìm hiểu về Threadpool, Executors.
- Tìm hiểu về synchronized, lock, atomic operation trong java: https://winterbe.com/posts/2015/04/30/java8-concurrency-tutorial-synchronized-locks-examples/. Làm rõ cách hoạt động và usecase của mỗi loại lock sau:
  + ReadWriteLock
  + StampedLock: https://dzone.com/articles/a-look-at-stampedlock

### 2.1.3 Networing (15 đ)
- Blocking và non-blocking IO và sự khác nhau. https://medium.com/@copyconstruct/nonblocking-i-o-99948ad7c957
- Tìm hiểu chung về Java NIO và Netty. Tham khảo thêm:https://stackoverflow.com/questions/8406914/benefits-of-netty-over-basic-serversocket-server
- Connection pooling ?
- Caching ? Caching với guava, redis: https://www.baeldung.com/guava-cache, https://redis.io/
- Khái niệm cơ bản về protocol trong networking.
  + http
  + websocket
  + protobuf
  + SSL/TLS

### 2.1.4 Benchmark (2 đ)
 - Benhmark ?
 - Tìm hiểu mô hình benchmark với locust https://docs.locust.io/en/stable/what-is-locust.html

### 2.1.5 JVM (3 đ)
-  jvm ? how it work ?

# 2.2. Bài tập (60 điểm)

### 2.2.1 Yêu cầu chức năng
Thiết kế chương trình chat gồm Server và Client với những chức năng sau:
 - Đăng kí và Login/Logout account
 - Hiển thị danh sách user, user online, group chat
 - Chat với 1 người hoặc group
 - UI: Web hoặc Desktop, Mobile App...

Non-Func:
 - UI/UX
 - Performance

### 2.2.2 Yêu cầu Kĩ Thuật
 - Thiết kế protocol request/response: 
   + Json cho Http
   + Protobuf cho gRPC: https://www.baeldung.com/grpc-introduction
=> Gom xử lý logic vào một module và public http & grpc api. Http có thể dùng Postman để test.

 - Authen user trước khi cho thực hiện các request tới Server. Vi dụ: Sử dụng JWT(https://jwt.io/) để sinh ra một token gửi về cho authenticated client. Các request về sau phải gửi kèm token thì mới hợp lệ 
 - Dựa trên TCP, implement socket server viết dựa trên Netty.
 - Thiết kế lưu chat data trên redis với nhiệm vụ như sau:
    + cache lại thông tin user 
    + cache lại message gần đây của user, group mà user thuộc vào - chỉ lưu `n` msg gần nhất (config từ file).
    + thiết kế cache tối ưu nhất, connection pool, ../

 - Logging: Ghi log đầy đủ và hợp ý, cấu hình logback hoặc log4j2 (console, file) sao cho ảnh hưởng ít nhất tới perfomance, lý giải config.

 - [Java Code Conventions](https://www.oracle.com/technetwork/java/codeconventions-150003.pdf)

  ## 2.2.3 Tham khảo
 - [Netty Best Practices](http://normanmaurer.me/presentations/2014-facebook-eng-netty/slides.html)
 - [Netty in Action](http://pdf.th7.cn/down/files/1603/Netty%20in%20Action.pdf)

