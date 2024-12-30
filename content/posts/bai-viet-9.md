---
title: "Bài Viết 9: Lập Trình Mạng Trong Java"
date: 2024-01-01T00:00:00+07:00
draft: false
tags: ["Java", "Networking"]
---

## Giới Thiệu

Lập trình mạng (Networking) là một kỹ thuật quan trọng trong lập trình, cho phép các ứng dụng giao tiếp với nhau qua mạng. Trong Java, thư viện `java.net` cung cấp các lớp và giao diện hỗ trợ lập trình mạng. Trong bài viết này, chúng ta sẽ tìm hiểu cách sử dụng các lớp này để tạo các ứng dụng mạng, bao gồm tạo server và client.

## Tạo Server Đơn Giản

1. **Cấu Trúc Cơ Bản:**
   - Để tạo một server đơn giản, bạn cần sử dụng lớp `ServerSocket` để lắng nghe các kết nối từ client.
   - Ví dụ:
     ```java
     import java.io.*;
     import java.net.*;

     public class SimpleServer {
         public static void main(String[] args) {
             try (ServerSocket serverSocket = new ServerSocket(12345)) {
                 System.out.println("Server is listening on port 12345");
                 Socket socket = serverSocket.accept();
                 System.out.println("Client connected");

                 OutputStream output = socket.getOutputStream();
                 PrintWriter writer = new PrintWriter(output, true);
                 writer.println("Hello, Client!");

                 socket.close();
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Tạo Client Đơn Giản

1. **Cấu Trúc Cơ Bản:**
   - Để tạo một client đơn giản, bạn cần sử dụng lớp `Socket` để kết nối tới server.
   - Ví dụ:
     ```java
     import java.io.*;
     import java.net.*;

     public class SimpleClient {
         public static void main(String[] args) {
             try (Socket socket = new Socket("localhost", 12345)) {
                 InputStream input = socket.getInputStream();
                 BufferedReader reader = new BufferedReader(new InputStreamReader(input));
                 String message = reader.readLine();
                 System.out.println("Server: " + message);
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Truyền Dữ Liệu Giữa Server và Client

1. **Server:**
   - Ví dụ về server gửi và nhận dữ liệu từ client.
     ```java
     import java.io.*;
     import java.net.*;

     public class EchoServer {
         public static void main(String[] args) {
             try (ServerSocket serverSocket = new ServerSocket(12345)) {
                 System.out.println("Server is listening on port 12345");
                 while (true) {
                     Socket socket = serverSocket.accept();
                     System.out.println("Client connected");

                     InputStream input = socket.getInputStream();
                     BufferedReader reader = new BufferedReader(new InputStreamReader(input));

                     OutputStream output = socket.getOutputStream();
                     PrintWriter writer = new PrintWriter(output, true);

                     String message;
                     while ((message = reader.readLine()) != null) {
                         System.out.println("Received: " + message);
                         writer.println("Echo: " + message);
                     }

                     socket.close();
                 }
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

2. **Client:**
   - Ví dụ về client gửi và nhận dữ liệu từ server.
     ```java
     import java.io.*;
     import java.net.*;

     public class EchoClient {
         public static void main(String[] args) {
             try (Socket socket = new Socket("localhost", 12345)) {
                 OutputStream output = socket.getOutputStream();
                 PrintWriter writer = new PrintWriter(output, true);

                 InputStream input = socket.getInputStream();
                 BufferedReader reader = new BufferedReader(new InputStreamReader(input));

                 BufferedReader consoleReader = new BufferedReader(new InputStreamReader(System.in));
                 String message;

                 while (true) {
                     System.out.print("Enter message: ");
                     message = consoleReader.readLine();
                     writer.println(message);

                     if (message.equalsIgnoreCase("exit")) {
                         break;
                     }

                     String response = reader.readLine();
                     System.out.println("Server: " + response);
                 }
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Xử Lý Nhiều Client

1. **Server:**
   - Để xử lý nhiều client cùng một lúc, bạn có thể sử dụng luồng (threads).
   - Ví dụ:
     ```java
     import java.io.*;
     import java.net.*;

     public class MultiClientServer {
         public static void main(String[] args) {
             try (ServerSocket serverSocket = new ServerSocket(12345)) {
                 System.out.println("Server is listening on port 12345");

                 while (true) {
                     Socket socket = serverSocket.accept();
                     System.out.println("Client connected");

                     new ClientHandler(socket).start();
                 }
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }

     class ClientHandler extends Thread {
         private Socket socket;

         public ClientHandler(Socket socket) {
             this.socket = socket;
         }

         public void run() {
             try (InputStream input = socket.getInputStream();
                  BufferedReader reader = new BufferedReader(new InputStreamReader(input));
                  OutputStream output = socket.getOutputStream();
                  PrintWriter writer = new PrintWriter(output, true)) {

                 String message;
                 while ((message = reader.readLine()) != null) {
                     System.out.println("Received: " + message);
                     writer.println("Echo: " + message);
                 }
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

## Kết Luận

Lập trình mạng là một kỹ thuật mạnh mẽ cho phép các ứng dụng giao tiếp với nhau qua mạng. Bằng cách sử dụng các lớp và giao diện trong thư viện `java.net`, bạn có thể tạo các ứng dụng mạng đơn giản như server và client, cũng như xử lý dữ liệu truyền qua lại giữa chúng.

Hy vọng qua bài viết này, bạn đã có cái nhìn tổng quan về lập trình mạng trong Java và cách áp dụng nó trong thực tế. Nếu bạn có bất kỳ câu hỏi hoặc gặp khó khăn nào, đừng ngần ngại cho tôi biết nhé! 🚀😊 Chúc bạn thành công!
