# partition排序（分区--一趟扫描定区间）



## 数组partition

给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

注意:
不能使用代码库中的排序函数来解决这道题。

示例:

输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]
进阶：

一个直观的解决方案是使用计数排序的两趟扫描算法。
首先，迭代计算出0、1 和 2 元素的个数，然后按照0、1、2的排序，重写当前数组。
你能想出一个仅使用常数空间的一趟扫描算法吗？  

```java
class Solution {
    // 输入: [2,0,2,1,1,0]
    // 输出: [0,0,1,1,2,2]
    public void sortColors(int[] nums) {

        /**
            Partition
            [0,zreo)  all is 0
            [zero,i)  all is 1
            [i,len-1] all is 2

        */

        //特判
        if(nums.length == 0 || nums.length == 1){
            return ;
        }

        int len = nums.length;
        //置zero为0，使得初始的0号区间长度为0
        int zero = 0;
        //置two为le，使得初始的2号区间长度为0
        int two = len;

        int i=0;
        while(i<two){

            if(nums[i] == 0){
                //因为0号区间不包含zero，所以先交换，再自增
                swap(nums,zero,i);
                zero++;
                i++;
            }else if(nums[i] == 1){
                //如果是1，那么直接往后走，0号区间和二号区间不用动
                i++;
            }else{
                //因为two表示2号区间的开头，所以先 -- ，再交换
                two--;
                swap(nums,i,two);
            }

        }

    }
    public void swap(int[] nums,int i,int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
 JDK 的源码中 `Arrays.sort()` 。

![image.png](https://pic.leetcode-cn.com/0ff67b77154bcea4b85faeceb23b80062f82c20c137a6d8332ad068e624531f8-image.png)

- 按照数字顺序排列指定的数组。

  实施注意事项：排序算法是由Vladimir Yaroslavskiy，Jon Bentley和Joshua  Bloch提供的双轴快速排序。 该算法在许多数据集上提供O（n  log（n））性能，导致其他快速排序降级为二次性能，并且通常比传统（单轴）Quicksort实现更快。 



## 链表partition



