---
layout: post
title: "NimbleRx [onsite interview]."
date: 2016-05-13 20:00:00
categories: [个人笔记]
---


## 第一个面试工程师
Dana (Software Engineer) 8:30 - 9:45
很资深的工程师，做过开发和管理， 用过c++， python 之类的开发语言。 现在开始转作java开发， 一开始给我讲了NimbleRx 公司的系统架构和她负责那一块东西。

1. Two sum 变体，用hashMap来做，map.containsKey(sum - arr[i]) 
 Follow up:  如果不能用额外的空间
 我说 Arrays.sort, 然后用binary search， 她说，在binary search之前，你怎么sort array。 我就随便说了insert search 。她否定了，还是得用额外的空间，那我又说merge sort ，被否定后。 她说可以用 quick sort

2. common father of two nodes in Binary tree
这道题，我之前做过，临时想不起来方法， 只记得要保存访问过的node
在问她要提示以后，勉强做出来了。

## 第二个面试工程师
Amy (Software Engineer) 9:45 - 1100  (7年工作经验） qa出身，IBM干过， 熟悉db2

主要问了很多测试的问题，各种测试的项目

1.test scenario : pharmacy, doctor, patient, driver , 的流程， 如何测试， 怎样保证正确性  

     take picture 来验证是否收到货

2. test an user registration page:  username and password,  username is an email address, password have a list of limitation  
    - least 6 characters  
    - at least one Capital character  
    - 1 number  
    - 1 low case  
    - 1 special character  

3. test text box:  (Country, unicode , utf-8,   multi-line, 

4. test number:  ( 360-553-2098, phone number? )  need to be calculate,  the range of number , 

5. how to evaluate the relation between developer and QA? 

5.matrix (code, test cases, test plans) 
   1).valid test cases 
   2). invalid test cases 
      * a. data related vs non data related
      * b. severity 
      * c. UI related or backend API 
      * d. module, domain,

## 中途进来一个人 Tyler  
不是做技术的。 和他聊了会儿天。带我去取吃的食物。

## Lunch (Engineering team)  Yulei

lulei 是华人工程师，给我讲了公司的一些情况，一起吃饭，了解了一些相互的情况。 他给我介绍了公司的一些项目和开发的情况: 既做Node.js＋ Express + MongoDB, 又做 Java ＋ spring ＋ Hibernate ＋ mysql， 服务器部署到 AWS 的开发（s3 + Elastic Beanstalk) 

## 第三个面试工程师
Alan (Software Engineer)1:00 - 2:00

出了两道题
1. isValidXml (List<Tag> list)  
 
```java
class  Tag {
    String  getTageName();  // return the tag, ex, html
     boolean isOpen();
     boolean isClose();
}
```

<html> <body> </body> </html>  
这道题很类似[leetcode] [Valid Parentheses](https://[leetcode].com/problems/valid-parentheses/)

```java
isValidXml (List<Tag> list ) {
  Stack<Tag> st = new Stack<Tag>();
  for (Tag tag : list ) {
    if ( tag.isOpen()) {
        st.push(tag.getTagName());
    }
    if (tag.isClose()  && st.peek() == tag.getTagName()) {
     st.pop();
     } else {
      return false;
     }
 }
  return st.size() == 0; 
}
```

2.Connect nodes at same level
问他要了提示， 磕磕巴巴写完程序  

```java
// Java program to connect nodes at same level 
// NimbleRx coding question 
// Date: 2016-05-12

// A binary tree node
class Node {

	int val;
	Node left, right, next;

	Node(int item) {
		val = item;
		left = null;
		right = null;
		next = null;
	}
}

public class ConnectedTree {

	static Node root;

	// set the next of root and calls helper recursively for other nodes
	void connectNodes(Node p) {
		p.next = null; // Set the next for root

		// recursively set the next for rest of the nodes
		helper(p);
	}

	// set next of all descendants of p.
	public void helper(Node p) {

		if (p == null) {
			return;
		}

		if (p.left != null) {
			p.left.next = p.right;
		}

		// set the next node for p's right child
		if (p.right != null) {
			if (p.next != null) {
				p.right.next = p.next.left;
			} else {
				p.right.next = null; // if p is the right most child at its
										// level
			}
		}

		// Set next for other nodes
		helper(p.left);
		helper(p.right);
	}

	public static void main(String args[]) {
		ConnectedTree tree = new ConnectedTree();
		tree.root = new Node(10);
		tree.root.left = new Node(8);
		tree.root.right = new Node(2);
		tree.root.left.left = new Node(1);
		tree.root.left.right = new Node(4);
		
		tree.root.right.left = new Node(7);
		tree.root.right.right = new Node(3);

		// set next nodes in all nodes
		tree.connectNodes(root);

		// Let us check the values of next nodes
		System.out.println("Check the next node in the ConnecteTree " );
		System.out.println("Print -1 if there is no next node :\n");
		
		int rootNext = root.next != null ? root.next.val : -1;
		System.out.println("next of " + root.val + " is " + rootNext);

		int leftNext = root.left.next != null ? root.left.next.val : -1;
		System.out.println("next of " + root.left.val + " is " + leftNext);

		int rightNext = root.right.next != null ? root.right.next.val : -1;
		System.out.println("next of " + root.right.val + " is " + rightNext);
		
		int leftLeftNext = root.left.left.next != null ? root.left.left.next.val : -1;
		System.out.println("next of " + root.left.left.val + " is " + leftLeftNext);  //4
		
		int leftRightNext = root.left.right.next != null ? root.left.right.next.val : -1;
		System.out.println("next of " + root.right.right.val + " is " + leftRightNext);  //7
		

	}

}
```


## 第四个面试官
Duy (Head of Engineering) 14:00 - 14:40

The interviewer asked me to sum (Collection<Object> objects). The objects are possible ( string, number, List, Set or HashMap). I need to check the objs’  type, and sum the values of the objects. Skip the strings of Objects.   

```java
Collection<Object>

1.245
“2.345"
List
HashMap<k, v>
Pojo  { 
          person {
               int id
               String name
   }
```
分两步做
1) How to deal with List, Set, Map, refer to Check if Object is instance of String, HashMap, or HashMap[ ]
obj.instanceOf();

2). How to deal with PoJO, refer to how to get fields from a pojo dynamically
You may use java reflection. For simplicity I assume your Employee calss only contains int field. But you can use the similar rules used here for getting float, double or long value.

```java
package com.hustbill;

import java.lang.reflect.Field;
import java.util.List;

class Person {

	private int salary = 100;
	private int tips = 20;
	private int benefit = 25;
	private int cashBack = 30;
	
}

public class PojoDemo {

	public static void main(String[] args) throws NoSuchFieldException, IllegalAccessException {

		int sum = 0;
		Person Person = new Person();
		Field[] allFields = Person.getClass().getDeclaredFields();

		for (Field each : allFields) {

			if (each.getType().toString().equals("int")) {

				Field field = Person.getClass().getDeclaredField(each.getName());
				field.setAccessible(true);

				Object value = field.get(Person);
				Integer i = (Integer) value;
				sum = sum + i;
			}

		}

		System.out.println("Sum :" + sum);
	}

}

```

## 第四个是 Evance
Sr. Software Engineer 14:40 - 15:30

He asked me introduce my projects and architecture. Also, asked me to introduce infrastructure of ELK (ElasticSearch, Logstash, Kibana) 


## Reference
 Connect nodes at same level

### Method 1 (Extend Level Order Traversal or BFS)
Consider the method 2 of [Level Order Traversal](http://www.geeksforgeeks.org/archives/2686). The method 2 can easily be extended to connect nodes of same level. We can augment queue entries to contain level of nodes also which is 0 for root, 1 for root’s children and so on. So a queue node will now contain a pointer to a tree node and an integer level. When we enqueue a node, we make sure that correct level value for node is being set in queue. To set nextRight, for every node N, we dequeue the next node from queue, if the level number of next node is same, we set the nextRight of N as address of the dequeued node, otherwise we set nextRight of N as NULL.
Time Complexity: O(n)

### Method 2 (Extend Pre Order Traversal)
This approach works only for [Complete Binary Trees](http://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees). In this method we set nextRight in Pre Order fashion to make sure that the nextRight of parent is set before its children. When we are at node p, we set the nextRight of its left and right children. Since the tree is complete tree, nextRight of p’s left child (p->left->nextRight) will always be p’s right child, and nextRight of p’s right child (p->right->nextRight) will always be left child of p’s nextRight (if p is not the rightmost node at its level). If p is the rightmost node, then nextRight of p’s right child will be NULL.
