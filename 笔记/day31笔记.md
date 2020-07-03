Java：
++a 先加
a++ 后加
– a 先减
a-- 后减
kotlin：
没有++或者-- 取代的是 固定函数
a.inc 等于 ++a/a++
a.dec 等于 --a/a–

然后重点来了：
我们都知道 在Java中 自增或者自减都会改变原有的值的大小
Java：
int a=3;
++a;
输出a a=4
然后就是kotlin
var a=3
println(a.inc)
输出的结果是 4
但是这个时候你要是输出 a发现还是3，意思就是kotlin的函数运算不会改变原有的值





var可变

val不可变



```
 fun kthToLast(head: ListNode?, k: Int): Int {
        var fast = head
        var slow = head
        var kk = k
        while (kk!=0){
            kk -= 1;
            fast = fast?.next
        }

        while (fast!=null){
            fast = fast.next
            slow = slow?.next
        }

        return slow!!.`val`

    }
```

怎么实现k--?   可以复制变量kk 然后  kk-=1 就是自减1





kotlin初始化的时候最好指定类型 不然会有强制类型转换 如果没有 会转为nothing

 pre = cur as Nothing?

正确是先初始化pre为 listNode类型





---





