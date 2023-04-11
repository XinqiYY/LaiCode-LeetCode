# 408. Valid Word Abbreviation

## 题目

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### Leetcode链接：[https://leetcode.com/problems/valid-word-abbreviation/description/](https://leetcode.com/problems/valid-word-abbreviation/description/)

#### Youtube参考：

## 解法一

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> 1. 分别使用 i, j 指向两个string的index，i指向长，j指向短，使用while 循环，当两个index都不出界时
>    1. 如果当前 j 指向的string是数字，记录数字，每次记录时，j++, 直到 j 不是数字，i += num
>    2. 如果是char，对比两个字符，不符合的话return false，else i++, j++
> 2. 最后对比i 和 j 与两个string的index

#### <mark style="color:red;">注意：</mark>

## 代码

````java
```java
public boolean validWordAbbreviation(String word, String abbr) {
    int i = 0, j = 0;
    while (i < word.length() && j < abbr.length()) {
        if (abbr.charAt(j) >= '0' && abbr.charAt(j) <= '9') {
            if (abbr.charAt(j) == '0') {
                return false; // leading zeros are not allowed
            }
            int num = 0;
            while (j < abbr.length() && abbr.charAt(j) >= '0' && abbr.charAt(j) <= '9') {
                num = num * 10 + abbr.charAt(j) - '0';
                j++;
            }
            i += num;
        } else {
            if (word.charAt(i) != abbr.charAt(j)) {
                return false;
            }
            i++;
            j++;
        }
    }
    return i == word.length() && j == abbr.length();
}
```
````

#### TC & SC:&#x20;

> TC: O(m) --> 因为会跳过数字char，所以即使对比两个string，但也只走过m长度
>
> SC: O(1)
