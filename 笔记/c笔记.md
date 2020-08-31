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



枚举

常量符号化

可以变成更加方便的   枚举

enum COLOR{RED,YELLOW,GREEN};

![image-20200825085148349](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825085148349.png)

枚举可以当做int

![image-20200825085744621](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825085744621.png)

![image-20200825090314732](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825090314732.png)

![image-20200825090517330](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825090517330.png)

枚举主要用来常量符号化



结构类型

结构化初始化

![image-20200825092732274](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825092732274.png)

结构成员

结构和数组有点像  数组单元必须相同

结构成员可以不同

用.运算符和名字访问其成员

![image-20200825092905154](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825092905154.png)

结构运算

![image-20200825093216804](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825093216804.png)

结构指针

![image-20200825093305091](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825093305091.png)



结构与函数

![image-20200825093607406](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825093607406.png)

![image-20200825111000588](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825111000588.png)

![image-20200825151340058](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825151340058.png)

![image-20200825151448397](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825151448397.png)



自定义数据类型typedef

typedef int Length;

![image-20200825151755760](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825151755760.png)

![image-20200825152132299](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825152132299.png)



union联合

![image-20200825152243333](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825152243333.png)

用了一个,另一个就不能用他

![image-20200825153214096](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825153214096.png)

小端解释

低位在前  02   04   00   00  (小端)     通过union得到内存字节

正常1234---->00   00  04   02

![image-20200825153420650](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825153420650.png)



宏

![image-20200825161023975](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825161023975.png)

![image-20200825165112455](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825165112455.png)

![image-20200825165335167](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825165335167.png)

![image-20200825165500063](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825165500063.png)

![image-20200825165854124](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825165854124.png)





错误

![image-20200825170001227](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825170001227.png)

![image-20200825170149694](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825170149694.png)

正确

![image-20200825170306195](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825170306195.png)

![image-20200825170401448](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825170401448.png)

![image-20200825170532745](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825170532745.png)

缺点:没有任何类型检查





![image-20200825172532380](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825172532380.png)

![image-20200825172602421](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825172602421.png)

![image-20200825172728490](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200825172728490.png)

条件编译指令

#ifndef _MAX_H_

#define _MAX_H_

#endif

![image-20200826085010312](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200826085010312.png)



函数指针

函数地址  每一个函数都有地址  类型xx()

```
void f(void)
{
    printf("in f()\n");
}

int main()
{
void(*pf)(void) = f;
printf("%p\n",pf);
printf("-----------------\n");
f();
(*pf)();
}
```

