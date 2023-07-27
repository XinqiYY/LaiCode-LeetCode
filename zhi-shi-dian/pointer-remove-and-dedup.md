# Pointer Remove & Dedup

## 什么是双指针

> 指针start的责任？初始值？

* Start 的责任是用来 update 符合条件的element

> 指针 i 的责任？初始值？

* i 的责任是查找还未处理过的 element，找出符合条件的

> 什么条件下，nums\[start] = nums\[i]

* 根据每个题的要求不同条件也不同

## Relate Topics:

[27 . Remove Element](https://leetcode.com/problems/remove-element/)

```java
public int removeElement(int[] a, int val) {
    int start = 0;
    
    for (int i = 0; i < a.length; i++) {
        if (a[i] != val) {
            a[start++] = a[i];
        }
    }

    return start;
}
```

[283 . Move Zeroes](https://leetcode.com/problems/move-zeroes/)

```java
public void moveZeroes(int[] a) {
    int start = 0;
    for (int i = 0; i < a.length; i++) {
        if (a[i] != 0) {
            a[start++] = a[i];
        }
    }

    for (int i = start; i < a.length; i++) {
        a[i] = 0;
    }
}
```

[26 . Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

```java
public int removeDuplicates(int[] a) {
    int start = 1;
    
    for (int i = 1; i < a.length; i++) {
        if (a[i] != a[i - 1]) {
            a[start++] = a[i];
        }
    }

    return start;
}
```

[80 . Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

```java
public int removeDuplicates(int[] a) {
    int start = 2;

    for (int i = 2; i < a.length; i++) {
        if (a[i] != a[start - 2]) {
            a[start++] = a[i];
        }
    }

    return start;
}
```
