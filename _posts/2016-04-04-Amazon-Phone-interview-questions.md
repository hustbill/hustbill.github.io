---
layout: post
title: "亚麻电面题"
date: 2016-04-04 11:50:00
categories: jekyll update
---

# *Question*

You’ve got a text file that contains x,y,z-coordinate points for every star in the sky (on the order of 1 billion (this is N)). I
want to know the 100 (or K) closest stars to earth, how would you compute that? earth = 0, 0, 0

# *Solution*  
(1) Split the file by N= 10000 lines,  and calculate the distance, define a class Star with comparable  
(2) use a Priority queue  
(3) Fill the heap with first 100 (k) values  
(4) Comapre each new value with the top of heap  
     -  if bigger do nothing  
     -  if smaller replace top of the heap  
Finally, the heap contains top 100 closest stars.   

Attached file is my sample source code. Your suggestions are highly appreciated!  


# *Code*
```java 
import java.util.*;

public class KthClosestStarFinder{

    public static Star findClosest(Star[] sky, int k) {
        PriorityQueue<Star> pq = new PriorityQueue<Star>();

        int N = sky.length;
        if (N <= k) return sky[N-1];

        for (int i = 0; i < k; i++)
            pq.add(sky[i]);

        for (int i = k; i < N; i++) {
            Star mystar = sky[k];
            if (mystar.compareTo(pq.peek()) < 0) {
                pq.remove();
                pq.add(mystar);
            }
        }
        return pq.peek();
    }
    
    public static void main(String[] args) {
        int N = 1000000, k = 100;
        Star[] sky = new Star[N];
        Random random = new Random();
        
        for (int i = 0 ; i < N  ; i++) {
            sky[i] = new Star(i, 100 + random.nextInt(1000) + i  );
            //System.out.print(sky[i].getDistance() + " , ");
        }
        
        Star res = findClosest(sky, k);
        System.out.printf("The 100 closest star is: %d, distance : %.2f",
             res.getId(), res.getDistance());
    }
}


class Star implements Comparable<Star> {
    public int id;
    public float dst;
    public Star(int id, float dst) {
        this.id = id;
        this.dst = dst;
    }
    
    public int getId() {
        return id;
    }
    public float getDistance() {
        return dst;
    }

    public int compareTo(Star other) {
        if (this.dst > other.dst) 	return 1;
        if (this.dst < other.dst) 	return -1;
        return 0;
    }
} 
```