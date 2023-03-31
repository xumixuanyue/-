# 什么时候需要用虚拟头结点？  
总结一下：当需要创造一条新链表的时候，可以使用虚拟头结点简化边界情况的处理。

# 遇到一道二叉树的题目时的通用思考过程是：  
&emsp;&emsp;1、是否可以通过遍历一遍二叉树得到答案？如果可以，用一个 traverse 函数配合外部变量来实现。  
&emsp;&emsp;2、是否可以定义一个递归函数，通过子问题（子树）的答案推导出原问题的答案？如果可以，写出这个递归函数的定义，并充分利用这个函数的返回值。  
&emsp;&emsp;3、无论使用哪一种思维模式，你都要明白二叉树的每一个节点需要做什么，需要在什么时候（前中后序）做。  

&emsp;&emsp;一旦你发现题目和子树有关，那大概率要给函数设置合理的定义和返回值，在后序位置写代码了。

&emsp;&emsp;动态规划的核心思想就是穷举求最值，但需要熟练掌握递归思维，只有列出正确的「状态转移方程」，才能正确地穷举。  
&emsp;&emsp;而且，需要判断算法问题是否具备「最优子结构」，是否能够通过子问题的最值得到原问题的最值。  
&emsp;&emsp;另外，动态规划问题存在「重叠子问题」，如果暴力穷举的话效率会很低，所以需要使用「备忘录」或者「DP table」来优化穷举过程，避免不必要的计算。   
&emsp;&emsp;重叠子问题、最优子结构、状态转移方程就是动态规划三要素，但是在实际的算法问题中，写出状态转移方程是最困难的。

# 动态规划框架
![image](https://user-images.githubusercontent.com/90192841/227175873-c080b027-14b7-41ee-b5de-fe3930518d02.png)
### 动态规划典型题目（未解决）
322
# 递归算法的时间复杂度怎么计算？
就是用子问题个数乘以解决一个子问题需要的时间。

# 回溯算法的框架
![image](https://user-images.githubusercontent.com/90192841/227175598-13a64c58-47a9-40a3-8c92-464fcab145cd.png)  
回溯算法时间复杂度不可能低于 O(N!)，因为穷举整棵决策树是无法避免的。这也是回溯算法的一个特点，不像动态规划存在重叠子问题可以优化，回溯算法就是纯暴力穷举，复杂度一般都很高。
### 解决一个回溯问题，实际上就是一个决策树的遍历过程，站在回溯树的一个节点上，你只需要思考 3 个问题：
1、路径：也就是已经做出的选择。  
2、选择列表：也就是你当前可以做的选择。  
3、结束条件：也就是到达决策树底层，无法再做选择的条件。
# 回溯算法解决所有排列/组合/子集问题
### 形式一、元素无重不可复选，即 nums 中的元素都是唯一的，每个元素最多只能被使用一次  
&emsp;&emsp;子集：使用 start 参数控制树枝的遍历，避免产生重复的子集；同时用 track 记录根节点到每个节点的路径的值，同时在前序位置把每个节点的路径值收集起来，完成回溯树的遍历就收集了所有子集  
&emsp;&emsp;组合：遍历同子集，选择时在base case加上相应条件即可  
&emsp;&emsp;排列：使用used 数组标记已经在路径上的元素，避免重复选择  
### 形式二、元素可重不可复选，即 nums 中的元素可以存在重复，每个元素最多只能被使用一次  
&emsp;&emsp;子集/组合：将nums进行排序；使用 start 参数控制树枝的遍历，避免产生重复的子集；使用nums[i] == nums[i - 1]进行剪枝（剪枝逻辑：值相同的相邻树枝，只遍历第一条）  
&emsp;&emsp;排列：将nums进行排序；使用used 数组标记已经在路径上的元素，避免重复选择；使用nums[i] == nums[i - 1] and !used[i - 1]进行剪枝（或使用preNum记录前一条树枝的值，使用nums[i] == preNum进行剪枝）  
### 形式三、元素无重可复选，即 nums 中的元素都是唯一的，每个元素可以被使用若干次  
&emsp;&emsp;子集/组合：在元素无重不可复选的子集/组合问题中，使用start参数控制树枝的遍历，下一层回溯树从i + 1开始，在元素无重可复选问题中，只需要使下一层回溯树从i开始就行  
&emsp;&emsp;排列：在元素无重不可复选的基础上，去除uesd数组操作即可  
# DFS算法、BFS算法
### DFS算法就是回溯算法  
### BFS算法核心思想：  
&emsp;&emsp;就是一幅[图]，让你从一个起点start，走到终点end，问最短路径。一般来说，我们写BFS算法都是用[队列]这种数据结构，每次将一个节点周围的所有节点加入队列。  
&emsp;&emsp;BFS相对DFS的最主要的区别是：BFS找到的路径一定是最短的，但代价就是空间复杂度可能比DFS大很多  
![image](https://user-images.githubusercontent.com/90192841/227970145-a61a0d99-0b55-4c73-8165-d818010b4bc1.png)  
# 二分搜索算法
