---
title: "Bài Viết 1: Cơ Bản Về Java"
date: 2024-12-29T00:00:00+07:00
draft: false
tags: ["Java"]
---

## Giới Thiệu

Java là một ngôn ngữ lập trình mạnh mẽ và phổ biến, được phát triển bởi Sun Microsystems và hiện nay thuộc về Oracle. Java được thiết kế để viết một lần và chạy ở mọi nơi (write once, run anywhere), có nghĩa là mã Java có thể chạy trên bất kỳ nền tảng nào có hỗ trợ máy ảo Java (JVM).

## Cài Đặt Môi Trường Phát Triển

1. **Tải và cài đặt JDK (Java Development Kit):**
   Truy cập trang chủ của Oracle và tải JDK: [Oracle JDK](https://www.oracle.com/java/technologies/javase-downloads.html).
   Chạy tệp cài đặt và làm theo hướng dẫn để cài đặt JDK trên hệ thống của bạn.

2. **Cài Đặt Môi Trường Phát Triển:**
   Bạn có thể sử dụng bất kỳ trình soạn thảo văn bản hoặc môi trường phát triển tích hợp (IDE) nào để viết mã Java. Các IDE phổ biến bao gồm Eclipse, IntelliJ IDEA và NetBeans.

## Viết Chương Trình Hello World

1. **Tạo tệp mã nguồn Java:**
   Mở IDE hoặc trình soạn thảo văn bản của bạn và tạo một tệp mới với phần mở rộng `.java`. Ví dụ: `HelloWorld.java`.

2. **Viết mã nguồn:**
   Thêm đoạn mã sau vào tệp `HelloWorld.java`:
   ```java
   public class HelloWorld {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }

3. **Biên dịch chương trình:**
    Mở terminal hoặc command prompt và điều hướng đến thư mục chứa tệp `HelloWorld.java.`'Chạy lệnh sau để biên dịch tệp Java:
    ```sh
    javac HelloWorld.java
    ```

4. **Chạy chương trình:**
    Sau khi biên dịch thành công, một tệp HelloWorld.class sẽ được tạo ra. Chạy lệnh sau để thực thi chương trình:
    ```sh
    java HelloWorld
    ```

## Cú Pháp Cơ Bản Của Java
1. Biến (Variable)
Các biến trong Java được khai báo với một kiểu dữ liệu cụ thể và có thể chứa giá trị tương ứng với kiểu đó.

    ```java
    int number = 10;
    double pi = 3.14;
    boolean isJavaFun = true;
    ```
2. Điều Kiện (Condition)
Các cấu trúc điều kiện như `if`, `else`, và `switch` được sử dụng để kiểm tra các điều kiện và thực hiện các lệnh tương ứng.

    ```java
    int score = 85;
    if (score >= 90) {
        System.out.println("A");
    } else if (score >= 80) {
        System.out.println("B");
    } else {
        System.out.println("C");
    }
    ```
3. Vòng Lặp (Loop)
Các vòng lặp như `for`, `while`, và `do-while` được sử dụng để lặp lại các thao tác cho đến khi một điều kiện nhất định được thỏa mãn.

    ```java
    for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
    }
    ```
## Kết Luận
Java là một ngôn ngữ lập trình mạnh mẽ và phổ biến, rất phù hợp cho việc phát triển ứng dụng từ nhỏ đến lớn. Với khả năng chạy trên nhiều nền tảng khác nhau và cú pháp dễ hiểu, Java là một lựa chọn tuyệt vời cho các lập trình viên ở mọi cấp độ.