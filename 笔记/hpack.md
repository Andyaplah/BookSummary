1.背景:

- HTTP压缩是使用gzip在TLS层中执行的。标头和正文都被任意压缩，因为较低的TLS层不知道传输的数据类型。实际上，这意味着两者都使用DEFLATE算法压缩

- HTTP/1.1中，头部字段未被压缩。随着网页数量增长到需要数十到数百个请求，这些请求中的冗余头部字段会不必要地占用带宽，从而显着增加延迟

- SPDY推出了一种新的专用报头压缩算法。尽管它是专门针对标头设计的，包括使用预设字典，但仍使用DEFLATE，包括动态霍夫曼代码和字符串匹配

- SPDY最初通过使用DEFLATE格式压缩头部字段来解决这个冗余问题,它在高效地表示冗余头部字段时非常有效

- 两者都发现容易受到CRIME攻击，可以从压缩的标头中提取秘密身份验证cookie：因为DEFLATE使用向后字符串匹配和动态的Huffman代码，因此可以控制部分请求标头的攻击者可以逐渐恢复完整的cookie。通过修改请求的各个部分并查看在压缩过程中请求的总大小如何变化

  由于CRIME，大多数边缘网络都禁用了报头压缩,直到HTTP / 2出现

2.HPACK

- HTTP / 2支持一种新的专用报头压缩算法，称为HPACK。HPACK的开发考虑了CRIME之类的攻击，因此被认为可以安全使用
- HPACK对CRIME具有弹性，因为它不使用部分向后的字符串匹配和动态的Huffman代码（如DEFLATE）。而是使用以下三种压缩方法:
  1. 静态词典：预定义的词典，其中包含**61个常用的标头字段**，其中一些具有预定义的值
  2. 动态字典：连接期间遇到的实际标头的列表。该词典的大小受到限制，并且当添加新条目时，可能会驱逐旧条目
  3. 霍夫曼编码：静态霍夫曼编码可用于**编码任何字符串**：名称或值。该代码是专门为HTTP响应/请求标头计算的-ASCII数字和小写字母的编码较短
- HPACK格式有意地`简单`且`不灵活`。这两个特性都降低了由于实现错误而导致的互操作性或安全问题的风险。没有定义可扩展性机制;只有通过定义一个完整的替换才能更改格式



2.静态表

静态表由一个预定义的头部字段静态列表组成



3.动态表

- 动态表格由按先入先出顺序维护的头部字段列表组成。 动态表中的第一个和最新条目处于最低索引处，并且动态表的最旧条目处于最高索引处
- 动态表最初是空的。 在每个头部块被解压缩时添加条目。 动态表可以包含重复的条目（即具有相同名称和相同值的条目), 因此，**重复条目不能被解码器视为错误**
- 编码器决定如何更新动态表，因此可以控制动态表使用多少内存。 为了限制解码器的内存需求，动态表大小是严格限制的.解码器在处理头部字段表示的列表期间更新动态表。



4.索引地址空间

**静态表和动态表**合并成一个索引地址空间







重复大量 头部  效率低下

![image-20200904170159406](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904170159406.png)



index   1-61     header name   header value  

用16就可以表达 省下大量空间   静态表



编码请求

![image-20200904170454885](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904170454885.png)

静态表和动态表编码

如果没有  采用哈夫曼编码





静态表和动态表称为索引表

![image-20200904170556295](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904170556295.png)



工具h2load

![image-20200904170718603](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904170718603.png)

![image-20200904170944234](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904170944234.png)





两次动态表发挥作用

![image-20200904171021244](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904171021244.png)



四次压缩效率更高

![image-20200904171145326](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904171145326.png)





哈夫曼编码

![image-20200904172149865](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904172149865.png)



http2前身 spdy采用哈夫曼编码 不过是动态的

基于已经传输过进行动态编码  

hpack采用静态 防止被攻击



使用:

![image-20200904172825866](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904172825866.png)

步骤:

1.

![image-20200904172905185](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904172905185.png)

2.

![image-20200904173009185](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904173009185.png)

![image-20200904173017044](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904173017044.png)



案例(反向推):

![image-20200904173220137](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904173220137.png)





整形数字编码

只为静态表和动态索引

![image-20200904173548961](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904173548961.png)

静态表中

31以下才会有value出现    5位表示

31以上没有value



动态的索引号就比较大了



![image-20200904173854151](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904173854151.png)

例子

![image-20200904173925090](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904173925090.png)

解码

![image-20200904174151133](https://gitee.com/andylinchuanxin/bookimagenew/raw/master/img/image-20200904174151133.png)