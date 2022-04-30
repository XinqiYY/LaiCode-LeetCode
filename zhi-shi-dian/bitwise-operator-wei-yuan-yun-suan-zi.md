# Bitwise operator(位元运算子)

![](<../.gitbook/assets/image (134).png>)

## AND

![](<../.gitbook/assets/image (71) (1).png>)

## OR

![](<../.gitbook/assets/image (52) (1).png>)

## XOR

![](<../.gitbook/assets/image (89).png>)

## NOT

![](<../.gitbook/assets/image (44) (1).png>)

## Shift Operators

> 算数位移(Arithmetic shift)：
>
> * 算数位移又称有符号的位移(Signed shift). 会将所有的位元往左，或往右做指定数目的位置移动，而空出来的位元位置则会被填入。
>   * 左移，右填0
>   * 右移，左填signed bit。这样可以确保位移后整数的符号不会改变
> * 算数位移是相当于乘以2的倍数，或除以2的倍数运算
>   * 左移n个位元位置，相当于乘以 2^n
>   * 右移n个位元位置，相当于除以 2^n，如果不能整除，则往-∞方向做无条件舍去(round down toward negative infinity). 这与一般的除法往0方向做无条件舍去不同。
>
> 逻辑位移(Logical shift)
>
> * 仅把运算元当作是一序列的位元去做位移，无论左移或者右移，空出来的位元都填0. 因此对于负整数而言，位移后不会保持它的符号。

### Right Shift Example

> 第一个数字为符号位。0代表正数，1代表负数
>
> 右移后的数字是原数字除以2得到。

![](<../.gitbook/assets/image (90).png>)

### Left Shift Example

> 同理，左移是乘以2。位移1位，乘以2^1。位移两位乘以2^2

![](<../.gitbook/assets/image (20).png>)

### Right Logical Shift Example

> 符号位发生变化

![](<../.gitbook/assets/image (132).png>)

> \>>>: 逻辑右移的运算子，又称无符号右移
>
> \>> / <<: 算数右 / 左移的运算子
>
> 在Java中，基本都是算数位移，符号位都是signed。但是当我们进行char的操作时，符号位是unsigned。

![](<../.gitbook/assets/image (110) (1).png>)

> 例子1： 查看n=2的位置是不是1，我们首先把1向左移到需要的位置上，之后进行&。因为&是只有两个都是1的时候才会返回1，而任何一个为0的话，都会返回0。
>
> 例子2：把某一个bit设置成为1. 首先把1向左移到需要的位置上，之后进行 | 。因为 | 是任何一个是1则返回1. 所以 | 后，不管n这个位置是0还是1都会是1.&#x20;

![](<../.gitbook/assets/image (28) (1) (1).png>)

> 例子1：把某一个bit设置成0. 与上述同理，不过把1设为0 --> \~(1<\<n)。做&的运算
>
> 例子2：把某一个bit做反向，使用XOR，不会影响原本的结果

引用：[https://www.youtube.com/watch?v=10sJkpoFpv0](https://www.youtube.com/watch?v=10sJkpoFpv0)
