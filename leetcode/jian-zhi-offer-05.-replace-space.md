# 剑指Offer 05. Replace Space

## 题目

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Leetcode链接：[https://github.com/youngyangyang04/leetcode-master/blob/master/problems/%E5%89%91%E6%8C%87Offer05.%E6%9B%BF%E6%8D%A2%E7%A9%BA%E6%A0%BC.md](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/%E5%89%91%E6%8C%87Offer05.%E6%9B%BF%E6%8D%A2%E7%A9%BA%E6%A0%BC.md)

#### 参考：

## 解法一

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> * 除了stringbuilder，还可以用stringbuilder找出空格并且为此扩充两个位置，将扩充好的spaces的长度加到原有的string长度上，重新建立一个数组
> * 双指针如果left是空格，则右边append一个"%20" else append字符

#### <mark style="color:red;">注意：</mark>

## 代码

```java
public String replaceSpace(String s) {
    if(s == null || s.length() == 0){
        return s;
    }
    //扩充空间，空格数量2倍
    StringBuilder str = new StringBuilder();
    for (int i = 0; i < s.length(); i++) {
        if(s.charAt(i) == ' '){
            str.append("  "); // 这里是两个空格
        }
    }
    //若是没有空格直接返回
    if(str.length() == 0){
        return s;
    }
    //有空格情况 定义两个指针
    int left = s.length() - 1;//左指针：指向原始字符串最后一个位置
    s += str.toString();
    int right = s.length()-1;//右指针：指向扩展字符串的最后一个位置
    char[] chars = s.toCharArray();
    while(left>=0){
        if(chars[left] == ' '){
            chars[right--] = '0';
            chars[right--] = '2';
            chars[right] = '%';
        }else{
            chars[right] = chars[left];
        }
        left--;
        right--;
    }
    return new String(chars);
}
```

#### TC & SC:&#x20;

> TC: O(n)
>
> SC: O(11)

## **Similar Questions:**&#x20;
