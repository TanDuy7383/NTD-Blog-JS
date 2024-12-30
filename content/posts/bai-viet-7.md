---
title: "Bài Viết 7: Làm Việc Với Cơ Sở Dữ Liệu Trong Java"
date: 2024-01-03T00:00:00+07:00
draft: false
tags: ["Java", "Database"]
---

## Giới Thiệu

Làm việc với cơ sở dữ liệu là một phần quan trọng trong phát triển ứng dụng. Java cung cấp một API mạnh mẽ gọi là JDBC (Java Database Connectivity) để kết nối và thao tác với cơ sở dữ liệu. Trong bài viết này, chúng ta sẽ tìm hiểu cách sử dụng JDBC để kết nối với cơ sở dữ liệu, thực hiện các câu lệnh SQL và quản lý dữ liệu.

## Cài Đặt JDBC

1. **Thêm Thư Viện JDBC:**
   - Để sử dụng JDBC, bạn cần thêm thư viện JDBC của cơ sở dữ liệu bạn đang sử dụng vào dự án của mình. Ví dụ, với MySQL, bạn có thể tải thư viện JDBC từ trang chủ của MySQL.

2. **Kết Nối Với Cơ Sở Dữ Liệu:**
   - Để kết nối với cơ sở dữ liệu, bạn cần tạo một đối tượng `Connection` và cung cấp thông tin kết nối như URL của cơ sở dữ liệu, tên người dùng và mật khẩu.
   - Ví dụ:
     ```java
     import java.sql.Connection;
     import java.sql.DriverManager;
     import java.sql.SQLException;

     public class DatabaseConnection {
         public static void main(String[] args) {
             String url = "jdbc:mysql://localhost:3306/mydatabase";
             String user = "root";
             String password = "password";

             try {
                 Connection connection = DriverManager.getConnection(url, user, password);
                 System.out.println("Connected to the database.");
             } catch (SQLException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Thực Hiện Các Câu Lệnh SQL

1. **Tạo Bảng:**
   - Bạn có thể sử dụng đối tượng `Statement` để thực hiện các câu lệnh SQL.
   - Ví dụ:
     ```java
     import java.sql.Connection;
     import java.sql.DriverManager;
     import java.sql.SQLException;
     import java.sql.Statement;

     public class CreateTable {
         public static void main(String[] args) {
             String url = "jdbc:mysql://localhost:3306/mydatabase";
             String user = "root";
             String password = "password";

             try (Connection connection = DriverManager.getConnection(url, user, password);
                  Statement statement = connection.createStatement()) {

                 String sql = "CREATE TABLE IF NOT EXISTS Users (" +
                              "id INT AUTO_INCREMENT PRIMARY KEY," +
                              "name VARCHAR(255)," +
                              "email VARCHAR(255)" +
                              ")";
                 statement.executeUpdate(sql);
                 System.out.println("Table created successfully.");
             } catch (SQLException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

2. **Chèn Dữ Liệu:**
   - Bạn có thể sử dụng đối tượng `PreparedStatement` để chèn dữ liệu vào bảng.
   - Ví dụ:
     ```java
     import java.sql.Connection;
     import java.sql.DriverManager;
     import java.sql.PreparedStatement;
     import java.sql.SQLException;

     public class InsertData {
         public static void main(String[] args) {
             String url = "jdbc:mysql://localhost:3306/mydatabase";
             String user = "root";
             String password = "password";

             try (Connection connection = DriverManager.getConnection(url, user, password)) {
                 String sql = "INSERT INTO Users (name, email) VALUES (?, ?)";
                 PreparedStatement statement = connection.prepareStatement(sql);
                 statement.setString(1, "John Doe");
                 statement.setString(2, "john.doe@example.com");
                 statement.executeUpdate();
                 System.out.println("Data inserted successfully.");
             } catch (SQLException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

3. **Truy Vấn Dữ Liệu:**
   - Bạn có thể sử dụng đối tượng `ResultSet` để truy vấn dữ liệu từ bảng.
   - Ví dụ:
     ```java
     import java.sql.Connection;
     import java.sql.DriverManager;
     import java.sql.ResultSet;
     import java.sql.SQLException;
     import java.sql.Statement;

     public class QueryData {
         public static void main(String[] args) {
             String url = "jdbc:mysql://localhost:3306/mydatabase";
             String user = "root";
             String password = "password";

             try (Connection connection = DriverManager.getConnection(url, user, password);
                  Statement statement = connection.createStatement()) {

                 String sql = "SELECT * FROM Users";
                 ResultSet resultSet = statement.executeQuery(sql);

                 while (resultSet.next()) {
                     int id = resultSet.getInt("id");
                     String name = resultSet.getString("name");
                     String email = resultSet.getString("email");
                     System.out.println("ID: " + id + ", Name: " + name + ", Email: " + email);
                 }
             } catch (SQLException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Đóng Kết Nối

- Sau khi hoàn thành các thao tác với cơ sở dữ liệu, bạn nên đóng kết nối để giải phóng tài nguyên.
- Ví dụ:
  java
  try {
      if (connection != null && !connection.isClosed()) {
          connection.close();
      }
  } catch (SQLException e) {
      e.printStackTrace();
  }
  ```
## Kết Luận
Làm việc với cơ sở dữ liệu là một kỹ năng quan trọng trong phát triển ứng dụng Java. Bằng cách sử dụng JDBC, bạn có thể dễ dàng kết nối với cơ sở dữ liệu, thực hiện các câu lệnh SQL và quản lý dữ liệu một cách hiệu quả.

