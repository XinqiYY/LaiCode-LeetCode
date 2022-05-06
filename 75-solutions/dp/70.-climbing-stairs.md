# 70. Climbing Stairs

## 题目

![](<../../.gitbook/assets/image (146) (1).png>)

#### Leetcode链接：[https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)

#### Youtube参考：

## 解法一: DP & Fibonacci

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> * 楼梯为1或2是等于它自身。
> * 楼梯之后的结果，都为dp\[i - 1] + dp\[i - 2]之和。因为只需要读取两个值，所以可以只使用variable

#### <mark style="color:red;">注意：</mark>

## 代码

```java
class Solution {
    public int climbStairs(int n) {
        if (n == 1) return 1;
        
        int first = 1;
        int second = 2;
        for (int i = 3; i <= n; i++) {
            int third = first + second;
            first = second;
            second = third;
        }
        return second;
    }
}
```

#### TC & SC:&#x20;

> TC: O(n)
>
> SC: O(1)
