### Left View of Binary Tree

**Easy**Accuracy: **33.74%**Submissions: **471K+**Points: **2**

[

Get Internship at GfG by submitting your Entries in: Data Science Blogathon

![banner](https://media.geeksforgeeks.org/img-practice/external-1657081738.svg)

](https://www.geeksforgeeks.org/data-science-blogathon/)

Given a Binary Tree, return Left view of it. Left view of a Binary Tree is set of nodes visible when tree is visited from Left side. The task is to complete the function **leftView()**, which accepts root of the tree as argument. If no left view is possible, return an empty tree.

Left view of following tree is 1 2 4 8.

 1  
       /     \\  
     2        3  
   /     \\    /    \\  
  4     5   6    7  
   \\  
     8 

**Example 1:**

**Input:**    1
 /  \\
3    2
**Output:** 1 3 

**Example 2:**

**Input:** ![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20190221103723/leftview.jpg)
**Output:** 10 20 40 

**Your Task:**  
You just have to **complete** the function **leftView()** that returns an array containing the nodes that are in the left view. The newline is automatically appended by the driver code.  
**Expected Time Complexity:** O(N).  
**Expected Auxiliary Space:** O(N).

**Constraints:**  
0 <= Number of nodes <= 100  
0 <= Data of a node <= 1000