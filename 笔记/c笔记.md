场景1

交换变量

函数返回多个值

参数应用把结果从函数中带出来



场景2

函数返回运算状态,通过指针返回

返回 -1或0状态



**指针需要先初始化变量再赋值**



指针和数组

传入函数数组成了什么?

就是指针

![image-20200822113224677](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200822113224677.png)

数组变特殊指针

![image-20200822114334291](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200822114334291.png)

![image-20200822114351658](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200822114351658.png)





指针与const?????

int i;

const int* p1 = &i;

int const* p2 = &i;

int *const p3 = &i;

上面四种可以反馈两个:

指针不可修改

通过指针不可修改

![image-20200824143328092](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824143328092.png)

![image-20200824143928291](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824143928291.png)

![image-20200824144023637](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824144023637.png)

![image-20200824144057203](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824144057203.png)



指针运算

如果不是数组,指针+1没有任何意义

可以+  +=  -=  -

可以++  --

两个指针可以相减

![image-20200824154009303](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824154009303.png)

![image-20200824154056989](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824154056989.png)

![image-20200824154134999](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824154134999.png)

![image-20200824155821153](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824155821153.png)

![image-20200824160851589](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200824160851589.png)