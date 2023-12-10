# 并查集 (Union Find)

> 并查集可以解决什么问题呢？

并查集常用来解决连通性问题。当我们需要判断两个元素是否在同一个集合里的时候，我们就要想到用并查集。并查集主要有两个功能：

* 将两个元素添加到一个集合中。
* 判断两个元素在不在同一个集合

### 代码模板：

```java
class Solution {
    int[] father;
    public boolean validPath(int n, int[][] edges, int source, int destination) {
        father = new int[n];
        init();
        for (int i = 0; i < edges.length; i++) {
            join(edges[i][0], edges[i][1]);
        }

        return isSame(source, destination);
    }

    // 并查集初始化
    public void init() {
        for (int i = 0; i < father.length; i++) {
            father[i] = i;
        }
    }

    // 并查集里寻根的过程
    public int find(int u) {
        if (u == father[u]) {
            return u;
        } else {
            father[u] = find(father[u]);
            return father[u];
        }
    }

    // 判断 u 和 v是否找到同一个根
    public boolean isSame(int u, int v) {
        u = find(u);
        v = find(v);
        return u == v;
    }

    // 将v->u 这条边加入并查集
    public void join(int u, int v) {
        u = find(u); // 寻找u的根
        v = find(v); // 寻找v的根
        if (u == v) return; // 如果发现根相同，则说明在一个集合，不用两个节点相连直接返回

        father[v] = u;
    }
}
```

通过模板，我们可以知道，并查集主要有三个功能。

1. 寻找根节点，函数：find(int u)，也就是判断这个节点的祖先节点是哪个
2. 将两个节点接入到同一个集合，函数：join(int u, int v)，将两个节点连在同一个根节点上
3. 判断两个节点是否在同一个集合，函数：isSame(int u, int v)，就是判断两个节点是不是同一个根节点

### 复杂度分析 <a href="#fu-za-du-fen-xi" id="fu-za-du-fen-xi"></a>

这里对路径压缩版并查集来做分析。

空间复杂度： O(n) ，申请一个father数组。

关于时间复杂度，如果想精确表达出来需要繁琐的数学证明，就不在本篇讲解范围内了，大家感兴趣可以自己去深入去研究。

这里做一个简单的分析思路。

路径压缩后的并查集时间复杂度在O(logn)与O(1)之间，且随着查询或者合并操作的增加，时间复杂度会越来越趋于O(1)。

了解到这个程度对于求职面试来说就够了。

在第一次查询的时候，相当于是n叉树上从叶子节点到根节点的查询过程，时间复杂度是logn，但路径压缩后，后面的查询操作都是O(1)，而 join 函数 和 isSame函数 里涉及的查询操作也是一样的过程。

### 相关题目：

[1971. Find if Path Exists in Graph](https://leetcode.com/problems/find-if-path-exists-in-graph/)
