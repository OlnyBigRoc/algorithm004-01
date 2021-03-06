## 位运算基础及实战要点

header 1 | header 2 | 示例 |
---|--- |---
左移 | << | 0011 => 0110
右移 | >> | 0110 => 0011
按位或 | \|  |  0011 =>1011 1011
按位与 | &   |  0011 =>0011 1011
按位取反 | ~   |  0011 => 1100
异或 | ^ | 0011 ^ 0110 => 0100


XOR -异或
1. x ^ 0 =X
1.  x ^ 1s =~x //注意1S = ~0;
1.  x ^ (~x) = 1s
1.  x ^ x = 0
1.  c = a ^ b => a ^ c =b,b ^ c = a //交换两个数
1.  a ^ b ^ c =a ^(b^c) = (a^b)^c’


指定位置的位运算
1. 将x最右边的n位清零: x&(0<< n)
2. 获取x的第n位值(0或者1) : (x>>n) & 1
3. 获取x的第n位的幂值: x&(1 <<(n-1))
4. 仅将第n位置为1: x|(1 <<n)
5. 仅将第n位置为0: x&((1 << n))
6. 将x最高位至第n位(含)清零:X&((1 <<n) -1)
7. 将第n位至第0位(含)清零: x&(~((1 <<(n+ 1))- 1))

实战位运算要点
1. 判断奇偶：
X%2==1-->(x& 1) ==1
x%2==0-->(x& 1) ==0
2. x>>1 ->x/2
3. X=X& (X-1)清零最低位的1
4. X&-X=>得到最低位的1
5. X &~X=> 0



## 布隆过滤器
- 优点：优点是空间效率和查询时间都远远超过一般的算法;

- 缺点：缺点是有一定的误识别率和删除困难。          

一般用布隆过滤器去查是否存在，有一位为0则肯定不存在，反之可能存在，需要进一步去查询（查库等） 


- 案例
  比特币网络
  分布式系统 （Map Reduce）Hadoop、   search engine
  Redis缓存
  垃圾邮件、评论等过滤
  
  
## LRU Cahe
  两要素：大小（缓存的大小，超过该大小，根据替换策略执行替换）、替换策略（超出大小的替换原则）
  
  数据结构：Hash Table + Double LinkedList;
  
   时间复杂度：查询-->O(1)；修改、更新-->O(1
  
  )替换策略：LFU-least frequently used（最不常用替换）、LRU-least recently used(最近最少使用替换)
 
##排序
![image](https://images2018.cnblogs.com/blog/849589/201804/849589-20180402133438219-1946132192.png)

- 重点nlogon  堆排序、 快速排序、归并排序
总体分为 比较类和非比较类

![image](https://img2018.cnblogs.com/blog/849589/201903/849589-20190306165258970-1789860540.png)

###初级
选择 插入 冒泡

###高级
- 归并排序 （Merge Sort） - 分治
- 堆排序

###特殊
计数排序、桶排序、基数排序
