
---
title: "Bài Viết 6: Xử Lý File Trong Java"
date: 2024-01-04T00:00:00+07:00
draft: false
tags: ["Java", "File Handling"]
---

## Giới Thiệu

Xử lý file (File Handling) là một kỹ thuật quan trọng trong lập trình, cho phép bạn đọc và ghi dữ liệu từ và đến các file trên hệ thống. Trong Java, có nhiều lớp và phương thức hỗ trợ xử lý file, bao gồm `File`, `FileReader`, `FileWriter`, `BufferedReader`, và `BufferedWriter`. Trong bài viết này, chúng ta sẽ tìm hiểu cách sử dụng các lớp này để xử lý file trong Java.

## Đọc File Trong Java

1. **Sử Dụng Lớp `FileReader` và `BufferedReader`:**
   - `FileReader` và `BufferedReader` được sử dụng để đọc dữ liệu từ file.
   - Ví dụ:
     ```java
     import java.io.*;

     public class ReadFileExample {
         public static void main(String[] args) {
             try {
                 FileReader fileReader = new FileReader("example.txt");
                 BufferedReader bufferedReader = new BufferedReader(fileReader);

                 String line;
                 while ((line = bufferedReader.readLine()) != null) {
                     System.out.println(line);
                 }

                 bufferedReader.close();
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

2. **Sử Dụng Lớp `Files`:**
   - Lớp `Files` từ gói `java.nio.file` cung cấp các phương thức tiện ích để đọc file.
   - Ví dụ:
     ```java
     import java.nio.file.*;
     import java.io.IOException;
     import java.util.List;

     public class ReadFileExample {
         public static void main(String[] args) {
             try {
                 List<String> lines = Files.readAllLines(Paths.get("example.txt"));
                 for (String line : lines) {
                     System.out.println(line);
                 }
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Ghi File Trong Java

1. **Sử Dụng Lớp `FileWriter` và `BufferedWriter`:**
   - `FileWriter` và `BufferedWriter` được sử dụng để ghi dữ liệu vào file.
   - Ví dụ:
     ```java
     import java.io.*;

     public class WriteFileExample {
         public static void main(String[] args) {
             try {
                 FileWriter fileWriter = new FileWriter("output.txt");
                 BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

                 bufferedWriter.write("Hello, World!");
                 bufferedWriter.newLine();
                 bufferedWriter.write("This is a test.");

                 bufferedWriter.close();
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

2. **Sử Dụng Lớp `Files`:**
   - Lớp `Files` từ gói `java.nio.file` cung cấp các phương thức tiện ích để ghi file.
   - Ví dụ:
     ```java
     import java.nio.file.*;
     import java.io.IOException;
     import java.util.Arrays;
     import java.util.List;

     public class WriteFileExample {
         public static void main(String[] args) {
             try {
                 List<String> lines = Arrays.asList("Hello, World!", "This is a test.");
                 Path file = Paths.get("output.txt");
                 Files.write(file, lines, StandardOpenOption.CREATE, StandardOpenOption.APPEND);
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Kiểm Tra Tồn Tại File

- Trước khi đọc hoặc ghi file, bạn có thể kiểm tra xem file có tồn tại hay không bằng cách sử dụng lớp `File`.
- Ví dụ:
  ```java
    import java.io.File;

    public class FileExistenceExample {
        public static void main(String[] args) {
            File file = new File("example.txt");
            if (file.exists()) {
                System.out.println("File exists.");
            } else {
                System.out.println("File does not exist.");
            }
        }
    }
    ```
## Xóa File
- Bạn có thể xóa file bằng cách sử dụng phương thức delete() của lớp File.

- Ví dụ:

    ```java
    import java.io.File;

    public class DeleteFileExample {
        public static void main(String[] args) {
            File file = new File("example.txt");
            if (file.delete()) {
                System.out.println("File deleted successfully.");
            } else {
                System.out.println("Failed to delete the file.");
            }
        }
    }
```
## Kết Luận
Xử lý file là một phần quan trọng trong lập trình Java, cho phép bạn thao tác với dữ liệu lưu trữ trên hệ thống. Bằng cách sử dụng các lớp và phương thức liên quan đến xử lý file, bạn có thể dễ dàng đọc, ghi, kiểm tra sự tồn tại và xóa file trong Java.