---
title: "2016-04-03-Collective Health HackerRank OA"
date: "2016-04-04 07:30:45"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
*Collect Health Software Engineer OA*  
要求在20分钟内完成所有的题目，不能copy 和paste答案。题目都比较基础，现场搜google 有点来不及。还是靠自己平时的积累。里面有好几套题。我因为时间紧张，就选第一套来完成了。  


1. 时间复杂度
```python
func removeChar (String input, String illeagePattern) {
     for (char x : illeagePattern) {
         input.remove(x);
     }
}
```
选项有
O(n), O(2n), O(nm), O(nlogn)
我选的 O(nm);

2. unit test 
```code
"signal failure within a unit test"  
题干没记全，这题没把握，我选的是 assert  
```
参考： 
Wikipedia:  It is generally possible to perform unit testing without the support of a specific framework by writing client code that exercises the units under test and uses assertions, exception handling, or other control flow mechanisms to signal failure

3. coding question 
```javascript
var add: () -> Int = {
  var counter = 0;
  return {counter = counter + 2; return counter}
}()
print(add())
print(add())
```
运行输出结果是 ？  
备选项有  
2  
4  
我给的答案是 None of above  

4. HTTP
From the list of http methods please select ALL that are reasonable to alter data:
我给的是  post, put, delete  

5. coding question 
```javascript
func multiplyPriors(n: Int) -> Int {
  switch n {
  case 0:
    return 1
  case 1:
    return 2
  default:
    return multiplyPriors(n-1) * multiplyPriors(n-2)
  }
}
```
算法复杂度是____   
选项是 O(n), O(2n), O(n^2), O(nlogn)  

6. 分析上述程序，可能的结果    
我选的是 stack overflow  when large n   

7. 计算结果 multiplyPriors(4)=_____  
我的答案是 8  

8. n/a 

9. 给出orders表
```sql
 ----------------------------
name             |  type
orderNumber (pk) |  number
Status           |  varchar50
 ----------------------------
-- Status = 'Shipped'
-- 求所有没有shipped订单数
select count(*) from ORDERS where status <> 'Shipped';  
```

10. 求top 5的没有shipped的订单  
select * from ORDERS  where status <> 'Shipped' limit 5;
