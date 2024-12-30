---
title: "Bài Viết 4: Xử Lý Ngoại Lệ Trong Java"
date: 2024-01-30T00:00:00+07:00
draft: false
tags: ["Java", "Exception Handling"]
---

## Giới Thiệu

Xử lý ngoại lệ (Exception Handling) là một phần quan trọng của lập trình trong Java. Ngoại lệ là các sự cố xảy ra trong quá trình thực thi chương trình, khiến chương trình không thể tiếp tục chạy. Trong bài viết này, chúng ta sẽ tìm hiểu cách xử lý ngoại lệ trong Java và cách sử dụng các khối `try`, `catch`, `finally` để quản lý ngoại lệ một cách hiệu quả.

## Các Loại Ngoại Lệ Trong Java

1. **Checked Exceptions:**
   - Ngoại lệ được kiểm tra tại thời điểm biên dịch. Chúng thường xảy ra do các điều kiện bên ngoài mà chương trình không thể kiểm soát được.
   - Ví dụ: `IOException`, `SQLException`.

2. **Unchecked Exceptions:**
   - Ngoại lệ không được kiểm tra tại thời điểm biên dịch. Chúng thường xảy ra do lỗi logic hoặc lập trình sai.
   - Ví dụ: `NullPointerException`, `ArrayIndexOutOfBoundsException`.

3. **Errors:**
   - Lỗi nghiêm trọng mà thường không thể xử lý được. Chúng thường xảy ra do các vấn đề về hệ thống hoặc tài nguyên.
   - Ví dụ: `OutOfMemoryError`, `StackOverflowError`.

## Sử Dụng Khối try-catch-finally

1. **Khối try-catch:**
   - Khối `try` chứa mã có thể gây ra ngoại lệ. Khối `catch` xử lý ngoại lệ nếu nó xảy ra.
   - Ví dụ:
     ```java
     try {
         int[] numbers = {1, 2, 3};
         System.out.println(numbers[5]);
     } catch (ArrayIndexOutOfBoundsException e) {
         System.out.println("Array index is out of bounds!");
     }
     ```

2. **Khối finally:**
   - Khối `finally` chứa mã sẽ được thực thi bất kể ngoại lệ có xảy ra hay không. Nó thường được sử dụng để giải phóng tài nguyên.
   - Ví dụ:
     ```java
     try {
         int[] numbers = {1, 2, 3};
         System.out.println(numbers[5]);
     } catch (ArrayIndexOutOfBoundsException e) {
         System.out.println("Array index is out of bounds!");
     } finally {
         System.out.println("This block is always executed.");
     }
     ```

## Tạo Ngoại Lệ Tùy Chỉnh

- Bạn có thể tạo ngoại lệ tùy chỉnh bằng cách mở rộng lớp `Exception` hoặc `RuntimeException`.
- Ví dụ:
  ```java
  public class CustomException extends Exception {
      public CustomException(String message) {
          super(message);
      }
  }

  public class Main {
      public static void main(String[] args) {
          try {
              checkNumber(0);
          } catch (CustomException e) {
              System.out.println(e.getMessage());
          }
      }

      public static void checkNumber(int number) throws CustomException {
          if (number <= 0) {
              throw new CustomException("Number must be greater than zero!");
          }
      }
  }
## Sử Dụng Throws
- Từ khóa `throws` được sử dụng để khai báo rằng một phương thức có thể ném ngoại lệ.

- Ví dụ:

    ```java
    public class Main {
        public static void main(String[] args) {
            try {
                checkFile("file.txt");
            } catch (IOException e) {
                System.out.println(e.getMessage());
            }
        }   
    
        public static void checkFile(String fileName) throws IOException {
            FileReader file = new FileReader(fileName);
            BufferedReader fileInput = new BufferedReader(file);
            fileInput.close();
        }
    }
    ```
## Kết Luận
Xử lý ngoại lệ là một phần quan trọng trong lập trình Java giúp bạn quản lý và kiểm soát các sự cố xảy ra trong quá trình thực thi chương trình. Bằng cách sử dụng các khối try, catch, finally và tạo ngoại lệ tùy chỉnh, bạn có thể đảm bảo chương trình của mình hoạt động ổn định và dễ bảo trì.