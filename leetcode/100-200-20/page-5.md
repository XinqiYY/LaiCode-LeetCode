# 190. Reverse Bits

## 题目

![](<../../.gitbook/assets/image (32) (1).png>)

#### Leetcode链接：[https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)

#### Youtube参考：

## 解法一

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> * 反转十进制整数
>   * res = res \* 10 + n % 10;
>   * n /= 10
> * 反转二进制整数
>   * res = res \* 2 + n % 2;
>   * n /= 2;
> * 反转二进制, 基于左右shift的特性，左 \* 2，右 / 2
>   * res = (res << 1) | (n & 1);
>   * n >>= 1;&#x20;

#### <mark style="color:red;">注意：</mark>

## 代码

```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        int res = 0;
        for (int i = 0; i < 32; i++) {
            res = (res << 1) | (n & 1);
            n >>= 1;
        }
        
        return res;
    }
}
```

#### TC & SC:&#x20;

> TC: O(32次) --> O(1)
>
> SC: O(1)
