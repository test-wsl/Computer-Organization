## 计算机组成原理

####  学习方法

![计算机组成原理知识地图](https://github.com/test-wsl/Computer-Organization/blob/master/img/zhishiditu.jpg?raw=true)

* 基本组成
  * 运算器
  * 存储器
  * 控制器
  * 输入输出设备
* 指令和计算
  * 编译器如何编译和汇编		控制器
  * 二进制和编码                       运算器
  * CPU设计                               CPU时钟
  * 数据通路                               连接运算器和控制器
  * 指令执行						       异常和中断,SIMD
  * 存储器原理                           高速缓存,内存,SSD硬盘,机械硬盘
* 学习方法
  * 提问自己来串联知识点			程序的编译、链接、装载和执行，以及计算时需要用到的逻辑电路、、ALU，乃至 CPU 自发为你做的流水线、指令级并行和分支预测，还有对应访问到的硬盘、内存，以及加载到高速缓存中的数据
  * 写一些程序来验证知识点          性能
  * 通过计算机硬件发展的历史对照           
  * 不明白的知识点,多搜索,多看不同来源的资料,多交流

* 书籍
  * 入门 
    * 计算机是怎样跑起来的
    * 程序是怎样跑起来的
  * 深入学习
    * 计算机组成与设计：硬件 / 软件接口
    * 深入理解计算机系统   ([bilibili](https://www.bilibili.com/video/av24540152/)   [Youtube](https://www.youtube.com/playlist?list=PLmBgoRqEQCWy58EIwLSWwMPfkwLOLRM5R ))
    * 计算机组成:结构化方法
    * 计算机体系结构:量化研究方法
  * 其他
    * What Every Programmer Should Know About Memory
    * 编码:隐匿在计算机软硬件背后的语言
    * 程序员的自我修养:链接,装载和库

#### CPU主频和性能

* 性能(时间倒数就是性能)
  * 响应时间                   提升不容易
  * 吞吐率                       堆硬件来提高性能
  * 跑分软件          ([SPEC](https://www.spec.org/cpu2017/results/cpu2017.html))
* 计算机的计时单位 CPU时钟
  * 时间不准                  程序运行的时候需要等待其他因素的时间
  * 程序的执行时间是 user time + sys time
  * 程序的CPU执行时间 = CPU时钟周期 x 时钟周期时间
    * 时钟周期  指令数X 每条指令的平均时钟周期数(CPI)
    * 执行时间 = 指令数 X CPI X Clock Cycle Time
      * 时钟周期  主频
      * 平均时钟周期数CPI  一条指令的CPU Cycle
      * 指令数 需要执行多少指令
* 思考
  * 实际运行![time](https://github.com/test-wsl/Computer-Organization/blob/master/img/time_seq.png?raw=true)
    * 测试中使用了多核处理器,在处理时,分别分配了不同的CPU核心,会导致真实时间会小于user time + sys time .



#### 穿越功耗强, 提高性能

* 多放一些晶体管,提高时钟频率.让CPU变得 更快
* CPU  超大规模集成电路
  * 一个个晶体管组成,通过不断打开关闭晶体管,完成各种运算和功能
    * 增加密度
    * 提升主频  (散热)
  * 一个CPU功耗
    * 功耗 ~=1/2 x 负载电容 x 电压平方 x开关频率 x 晶体管数量
* 满足并行计算提高性能
  * 可以分解为几个可以并行计算的任务
  * 确保几个人的结果可以汇总到一起
  * 汇总阶段需要顺序来,一步一步来
* 阿姆达尔定律
  * 优化后的执行时间 = 受优化影响的执行时间 / 加速倍数 + 不受影响的执行时间
* 提升性能的原则性问题
  * 加速大概率事件
  * 流水线提高性能
  * 通过预测提高性能
    * 分支和冒险
    * 局部性原理
* 思考
  * 阅读
    * 《计算机组成与设计：软 / 硬件接口》（第 5 版）的 1.7 和 1.10 节
    * 《深入理解计算机系统》（第 3 版）的 1.9 节
  * 软件开发运用类似的原则性问题提升性能



#### 计算机指令

* 打孔卡编程

* CPU执行各种计算机指令的逻辑机器

  * 计算机指令集  不同CPU使用的不同
  * 平时存储在存储器中的计算机程序            存储程序型计算机

* 汇编语言

  * Linux 上可以使用 gcc 和 objdump命令把代码和机器码打印出来
  * 机器码和汇编代码是一一对应的
  * 高级语言到汇编代码再到机器码  变成CPU可执行的计算机指令的过程

* 解析指令和机器码

  * 算术类指令                加减乘除

  * 数据传输类指令         变量赋值,内存读写数据

  * 逻辑类指令                 逻辑与或非

  * 条件分支指令              if/esle

  * 无条件跳转指令          

    ![汇编代码](https://github.com/test-wsl/Computer-Organization/blob/master/img/huibiandaima.jpeg?raw=true)

* MISP汇编代码([MISP](https://www.mips.com/mipsopen/))

  * 32位整数,高6位操作码,剩下26位三种格式,分别为R,I,J

    * R   算术和逻辑操作
    * I    数据传输,条件分支,运算
    * J    跳转指令(高26位都是跳转后的地址)

    ![MSIP](https://github.com/test-wsl/Computer-Organization/blob/master/img/MISP.jpeg?raw=true)

* 思考

  * 参考资料
    * 《计算机组成与设计：软 / 硬件接口》第 5 版的 2.17 小节





#### 指令跳转

* CPU如何执行指令

  * 一条一条顺序执行指令

  * 寄存器   --->    CPU    

  * 触发器和寄存器

    * PC寄存器       下一条指令的内存地址    3F

    * 指令寄存器    当前执行的指令码    83 7d fc 00

    * 条件寄存器    存放条件和逻辑运算的结果   SF , zf, SF ,OF

    * 其他寄存器

      ![CPU指令](https://github.com/test-wsl/Computer-Organization/blob/master/img/CPU.jpg?raw=true)

  * if/while 使用goto 跳转到制定位置的方式实现跳转

* 总结

  * 高级语言可以使用 if...else ... 或者while/for循环 回归到机器码就为一个goto语句
  * 实现goto语句,需要保存下一条指令的指令地址,当前指令的PC寄存器,指令寄存器

* 思考

  * 推荐
    * 深入理解计算机系统   第三章 ,介绍了C和intelCPU的对应关系
  * 除了if...else和for/while,还有switch...case的条件跳转指令,其汇编代码和这个类似?
    * [IntelJMP指令](http://www.unixwiz.net/techtips/x86-jumps.html)



#### 函数调用:发生stack overflow

* Stack Overflow
* 函数调用
  * 程序栈
    * 压栈和出栈
    * 多层函数调用
      * 内存中使用栈的方法,后进先出的数据结构 , 压栈(压入数据),出栈(取出数据)
      * 栈底,栈顶
    * 栈指针
    ![POP_PUSH](https://github.com/test-wsl/Computer-Organization/blob/master/img/pop_push.jpeg?raw=true)
    * 栈大小会出现栈溢出
      * 无限递归会创建出栈溢出
    * 函数内联会让复用的程序在程序调用的地方完全展开
    * 只会被调用的函数,被称为叶子函数(叶子过程)
* 思考
  * 推荐
    * 《深入理解计算机系统（第三版）》的 3.7 小节《过程》


#### ELF和静态链接 : 程序无法在Linux 和 Windows下运行
* 编译,链接和装载:拆解程序执行
  * 通过编译器编译汇编成汇编代码,再通过汇编器转化为CPU可以理解的机器码,CPU可以执行这些机器码
  * .o文件为一个目标文件,通过链接器把多个文件条用各种函数链接起来形成一个可执行文件
  ![C执行过程](https://github.com/test-wsl/Computer-Organization/blob/master/img/C_zhixng.jpg?raw=true)
  * 可执行文件和目标文件的代码差不多,但是却很长,都是用同一种文件格式ELF格式,叫做 可执行和可链接文件格式
  * ELF文件中,变量名,函数名都存放在一个叫做符号表的位置里,
  ![ELF格式](https://github.com/test-wsl/Computer-Organization/blob/master/img/ELF.jpg?raw=true)
    * .text Section 代码段
    * .data Section 数据段
    * .rel.text Section 重定位表
    * .systab Section 符号表
  * 链接器扫描所有输入的目标文件,所有符号表信息收集起来,构成一个全局的符号表--->根据重定位表,把不确定的跳转地址的代码,变成符号表里的地址 --->最后执行一次合并
    * 只需要解析ELF文件,对应指令和数据加载到CPU执行
* 为什么Linux和Windows下的程序不能一起执行
  * 两个操作系统的可执行文件的格式不同,Linux下位ELF格式,Windows下为一种叫做PE的装载器.
  * 分工合作 
* 思考
  * 推荐阅读
    * 《程序员的自我修养——链接、装载和库》的 1～4 章
  * readelf读取演示的符号表,看存在哪些信息,通过objdump读取出重定位表,查看有哪些信息
    * readelf -s Link_example.o
    * objdump -r link_example.o

#### 程序装载:"640k内存真的不够用吗?"

* 通过装载器解析可执行文件,把对应的指令和数据加载到内存里面
* 满足装在其要求
  * 可执行程序装在之后占用的空间是连续的    指令顺序的一条一条的执行下去
  * 需要同时加载很多程序,不能让程序自己规定在内存中加载的位置
    * 在内存中找到一个连续的内存空间,分配给程序,把内存地址空间地址和整个程序指令的内存地址做一个映射
    * 指令用到的地址位虚拟内存地址
    * 实际硬件里的空间 物理内存地址
* 内存分段(连续的内存空间)
  * 内存碎片问题    Linux Swap内存
  * 内存交换
  * 硬盘访问速度比内存慢很多,内存交换时会占用一个很占内存空间的程序,会卡顿
* 内存分页
  * 把物理内存空间切成固定一段尺寸的大小,这样一个连续的内存的物理地址,二十按照一个一个页来
  * 通常linux下会设置位4kb
  * getconf PAGE_SIZE  查看内存页大小
  * 没有了不能使用的碎片,只有被释放出来的很多的页   通过交换也只是少数页,不会花费太多时间,加载程序不需要一次性把程序加载到物理内存.

