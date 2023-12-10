# Reverse Stack with Recursion

## 题目

⼀个栈依次压⼊1、2、3、4、5，那么从栈顶到栈底分别为5、4、3、2、1。将这个栈转置后，从栈顶到栈底为 1、2、3、4、5，也就是实现栈中元素的逆序，但是只能⽤递归函数来实现，不能⽤其他数据结构;

#### Leetcode链接：

#### 参考：

## 解法一

> Clarification:&#x20;
>
> Algorithm:&#x20;
>
> * 想要不使⽤别的数据结构完成栈的反转，就必须借助递归函数的返回值来实现这些操作。
> * ⾸先⼀个递归要深⼊栈 中，取得并移除栈底元素，但是不应该改变除了栈底外的其他元素的顺序。
> * 第⼆个递归是要将取出的元素按要求 再放⼊栈中，push操作要在递归返回后再push。也就完成了要求;

#### <mark style="color:red;">注意：</mark>

## 代码

```java
    public static void reverseStack(Stack<Integer> stack) {
        if (!stack.isEmpty()) {
            int top = stack.pop(); // 移除栈顶元素
            reverseStack(stack); // 递归处理剩余的栈

            insertAtBottom(stack, top); // 将移除的元素插入栈底
        }
    }

    public static void insertAtBottom(Stack<Integer> stack, int value) {
        if (stack.isEmpty()) {
            stack.push(value);
        } else {
            int top = stack.pop(); // 移除栈顶元素
            insertAtBottom(stack, value); // 递归将元素插入栈底
            stack.push(top); // 将之前的栈顶元素放回栈
        }
    }
```

#### TC & SC:&#x20;

> TC: O(n)
>
> 您提到的insertAtBottom函数中，每个元素在被操作时的次数是递增的，但总体的时间复杂度仍然是线性的。这是因为insertAtBottom函数的复杂度是O(N)，而它被递归调用的次数是N（因为有N个元素），所以总体时间复杂度是O(N^2)。
>
> 然而，当我们考虑整个reverseStack函数时，您应该注意到，insertAtBottom函数在每一次递归调用中都只会操作不超过一个元素。具体来说，第一次调用insertAtBottom时会将栈顶的元素移至栈底，第二次调用会将下一个元素移至栈底，以此类推。所以虽然每次insertAtBottom中的元素操作次数递增，但每个元素只会被操作一次。
>
> 因此，整个reverseStack的时间复杂度仍然是O(N)，而不是O(N^2)。这是因为虽然每个元素在insertAtBottom中的操作次数递增，但是它们仍然是线性关系，不会导致总体时间复杂度变为平方级别。
>
> SC: O(n)

## **Similar Questions:**&#x20;
