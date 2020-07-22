## 题目链接

https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/

## 题目描述

```
把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

示例 1：
输入：[3,4,5,1,2]
输出：1

示例 2：
输入：[2,2,2,0,1]
输出：0

```

## 思路

* 采用二分法的思维方式,取数组的中点来进行比较
* 题目说将若干个元素搬到数组末尾,且输入的为递增排序的数组,所以最小值应该位于右边
* 取中点m,与右边的数进行比较
* 若 中点数number[m] > 右边数number[r], 所以，最小数的范围为[m+1,r]
* 若 中点数number[m] < 右边数number[r], 所以，最小数的范围为[l,m]
* 若 中点数number[m] = 右边数number[r], 无法确定最小数的范围。但是根据转移，如果右边还存在最小数，那么必定number[m]的数小，但是若右边不存在，那么number[m]或者说number[r]就为最小数

## 代码

```java
class Solution {
    public int minArray(int[] numbers) {
        int low = 0 , high = numbers.length-1;

        while (low < high)
        {
            int m = (low + high) / 2;
            if (numbers[m] > numbers[high])
                low = m+1;
            else if (numbers[m] < numbers[high])
                high = m;
            else
                high--;
        }

        return numbers[low];
    }
}
```