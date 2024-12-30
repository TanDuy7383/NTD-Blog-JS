---
title: "Bài Viết 2: Các Kiểu Dữ Liệu Trong Java"
date: 2024-11-30T00:00:00+07:00
draft: false
tags: ["Java"]
---

## Giới Thiệu

Trong Java, kiểu dữ liệu rất quan trọng vì chúng xác định loại dữ liệu mà một biến có thể chứa và các thao tác có thể thực hiện trên dữ liệu đó. Java có các kiểu dữ liệu nguyên thủy và kiểu dữ liệu đối tượng. Trong bài viết này, chúng ta sẽ tìm hiểu về các kiểu dữ liệu cơ bản trong Java và cách sử dụng chúng.

## Các Kiểu Dữ Liệu Nguyên Thủy

1. **Số Nguyên (Integer):**
   - Các kiểu dữ liệu số nguyên bao gồm: `byte`, `short`, `int`, `long`.
   - Ví dụ:
     ```java
     byte smallNumber = 12;
     short mediumNumber = 32000;
     int number = 1000000;
     long largeNumber = 10000000000L;
     ```

2. **Số Thực (Floating-Point):**
   - Các kiểu dữ liệu số thực bao gồm: `float`, `double`.
   - Ví dụ:
     ```java
     float pi = 3.14f;
     double bigPi = 3.141592653589793;
     ```

3. **Kiểu Logic (Boolean):**
   - Kiểu dữ liệu boolean chỉ có hai giá trị: `true` và `false`.
   - Ví dụ:
     ```java
     boolean isJavaFun = true;
     boolean isFishTasty = false;
     ```

4. **Ký Tự (Character):**
   - Kiểu dữ liệu char lưu trữ một ký tự đơn và sử dụng mã Unicode.
   - Ví dụ:
     ```java
     char letterA = 'A';
     char letterB = 66; // Mã Unicode cho chữ 'B'
     ```

## Các Kiểu Dữ Liệu Đối Tượng

1. **Chuỗi (String):**
   - Kiểu dữ liệu chuỗi lưu trữ các chuỗi ký tự.
   - Ví dụ:
     ```java
     String greeting = "Hello, World!";
     ```

2. **Mảng (Array):**
   - Kiểu dữ liệu mảng lưu trữ một tập hợp các giá trị có cùng kiểu dữ liệu.
   - Ví dụ:
     ```java
     int[] numbers = {1, 2, 3, 4, 5};
     String[] fruits = {"Apple", "Banana", "Cherry"};
     ```

3. **Đối Tượng (Object):**
   - Kiểu dữ liệu đối tượng là các thực thể có thuộc tính và phương thức.
   - Ví dụ:
     ```java
     class Person {
         String name;
         int age;

         Person(String name, int age) {
             this.name = name;
             this.age = age;
         }

         void display() {
             System.out.println("Name: " + name + ", Age: " + age);
         }
     }

     public class Main {
         public static void main(String[] args) {
             Person person = new Person("John", 30);
             person.display();
         }
     }
     ```

## Ví Dụ Sử Dụng Các Kiểu Dữ Liệu

1. **Tính Toán Với Số Nguyên:**
   ```java
   int a = 10;
   int b = 20;
   int sum = a + b;
   System.out.println("Sum: " + sum);
2. **Xử Lý Chuỗi:**
   ```java
    String firstName = "John";
    String lastName = "Doe";
    String fullName = firstName + " " + lastName;
    System.out.println("Full Name: " + fullName);
    ```
3. **Làm Việc Với Mảng:**
   ```java
    int[] scores = {85, 90, 78, 92, 88};
    for (int score : scores) {
        System.out.println("Score: " + score);
    }
    ```

