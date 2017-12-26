- l 全称 list,  显示源码
- b 21 , 表示在源码21行下断点
- p sizeof(student) .  student是一个结构体实例
- p &student
- x/20gx
    + 20 表示要显示的内存单元个数
    + g后面的x表示以16进制格式表示数据, 可选d 以十进制格式表示数据
    + g 表示8字节, w表示4字节, h表示双字节, b表示单字节
- telescope, 进一步解析地址保存的内容, 字符串或者指针或者函数符号
- bt 全称backtrace, 打印当前函数调用栈的信息
- up/down `<number>` 切换栈帧
- watch 


 GDB 在调试的时候会默认禁用 ASLR










https://github.com/ludx/The-Lost-Art-of-C-Structure-Packing
