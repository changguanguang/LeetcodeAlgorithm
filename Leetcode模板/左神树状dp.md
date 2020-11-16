# 二叉树的最大路径之和



给定一个二叉树，请计算节点值之和最大的路径的节点值之和是多少。
这个路径的开始节点和结束节点可以是二叉树中的任意节点
例如：
给出以下的二叉树，
![img](https://uploadfiles.nowcoder.com/images/20200807/999991351_1596786349381_11531EA9352057ACF47D25928F132E96) 
返回的结果为6



1. 思路：

2. 步骤：

3. 代码：

      	

   ```java
   public class Solution {
       /**
        * 
        * @param root TreeNode类 
        * @return int整型
        */
       public int maxPathSum (TreeNode root) {
           // write code here
           return maxPathSum2(root).distance;
   
       }
       
       public Info maxPathSum2 (TreeNode root) {
           // write code here
         if (root == null) {
               return new Info(Integer.MIN_VALUE, Integer.MIN_VALUE);
           }
   
           int maxDistoHead = 0;
           int distance = 0;
   
           Info leftInfo = maxPathSum2(root.left);
           Info rightInfo = maxPathSum2(root.right);
   
   
           maxDistoHead = Math.max((leftInfo.maxDistoHead > 0 ? leftInfo.maxDistoHead : 0) + root.val,
                   (rightInfo.maxDistoHead > 0 ? rightInfo.maxDistoHead : 0 )+ root.val);
           int distance1 = (leftInfo.maxDistoHead > 0 ? leftInfo.maxDistoHead : 0) + root.val
                   + (rightInfo.maxDistoHead > 0 ? rightInfo.maxDistoHead : 0);
           int distance2 = Math.max(leftInfo.distance, rightInfo.distance);
           distance = Math.max(distance1, distance2);
   
           return new Info(maxDistoHead, distance);
   
   
       }
       
       class Info{
           int maxDistoHead;
           int distance;
           public Info(int maxDistoHead,int distance){
               this.maxDistoHead = maxDistoHead;
               this.distance = distance;
           }
       }
   }
   ```

   