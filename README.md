Learnspherel - Nền tảng học lập trình trực tuyến



Giới thiệu

Learnspherel là một nền tảng học lập trình trực tuyến được phát triển như một đồ án tốt nghiệp, tập trung vào backend. Hệ thống cho phép:





Học viên: Truy cập các khóa học lập trình chất lượng (miễn phí hoặc trả phí), làm khảo sát, theo dõi tiến độ, đánh giá khóa học, và nộp bài (trắc nghiệm hoặc code) để chấm tự động.



Giảng viên: Tạo và quản lý nội dung khóa học, bài học, bài kiểm tra.



Quản trị viên: Quản lý người dùng, nội dung, và phê duyệt yêu cầu xóa khóa học.

Dự án sử dụng Java Spring Boot, MySQL, và JWT để xây dựng REST API an toàn, hỗ trợ các tính năng như lộ trình học tập, đánh giá trình độ, và chấm bài tự động.

Mục tiêu





Cung cấp trải nghiệm học lập trình cá nhân hóa qua khảo sát và gợi ý khóa học.



Đảm bảo quản lý nội dung an toàn với quy trình phê duyệt.



Giả lập trả phí để mô phỏng nền tảng thương mại.



Tự động chấm và chữa bài (trắc nghiệm hoặc code) để hỗ trợ học viên.

Công nghệ





Backend: Java Spring Boot (REST API), Spring Security.



Cơ sở dữ liệu: MySQL.



Bảo mật: JSON Web Token (JWT).



ORM: Hibernate/JPA.



JSON: Jackson (xử lý khảo sát, bài kiểm tra).



Build: Maven.

Chức năng chính





Quản lý người dùng: Đăng ký, đăng nhập, phân quyền (Học viên, Giảng viên, Quản trị viên).



Quản lý khóa học: Tạo, cập nhật, xóa khóa học (yêu cầu phê duyệt).



Đăng ký khóa học: Học viên đăng ký, giả lập trả phí.



Khảo sát sau đăng ký: Đánh giá trình độ, sở thích để gợi ý khóa học.



Theo dõi tiến độ: Lưu và hiển thị tiến độ học tập.



Đánh giá khóa học: Học viên đánh giá bằng sao và bình luận.



Đánh giá đầu vào/cuối: Đo lường trình độ trước/sau khóa học.



Gợi ý khóa học: Dựa trên lịch sử học tập và điểm số.



Quản lý bài học và bài kiểm tra: Tạo bài học, bài kiểm tra (trắc nghiệm/code).



Chấm bài tự động: Chấm trắc nghiệm, code; cung cấp phản hồi.

Cấu trúc dự án

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

Hướng dẫn cài đặt

Yêu cầu





Java 17



Maven 3.8+



MySQL 8.0+



IDE: IntelliJ IDEA hoặc Eclipse (khuyến nghị)



Postman (để kiểm tra API)

Cài đặt





Cài đặt MySQL:





Tải và cài đặt MySQL từ mysql.com.



Tạo database:

CREATE DATABASE learnspherel;



Clone dự án:

git clone https://github.com/your_username/learnspherel.git
cd learnspherel



Cấu hình:





Mở file src/main/resources/application.properties, cập nhật:

spring.datasource.url=jdbc:mysql://localhost:3306/learnspherel?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=your_mysql_password
jwt.secret=your_jwt_secret_key



Đảm bảo file schema.sql chứa schema 10 bảng (users, courses, lessons, quizzes, course_enrollments, user_progress, course_reviews, surveys, course_deletion_requests, submissions).



Cài đặt phụ thuộc:

mvn clean install



Chạy ứng dụng:

mvn spring-boot:run





Ứng dụng chạy trên http://localhost:8080.

Kiểm tra API





Sử dụng Postman:





Đăng ký: POST http://localhost:8080/api/auth/register

{
  "username": "student1",
  "password": "pass123",
  "email": "student1@gmail.com",
  "role": "STUDENT"
}



Đăng nhập: POST http://localhost:8080/api/auth/login

{
  "username": "student1",
  "password": "pass123"
}





Lấy JWT từ phản hồi.



Gửi JWT trong header Authorization: Bearer <token> cho các API khác.



Tài liệu API:





Xem chi tiết các endpoint trong API Documentation (hoặc tài liệu đi kèm dự án).

Cơ sở dữ liệu





Số bảng: 10



Bảng chính:





users: Thông tin người dùng.



courses: Khóa học (hỗ trợ trả phí).



lessons: Bài học trong khóa học.



quizzes: Bài kiểm tra (trắc nghiệm/code, đánh giá đầu vào/cuối).



course_enrollments: Đăng ký khóa học.



user_progress: Tiến độ học tập.



course_reviews: Đánh giá khóa học.



surveys: Khảo sát và gợi ý khóa học.



course_deletion_requests: Yêu cầu xóa khóa học.



submissions: Bài nộp của học viên (trắc nghiệm/code).

Đóng góp





Fork repository.



Tạo branch mới:

git checkout -b feature/your-feature



Commit thay đổi:

git commit -m "Add your feature"



Push lên branch:

git push origin feature/your-feature



Tạo Pull Request.

Tác giả





NguyenXuanBach - Sinh viên TLUS, Đồ án tốt nghiệp.

Giấy phép

Dự án được phát triển cho mục đích học thuật, không sử dụng thương mại.
