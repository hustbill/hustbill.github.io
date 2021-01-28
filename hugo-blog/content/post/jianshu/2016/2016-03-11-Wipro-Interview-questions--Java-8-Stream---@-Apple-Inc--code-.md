---
title: "Wipro Interview questions- Java 8 Stream - @ Apple Inc. code "
date: "2016-03-11 09:17:46"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
```java

import java.util.*;

public class StreamDemo {

 public static void main(String[] args) {
  // TODO Auto-generated method stub
  List<Book> libray = new ArrayList<Book>();
  libray.add(new Book("hua", "Stream Demo", 5));
  libray.add(new Book("hua", "Do more practice", 5));
  libray.add(new Book("hua", "Focus on basics", 5));
  String authorName = "hua";

  List<String> collection = new ArrayList<String>();
  libray.stream().filter(e -> e.getAuthor() == authorName).forEach(e -> collection.add(e.getName()));
  System.out.print(collection);
 }

}

class Book {
 String author;
 String name;
 int number;

 public Book(String authorName, String bookName, int num) {
  author = authorName;
  name = bookName;
  number = num;
 }

 public String getAuthor() {
  return author;
 }

 public String getName() {
    return name;
 }

 public int getNumber() {
  return number;
 }

 public void setNumber(int num) {
  number = num;
 }
}
```
