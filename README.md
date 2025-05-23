# Learnspherel - Nền tảng học lập trình trực tuyến

![Java](https://img.shields.io/badge/Java-17-blue)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-green)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)
![JWT](https://img.shields.io/badge/JWT-Security-orange)

## Giới thiệu

**Learnspherel** là một nền tảng học lập trình trực tuyến được phát triển như một đồ án tốt nghiệp, tập trung vào backend. Hệ thống cho phép:

- **Học viên**: Truy cập các khóa học lập trình chất lượng (miễn phí hoặc trả phí), làm khảo sát, theo dõi tiến độ, đánh giá khóa học, và nộp bài (trắc nghiệm hoặc code) để chấm tự động.
- **Giảng viên**: Tạo và quản lý nội dung khóa học, bài học, bài kiểm tra.
- **Quản trị viên**: Quản lý người dùng, nội dung, và phê duyệt yêu cầu xóa khóa học.

Dự án sử dụng **Java Spring Boot**, **MySQL**, và **JWT** để xây dựng REST API an toàn, hỗ trợ các tính năng như lộ trình học tập, đánh giá trình độ, và chấm bài tự động.

## Mục tiêu

- Cung cấp trải nghiệm học lập trình cá nhân hóa qua khảo sát và gợi ý khóa học.
- Đảm bảo quản lý nội dung an toàn với quy trình phê duyệt.
- Giả lập trả phí để mô phỏng nền tảng thương mại.
- Tự động chấm và chữa bài (trắc nghiệm hoặc code) để hỗ trợ học viên.

## Công nghệ

- **Backend**: Java Spring Boot (REST API), Spring Security.
- **Cơ sở dữ liệu**: MySQL.
- **Bảo mật**: JSON Web Token (JWT).
- **ORM**: Hibernate/JPA.
- **JSON**: Jackson (xử lý khảo sát, bài kiểm tra).
- **Build**: Maven.

## Chức năng chính

1. **Quản lý người dùng**: Đăng ký, đăng nhập, phân quyền (Học viên, Giảng viên, Quản trị viên).
2. **Quản lý khóa học**: Tạo, cập nhật, xóa khóa học (yêu cầu phê duyệt).
3. **Đăng ký khóa học**: Học viên đăng ký, giả lập trả phí.
4. **Khảo sát sau đăng ký**: Đánh giá trình độ, sở thích để gợi ý khóa học.
5. **Theo dõi tiến độ**: Lưu và hiển thị tiến độ học tập.
6. **Đánh giá khóa học**: Học viên đánh giá bằng sao và bình luận.
7. **Đánh giá đầu vào/cuối**: Đo lường trình độ trước/sau khóa học.
8. **Gợi ý khóa học**: Dựa trên lịch sử học tập và điểm số.
9. **Quản lý bài học và bài kiểm tra**: Tạo bài học, bài kiểm tra (trắc nghiệm/code).
10. **Chấm bài tự động**: Chấm trắc nghiệm, code; cung cấp phản hồi.

## Cấu trúc dự án

```
learnspherel/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/learnspherel/
│   │   │       ├── config/         # Cấu hình JWT, Security
│   │   │       ├── controller/     # REST API controllers
│   │   │       ├── entity/         # JPA entities
│   │   │       ├── repository/     # JPA repositories
│   │   │       ├── service/        # Logic nghiệp vụ
│   │   │       └── LearnspherelApplication.java
│   │   ├── resources/
│   │       ├── application.properties  # Cấu hình Spring Boot
│   │       └── schema.sql             # Schema database
│   └── test/
└── pom.xml  # Maven dependencies
```

## Hướng dẫn cài đặt

### Yêu cầu
- Java 17
- Maven 3.8+
- MySQL 8.0+
- IDE: IntelliJ IDEA hoặc Eclipse (khuyến nghị)
- Postman (để kiểm tra API)

### Cài đặt

1. **Cài đặt MySQL**:
   - Tải và cài đặt MySQL từ [mysql.com](https://www.mysql.com/).
   - Tạo database:
     ```sql
     CREATE DATABASE learnspherel;
     ```

2. **Clone dự án**:
   ```bash
   git clone https://github.com/your_username/learnspherel.git
   cd learnspherel
   ```

3. **Cấu hình**:
   - Mở file `src/main/resources/application.properties`, cập nhật:
     ```properties
     spring.datasource.url=jdbc:mysql://localhost:3306/learnspherel?useSSL=false&serverTimezone=UTC
     spring.datasource.username=root
     spring.datasource.password=your_mysql_password
     jwt.secret=your_jwt_secret_key
     ```
   - Đảm bảo file `schema.sql` chứa schema 10 bảng (users, courses, lessons, quizzes, course_enrollments, user_progress, course_reviews, surveys, course_deletion_requests, submissions).

4. **Cài đặt phụ thuộc**:
   ```bash
   mvn clean install
   ```

5. **Chạy ứng dụng**:
   ```bash
   mvn spring-boot:run
   ```
   - Ứng dụng chạy trên `http://localhost:8080`.

## Kiểm tra API

1. **Sử dụng Postman**:
   - Đăng ký: `POST http://localhost:8080/api/auth/register`
     ```json
     {
       "username": "student1",
       "password": "pass123",
       "email": "student1@gmail.com",
       "role": "STUDENT"
     }
     ```
   - Đăng nhập: `POST http://localhost:8080/api/auth/login`
     ```json
     {
       "username": "student1",
       "password": "pass123"
     }
     ```
     - Lấy JWT từ phản hồi.
   - Gửi JWT trong header `Authorization: Bearer <token>` cho các API khác.

2. **Tài liệu API**:
   - Xem chi tiết các endpoint trong [API Documentation](docs/api.md) (hoặc tài liệu đi kèm dự án).

## Cơ sở dữ liệu

- **Số bảng**: 10
- **Bảng chính**:
  - `users`: Thông tin người dùng.
  - `courses`: Khóa học (hỗ trợ trả phí).
  - `lessons`: Bài học trong khóa học.
  - `quizzes`: Bài kiểm tra (trắc nghiệm/code, đánh giá đầu vào/cuối).
  - `course_enrollments`: Đăng ký khóa học.
  - `user_progress`: Tiến độ học tập.
  - `course_reviews`: Đánh giá khóa học.
  - `surveys`: Khảo sát và gợi ý khóa học.
  - `course_deletion_requests`: Yêu cầu xóa khóa học.
  - `submissions`: Bài nộp của học viên (trắc nghiệm/code).

## Đóng góp

1. Fork repository.
2. Tạo branch mới:
   ```bash
   git checkout -b feature/your-feature
   ```
3. Commit thay đổi:
   ```bash
   git commit -m "Add your feature"
   ```
4. Push lên branch:
   ```bash
   git push origin feature/your-feature
   ```
5. Tạo Pull Request.

## Tác giả
- NguyenXuanBach - Sinh viên TLUS, Đồ án tốt nghiệp.

## Giấy phép
Dự án được phát triển cho mục đích học thuật, không sử dụng thương mại.
