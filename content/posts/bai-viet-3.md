---
title: "Bài Viết 3: Lập Trình Hướng Đối Tượng Trong Java"
date: 2024-11-30T00:00:00+07:00
draft: false
tags: ["Java", "OOP"]
---

## Giới Thiệu

Lập trình hướng đối tượng (Object-Oriented Programming - OOP) là một trong những phương pháp lập trình phổ biến nhất hiện nay. Trong Java, OOP giúp tổ chức và quản lý mã nguồn một cách hiệu quả thông qua việc sử dụng các đối tượng và lớp. Trong bài viết này, chúng ta sẽ tìm hiểu về các khái niệm cơ bản của OOP trong Java.

## Các Khái Niệm Cơ Bản Của OOP

1. **Lớp (Class):**
   - Lớp là một bản thiết kế cho các đối tượng. Nó xác định các thuộc tính và phương thức mà đối tượng sẽ có.
   - Ví dụ:
     ```java
     public class Animal {
         String name;
         int age;

         void eat() {
             System.out.println("Eating...");
         }

         void sleep() {
             System.out.println("Sleeping...");
         }
     }
     ```

2. **Đối Tượng (Object):**
   - Đối tượng là một thể hiện cụ thể của lớp, chứa các giá trị cụ thể cho các thuộc tính.
   - Ví dụ:
     ```java
     public class Main {
         public static void main(String[] args) {
             Animal dog = new Animal();
             dog.name = "Buddy";
             dog.age = 5;
             dog.eat();
             dog.sleep();
         }
     }
     ```

3. **Kế Thừa (Inheritance):**
   - Kế thừa cho phép tạo ra một lớp mới dựa trên một lớp đã tồn tại. Lớp con sẽ kế thừa các thuộc tính và phương thức của lớp cha.
   - Ví dụ:
     ```java
     public class Dog extends Animal {
         void bark() {
             System.out.println("Barking...");
         }
     }

     public class Main {
         public static void main(String[] args) {
             Dog dog = new Dog();
             dog.name = "Buddy";
             dog.age = 5;
             dog.eat();
             dog.sleep();
             dog.bark();
         }
     }
     ```

4. **Đa Hình (Polymorphism):**
   - Đa hình cho phép sử dụng các đối tượng thuộc các lớp khác nhau thông qua một giao diện chung.
   - Ví dụ:
     ```java
     public class Animal {
         void sound() {
             System.out.println("Animal makes a sound");
         }
     }

     public class Dog extends Animal {
         void sound() {
             System.out.println("Dog barks");
         }
     }

     public class Cat extends Animal {
         void sound() {
             System.out.println("Cat meows");
         }
     }

     public class Main {
         public static void main(String[] args) {
             Animal myDog = new Dog();
             Animal myCat = new Cat();
             myDog.sound();
             myCat.sound();
         }
     }
     ```

5. **Đóng Gói (Encapsulation):**
   - Đóng gói bảo vệ trạng thái bên trong của đối tượng bằng cách hạn chế truy cập trực tiếp từ bên ngoài và chỉ cho phép thay đổi thông qua các phương thức công khai.
   - Ví dụ:
     ```java
     public class Person {
         private String name;
         private int age;

         public String getName() {
             return name;
         }

         public void setName(String name) {
             this.name = name;
         }

         public int getAge() {
             return age;
         }

         public void setAge(int age) {
             if (age > 0) {
                 this.age = age;
             }
         }
     }

     public class Main {
         public static void main(String[] args) {
             Person person = new Person();
             person.setName("John");
             person.setAge(30);
             System.out.println("Name: " + person.getName());
             System.out.println("Age: " + person.getAge());
         }
     }
     ```

## Ví Dụ Sử Dụng Các Khái Niệm OOP

1. **Tạo và Sử Dụng Đối Tượng:**
   ```java
   Animal cat = new Animal();
   cat.name = "Whiskers";
   cat.age = 3;
   cat.eat();
   cat.sleep();

2. Kế Thừa và Đa Hình:

    ```java
    Dog dog = new Dog();
    dog.name = "Buddy";
    dog.age = 5;
    dog.eat();
    dog.sleep();
    dog.bark();

    Animal myDog = new Dog();
    myDog.sound();
    ```
3. Đóng Gói:

    ```java
    Person person = new Person();
    person.setName("Jane");
    person.setAge(25);
    System.out.println("Name: " + person.getName());
    System.out.println("Age: " + person.getAge());
## Kết Luận
Lập trình hướng đối tượng (OOP) là một phương pháp lập trình mạnh mẽ giúp tổ chức và quản lý mã nguồn một cách hiệu quả. Bằng cách sử dụng các khái niệm OOP như lớp, đối tượng, kế thừa, đa hình, và đóng gói, bạn có thể viết mã dễ bảo trì và mở rộng.