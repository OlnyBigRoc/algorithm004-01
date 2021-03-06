# 1.学习总结

## 1.1关于新算法知识的理解

#### 【536-Week1】关于跳表的理解
    本周对相对陌生的跳表进行总结，以掌握思想为主，通过课上学习和查找相关材料，总结内容包括：

    1、跳表的定义；

    2、跳表的相关操作及实现思路；

    3、跳表的应用；
###### 第一部分：跳表的定义
   跳跃表（Skip List）是1987年才诞生的一种崭新的数据结构，它在进行查找、插入、删除等操作时的时间复杂度均为O(logn),有着近乎替代平衡树的本领。而且最重要的一点，就是它的编程复杂度较同类的AVL树，红黑树等要低得多，这使得其无论是在理解还是在推广性上，都有着十分明显的优势。

   1、跳跃表的结构
   
    跳跃表由多条链构成（S0，S1，S2 ……，Sh），且满足如下三个条件：
   
    （1）每条链必须包含两个特殊元素：+∞ 和 -∞；
  
    （2）S0包含所有的元素，并且所有链中的元素按照升序排列；

    （3）每条链中的元素集合必须包含于序数较小的链的元素集合。
   
   2、跳跃表的时间及空间复杂度
   
    空间复杂度： O(n)
   
    时间复杂度：
   
	(1)查找：	 O(logn)	
	
	(2)查找： 	 O(logn)	
   
	(3)删除：	 O(logn)	

###### 第二部分：跳表的相关操作及实现思路
   操作包括查找、插入、删除，各操作实现思路如下：
   
   1、查找
     
     在跳跃表中查找一个元素x，按照以下步骤进行：
     
     从最上层的链（Sh）的开头开始
     
     假设当前位置为p，它向右指向的节点为q（p与q不一定相邻），且q的值为y。将y与x作比较
      
     x=y		输出查询成功，输出相关信息
     
     y<x		从p向右移动到q的位置
     
     y>x		从p向下移动一格

     如果当前位置在最底层的链中（S0），且还要往下移动的话，则输出查询失败。

   2、插入
   
      在跳跃表中插入一个元素x，按照以下步骤进行：
      
      插入的位置和插入对应元素。
      
      当我们往跳表中插入数据的时候，我们可以通过一个随机函数，来决定这个结点插入到哪几级索引层中，
      
      随机函数的选择是非常有讲究的，从概率上讲，能够保证跳表的索引大小和数据大小平衡性，不至于性能的过度退化。
      
      至于随机函数的选择，见下面的C++代码实现：
        /***** 随机函数起始********/
	private int randomLevel()
	{
		int level = 1;
		for(int i = 1; i < MAX_LEVEL; ++i)//MAX_LEVEL为链条数
		{   
			if(random.nextInt() % 2 == 1){
				level++;
			}
		}		
		return level;
	}
	/******随机函数结束********/
   3、删除
         
     从跳跃表中删除一个元素x，按照以下步骤进行：
     
     1）在跳跃表中查找到这个元素的位置，如果未找到，则退出
     
     2）将该元素所在整列从表中删除
     
     3）将多余的“空链”删除	

###### 第三部分：跳表的应用
  使用跳跃表的产品：
      
    1、Lucene, elasticSearch

    2、Redis：
    
     Redis sorted set的内部使用HashMap和跳跃表(SkipList)来保证数据的存储和有序，
     
     HashMap里放的是成员到score的映射，而跳跃表里存放的 是所有的成员，排序依据是HashMap里存的score,
     
     使用跳跃表的结构可以获得比较高的查找效率，并且在实现上比较简单。

###### 写在最后

     1、要深刻理解跳表，需要自己动手用代码实现一遍，这个暂且搁置后续实现；
     
     2、leetcode涉及跳表题目：1206 设计跳表；

## 1.2其他感想

#### 算法学习习惯的探索

覃超老师说过算法学习需要刻意练习，印象最深的就是“五毒神掌”，相同的题目要不断的刷。道理很简单，但真正做到有难度，因为工作较忙，结合实际情况，只能减少遍数，我的算法学习步骤大致计划如下：

1、覃超老师的在线课程先听一遍，在听的过程中，涉及算法例题讲解的部分，自己同步在纸上写思路，和手写源码；

   注：第一遍主要是完成课程，了解知识点。
   
2、听完在线课程后，针对例题和练习题，学习leetcode上经典题解，每题在IDE里至少两种解法编写，提交leetcode；

   注：第二遍主要是刻意练习，巩固知识点。
   
3、对于做过的题目，跳出自己认为难理解、容易忘的题目再次IDE里编写，提交leetcode；

   注：第三遍主要是查漏补缺，掌握知识点。


---

# 2.改写代码和分析源码
主要用C/C++，不熟悉Java

---

# 3.Review和点评



