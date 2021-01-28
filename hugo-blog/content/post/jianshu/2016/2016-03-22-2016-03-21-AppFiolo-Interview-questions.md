---
title: "2016-03-21-AppFiolo Interview questions"
date: "2016-03-22 07:19:17"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
AppFolio, Inc.(NASDAQ:APPF)成立于2006年，总部位于美国加州圣巴巴拉，创始人为加州大学前计算机科学教授克劳斯·绍瑟尔(Klasu Schauser)和琼·沃克尔(Jon Walker)，是一家物业管理软件开发公司。

AppFolio creates complete, easy-to-use, cloud-based software for multiple vertical markets. 

![AppFolio Property Manager](/static/images/面试题/1647554-8c6bef1ed2d2025c.png)
## General questions
1. How to know AppFilo? Why AppFilo?
2. introduce your projects and tech stacks
3. Node.js, which kind of framework you used ?


## Tech questions

1. Tell me about the data schema and programming in PostgreSQL

2. What you did in MongoDB?

3. How to use the ElasticSearch in your project?

## Coding questions
- Reverse the words in the string, without java.util method - split
for example: 
Today     is Monday March 21st=>  21st March  Monday  is          Today

### 3/22/16 update
**这个是更精炼的解法**
```java
import java.util.*;

public class ReverseString{
	public static String reverseWordsInString(String s) {
		StringBuilder res = new StringBuilder(); 
		int j = s.length();
		
        for (int i = s.length() - 1; i >= 0; i--) {
            if (s.charAt(i) == ' ') {
                j = i;
            } else if (i == 0 || s.charAt(i-1) == ' ') {
                
                if (res.length() != 0) {
                    res.append(' ');
                }
                res.append(s.substring(i,j));
            }
        }
        return res.toString();
	}
}
	
```

旧的解法，留个纪念
```java
import java.util.*;

public class ReverseString{

    public static void main(String[] args) {

        String str = "Today     is Monday March 21st";
        System.out.println(str);
        System.out.print("=> " + reverseStr(str));
    }

    public static String reverseStr(String str) {
        // split string to multiple words
        LinkedList<String> list = new LinkedList<>();
        
        // check the whitespace , split string by whitespace
        int n = str.length();
        int left = 0, right = 0; 
        int index = 0;

        for (int i=0; i < n; i++){
            right++;
            if(str.charAt(i) == ' ') {
                String temp = str.substring(left, right);
                list.add(index, temp); 
                left = right;
                index++;
            }
        }
           // add the last word int the string
        list.add(index, str.substring(left, right));

        StringBuilder sb = new StringBuilder();
        for (int j=list.size() -1; j >= 0; j--) {
           sb.append(list.get(j) + " " );
         }
        return sb.toString();
    }
}

```

-  Update the code using OOP concept

```Ruby
class Meeting

end

class Interview

end

class DesignReview

end

class Scheduler

  def schedulable?(target, start_date, end_date)
    if target.is_a?(Meeting)
      return end_date - (start_date - 5.days) > 10.days
    elsif target.is_a?(Interview)
      return start_date > (end_date - 2.days)
    elsif target.is_a?(DesignReview)
      return (end_date + 10.days) - start_date > 15.days

    
    end
  end

end

targets = [ Meeting.new, Interview.new, DesignReview.new ]
scheduler = Scheduler.new

targets.each do |target|
  if scheduler.schedulable?(target, Clock.today, Clock.today + 10)
    puts "The #{target.class.name} can be scheduled"
  end
end
```

＃＃尾声
让面试官给推荐了一本书，
Agile Web Development with Rails 4 (Facets of Ruby) 1st Edition
