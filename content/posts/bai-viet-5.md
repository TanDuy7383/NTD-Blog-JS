

---
title: "Bài Viết 5: Lập Trình Đa Luồng Trong Java"
date: 2024-01-05T00:00:00+07:00
draft: false
tags: ["Java", "Multithreading"]
---

## Giới Thiệu

Lập trình đa luồng (Multithreading) là một khái niệm quan trọng trong Java cho phép thực thi nhiều luồng đồng thời trong một chương trình. Đa luồng giúp tối ưu hóa hiệu suất và tăng cường khả năng phản hồi của ứng dụng. Trong bài viết này, chúng ta sẽ tìm hiểu về lập trình đa luồng trong Java và cách sử dụng các lớp và phương thức liên quan để quản lý luồng.

## Các Khái Niệm Cơ Bản Về Đa Luồng

1. **Luồng (Thread):**
   - Một luồng là một đơn vị cơ bản của thực thi. Mỗi luồng có thể chạy đồng thời với các luồng khác.
   - Ví dụ:
     ```java
     public class MyThread extends Thread {
         public void run() {
             System.out.println("This is a thread running.");
         }

         public static void main(String[] args) {
             MyThread thread = new MyThread();
             thread.start();
         }
     }
     ```

2. **Runnable Interface:**
   - Giao diện `Runnable` cung cấp một cách khác để tạo luồng. Nó yêu cầu lớp triển khai phương thức `run()`.
   - Ví dụ:
     ```java
     public class MyRunnable implements Runnable {
         public void run() {
             System.out.println("This is a runnable running.");
         }

         public static void main(String[] args) {
             Thread thread = new Thread(new MyRunnable());
             thread.start();
         }
     }
     ```

## Quản Lý Luồng

1. **Tạo và Khởi Động Luồng:**
   - Bạn có thể tạo và khởi động luồng bằng cách sử dụng lớp `Thread` hoặc giao diện `Runnable`.
   - Ví dụ:
     ```java
     public class MyThread extends Thread {
         public void run() {
             System.out.println("Thread is running.");
         }

         public static void main(String[] args) {
             MyThread thread = new MyThread();
             thread.start();
         }
     }
     ```

2. **Đồng Bộ Hóa (Synchronization):**
   - Đồng bộ hóa đảm bảo rằng chỉ một luồng có thể truy cập vào một đoạn mã cụ thể tại một thời điểm, giúp tránh các vấn đề về dữ liệu không nhất quán.
   - Ví dụ:
     ```java
     public class Counter {
         private int count = 0;

         public synchronized void increment() {
             count++;
         }

         public int getCount() {
             return count;
         }

         public static void main(String[] args) {
             Counter counter = new Counter();

             Thread t1 = new Thread(() -> {
                 for (int i = 0; i < 1000; i++) {
                     counter.increment();
                 }
             });

             Thread t2 = new Thread(() -> {
                 for (int i = 0; i < 1000; i++) {
                     counter.increment();
                 }
             });

             t1.start();
             t2.start();

             try {
                 t1.join();
                 t2.join();
             } catch (InterruptedException e) {
                 e.printStackTrace();
             }

             System.out.println("Count: " + counter.getCount());
         }
     }
     ```

3. **Chờ và Thông Báo (Wait and Notify):**
   - `wait()` và `notify()` là hai phương thức quan trọng được sử dụng để quản lý luồng đồng bộ hóa. `wait()` làm cho luồng hiện tại chờ cho đến khi nó nhận được thông báo từ một luồng khác sử dụng `notify()`.
   - Ví dụ:
     ```java
     public class WaitNotifyDemo {
         private static final Object lock = new Object();

         public static void main(String[] args) {
             Thread t1 = new Thread(() -> {
                 synchronized (lock) {
                     System.out.println("Thread 1 is waiting...");
                     try {
                         lock.wait();
                     } catch (InterruptedException e) {
                         e.printStackTrace();
                     }
                     System.out.println("Thread 1 is resumed.");
                 }
             });

             Thread t2 = new Thread(() -> {
                 synchronized (lock) {
                     System.out.println("Thread 2 is notifying...");
                     lock.notify();
                 }
             });

             t1.start();
             t2.start();
         }
     }
     ```

## Ví Dụ Sử Dụng Đa Luồng

1. **Tạo và Khởi Động Luồng:**
   ```java
   public class MyThread extends Thread {
       public void run() {
           System.out.println("Thread is running.");
       }

       public static void main(String[] args) {
           MyThread thread = new MyThread();
           thread.start();
       }
   }
   ```
2. Đồng Bộ Hóa:

    ```java
    public class Counter {
        private int count = 0;

        public synchronized void increment() {
            count++;
        }

        public int getCount() {
            return count;
        }

        public static void main(String[] args) {
            Counter counter = new Counter();

            Thread t1 = new Thread(() -> {
                for (int i = 0; i < 1000; i++) {
                    counter.increment();
                }
            });

            Thread t2 = new Thread(() -> {
                for (int i = 0; i < 1000; i++) {
                    counter.increment();
                }
            });

            t1.start();
            t2.start();

            try {
                t1.join();
                t2.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            System.out.println("Count: " + counter.getCount());
        }
    }
    ```
3. Chờ và Thông Báo:

    ```java
    public class WaitNotifyDemo {
        private static final Object lock = new Object();

        public static void main(String[] args) {
            Thread t1 = new Thread(() -> {
                synchronized (lock) {
                    System.out.println("Thread 1 is waiting...");
                    try {
                        lock.wait();
                    } catch (InterruptedException e) {
                    e.printStackTrace();
                   }
                    System.out.println("Thread 1 is resumed.");
                }
            });

            Thread t2 = new Thread(() -> {
                synchronized (lock) {
                    System.out.println("Thread 2 is notifying...");
                lock.notify();
               }
           });

            t1.start();
            t2.start();
        }
    }
    ```
## Kết Luận
Lập trình đa luồng là một kỹ thuật mạnh mẽ trong Java giúp tối ưu hóa hiệu suất và khả năng phản hồi của ứng dụng. Bằng cách sử dụng các lớp và phương thức liên quan đến đa luồng, bạn có thể quản lý các luồng đồng thời và xử lý dữ liệu một cách hiệu quả.
