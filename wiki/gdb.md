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




### peda插件

- aslr -- Show/set ASLR setting of GDB
- checksec -- Check for various security options of binary
- dumpargs -- Display arguments passed to a function when stopped at a call instruction
- dumprop -- Dump all ROP gadgets in specific memory range
- elfheader -- Get headers information from debugged ELF file
- elfsymbol -- Get non-debugging symbol information from an ELF file
- lookup -- Search for all addresses/references to addresses which belong to a memory range
- patch -- Patch memory start at an address with string/hexstring/int
- pattern -- Generate, search, or write a cyclic pattern to memory
- procinfo -- Display various info from /proc/pid/
- pshow -- Show various PEDA options and other settings
- pset -- Set various PEDA options and other settings
- readelf -- Get headers information from an ELF file
- ropgadget -- Get common ROP gadgets of binary or library
- ropsearch -- Search for ROP gadgets in memory
- searchmem|find -- Search for a pattern in memory; support regex search
- shellcode -- Generate or download common shellcodes.
- skeleton -- Generate python exploit code template
- vmmap -- Get virtual mapping address ranges of section(s) in debugged process
- xormem -- XOR a memory region with a key




https://github.com/ludx/The-Lost-Art-of-C-Structure-Packing
