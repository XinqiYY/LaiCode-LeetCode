# Queue & Stack

## 题目

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

#### Laicode链接：[https://app.laicode.io/app/problem/280?plan=3](https://app.laicode.io/app/problem/280?plan=3)

#### Youtube参考：

## 解法一

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> 1. 对每一个stack中的元素操作，直到结束，所以使用while循环
>    1. 每一次重置min和count
>       1. min用来记录当前stack状态中的最小值
>       2. count用来记录当前stack状态中有几个重复，方便后续放入stack
>    2. 因为stack长度会变化，所以遍历stack时使用while loop
>       1. 更新min当当前ele < min
>       2. 如果 = min，则count++
>    3. 遍历一次stack后，把所有ele倒回input stack中
>    4. 倒回后，把min放入buffer stack中，放count次
> 2. 最后，由于stack 倒一次反序，倒两次回去，所以再倒一次回到input stack，返回input

#### <mark style="color:red;">注意：</mark>

## 代码

```java
public class Solution {
  public void sort(LinkedList<Integer> s1) {
    LinkedList<Integer> s2 = new LinkedList<Integer>();
    // Write your solution here.
    if (s1 == null || s1.size() <= 1) {
      return;
    }

    sort(s1, s2);
  }

  private void sort(LinkedList<Integer> input, LinkedList<Integer> buffer) {
    while (!input.isEmpty()) {
      int min = Integer.MAX_VALUE;
      int count = 0;
      while (!input.isEmpty()) {
        int cur = input.pollFirst();
        if (cur < min) {
          min = cur;
          count = 1;
        } else if (cur == min) {
          count++;
        }
        buffer.offerFirst(cur);
      }

      while (!buffer.isEmpty() && buffer.peekFirst() >= min) {
        int temp = buffer.pollFirst();
        if (temp > min) {
          input.offerFirst(temp);
        }
      }

      while (count-- > 0) {
        buffer.offerFirst(min);
      }
    }

    while (!buffer.isEmpty()) {
      input.offerFirst(buffer.pollFirst());
    }
  }
}
```

#### TC & SC:&#x20;

> TC: O(n^2) 对每个状态中的stack都进行n次操作
>
> SC: O(n) 额外的stack
