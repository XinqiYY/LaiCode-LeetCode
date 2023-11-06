# Smallest Submartic Sum with size K in 2D Array

## 题目

#### - 给一个2D Array，计算大小为K的submatrix合，并且返回其元素

#### Leetcode链接：

#### 参考：

## 解法一

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> * 遍历martix，起点为 i, j, 重点为 i + k, j + k，计算合，如果合有更新，则同时更新最小matrix的起点
> * 计算完毕后从最小matrix的起点开始遍历K次放入res\[]\[]中

#### <mark style="color:red;">注意：</mark>

## 代码

```java
public static int[][] findMinSumSubmatrix(int[][] matrix, int K) {
    int rows = matrix.length;
    int cols = matrix[0].length;
    int minSum = Integer.MAX_VALUE;
    int minStartRow = -1; // 记录最小子矩阵的起始行
    int minStartCol = -1; // 记录最小子矩阵的起始列

    for (int r1 = 0; r1 <= rows - K; r1++) {
        for (int c1 = 0; c1 <= cols - K; c1++) {
            int r2 = r1 + K;
            int c2 = c1 + K;
            int submatrixSum = 0;

            for (int i = r1; i < r2; i++) {
                for (int j = c1; j < c2; j++) {
                    submatrixSum += matrix[i][j];
                }
            }

            if (submatrixSum < minSum) {
                minSum = submatrixSum;
                minStartRow = r1;
                minStartCol = c1;
            }
        }
    }

    int[][] minSubmatrix = new int[K][K];
    int index = 0;

    // 遍历最小子矩阵并将元素添加到结果数组中
    for (int i = minStartRow; i < minStartRow + K; i++) {
        for (int j = minStartCol; j < minStartCol + K; j++) {
            minSubmatrix[index / K][index % K] = matrix[i][j];
            index++;
        }
    }

    return minSubmatrix;
}
```

#### TC & SC:&#x20;

> TC: O((m - k)(n - k)(k \* k)) --> 外层遍历m - k次，内层遍历 n - k 次，并且每次遍历k \* k次
>
> SC: O(k^2) output arr

## **Similar Questions:**&#x20;
