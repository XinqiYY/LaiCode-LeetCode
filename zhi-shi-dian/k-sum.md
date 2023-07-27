# K Sum

> 预留对撞指针之外的指针，后再开始对撞
>
> 参考：[\[LeetCode\]167. Two Sum II - Input array is sorted 中文 & K Sum模板](https://www.youtube.com/watch?v=PHBK0Em1p00\&ab\_channel=%E5%B1%B1%E6%99%AF%E5%9F%8E%E4%B8%80%E5%A7%90)

[167 . Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

> k sum的底层逻辑，给定数组是sorted，那么两个指针分别对应开头和结尾，如果和大于target则 j--，小的话 i++，等于target的话直接返回index i 和 j 对应的数字

```java
public int[] twoSum(int[] a, int tar) {
    if (a == null || a.length == 0) return null;

    int i = 0, j = a.length - 1;

    while (i < j) {
        int cur = a[i] + a[j];
        if (cur > tar) {
            j--;
        } else if (cur < tar) {
            i++;
        } else {
            return new int[] { i + 1, j + 1 };
        }
    }

    return null;
} 
```

[15 . 3Sum](https://leetcode.com/problems/3sum/)

> 套用 2 sum 模板，要注意查重

```java
public List<List<Integer>> threeSum(int[] a) {
    List<List<Integer>> res = new ArrayList<>();
    if (a == null || a.length == 0) return res;
    Arrays.sort(a);
    for (int i = 0; i < a.length; i++) {
        if (i > 0 && a[i] == a[i - 1]) continue; // dedup
        
        int left = i + 1;
        int right = a.length - 1;
        while (left < right) {
            int tmp = a[left] + a[right];
            if (a[i] + tmp == 0) {
                res.add(Arrays.asList(a[i], a[left++], a[right]));
                while (left < right && a[left] == a[left - 1]) { // dedup
                    left++;
                }
            } else if (a[i] + tmp < 0) {
                left++;
            } else {
                right--;
            }
        }
    }
    
    return res;
}
```

[16 . 3Sum Closest](https://leetcode.com/problems/3sum-closest/)

> 每次更新gap

```java
public int threeSumClosest(int[] a, int t) {
    int diff = Integer.MAX_VALUE;
    int res = 0;
    Arrays.sort(a);
    for (int i = 0; i < a.length; i++) {
        int k = a.length - 1;
        for (int j = i + 1; j < k;) {
            int sum = a[i] + a[j] + a[k];
            if (sum == t) return sum;
            else if (sum < t) j++;
            else k--;

            if (Math.abs(t - sum) < diff) {
                diff = Math.abs(t - sum);
                res = sum;
            }
        }
        
    }

    return res;
}
```

[18 . 4Sum](https://leetcode.com/problems/4sum/)

```java
public List<List<Integer>> fourSum(int[] a, int tar) {
    List<List<Integer>> res = new ArrayList<>();
    if (a == null || a.length < 4) return res;
    Arrays.sort(a);
    
    for (int i = 0; i < a.length - 3; i++) {
        if (i > 0 && a[i] == a[i - 1]) continue;
        for (int j = i + 1; j < a.length - 2; j++) {
            if (j > i + 1 && a[j] == a[j - 1]) continue;
            int k = j + 1;
            int l = a.length - 1;
            while (k < l) {
                long sum = (long) a[i] + a[j] + a[k] + a[l];
                if (sum < tar) {
                    k++;
                    while (a[k] == a[k - 1] && k < l) k++;
                } else if (sum > tar) {
                    l--;
                    while (a[l] == a[l + 1] && k < l) l--;
                } else {
                    res.add(Arrays.asList(a[i], a[j], a[k], a[l]));
                    k++;
                    l--;
                    while (a[k] == a[k - 1] && k < l) k++;
                    while (a[l] == a[l + 1] && k < l) l--;
                }
            }
        }
    }

    return res;
}
```

[259 . 3Sum Smaller](https://leetcode.com/problems/3sum-smaller/)

```java
public int threeSumSmaller(int[] a, int tar) {
    if (a == null || a.length == 0) return 0;
    Arrays.sort(a);
    int res = 0;

    for (int i = 0; i < a.length - 1; i++) {
        int j = i + 1;
        int k = a.length - 1;
        while (j < k) {
            int sum = a[i] + a[j] + a[k]; 
            if (sum < tar) {
                res += k - j;
                j++;
            } else {
                k--;
            }
        }
    }

    return res;
}
```
