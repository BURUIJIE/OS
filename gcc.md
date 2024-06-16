# gcc
 gcc可以生成可执行程序
linux .o,.a,.so
.o是中间文件，相当于windows系统下的.obj文件 。
.a为静态库，是好多个.o合在一起,用于静态链接， 相当于windows系统下的lib。
.so 为共享库，是shared object,用于动态链接的，相当于windows系统下的dll。
## gcc的基本语法：
```gcc [options] [filenames] ```
其中[options]表示参数，[filenames]表示相关文件的名称。
一些常用的参数及含义下表所示：

|      参数       |                                                描述                                                 |
| -------------- | -------------------------------------------------------------------------------------------------- |
| -E	         | 仅执行预处理，不进行编译、汇编和链接（生成后缀为 .i 的预编译文件）                                       |
| -S             | 执行编译后停止，不进行汇编和链接（生成后缀为 .s 的预编译文件）                                           |
| -c             | 编译程序，但不链接成为可执行文件（生成后缀为 .o 的文件）                                                |
| -o             | 直接生成可执行文件                                                                                   |
| -O/-O1/-O2/-O3 | 优化代码，减少代码体积，提高代码效率，但是相应的会增加编译的时间                                         |
| -Os            | 优化代码体积（多个-O参数默认最后一个）                                                                 |
| -Og            | 代码优化（不能与“-O”一起用）                                                                          |
| -O0            | 关闭优化                                                                                            |
| -l [lib]       | 指定程序要链接的库，[lib]为库文件名称。如果gcc编译选项中加入了“-static”表示寻找静态库文件                 |
| -L [dir]       | 指定-l（小写-L）所使用到的库文件所在路径                                                               |
| -I [dir]       | 增加 include 头文件路径                                                                              |
| -D [define]    | 预定义宏                                                                                            |
| -static        | 链接静态库生成目标文件，禁止使用动态库（在支持动态链接的系统上）                                         |
| -share         | 尽量使用动态库，但前提是系统存在动态库，生成的目标文件较小                                               |
| -shared        | 生成共享文件，然后可以与其它文件链接生成可执行文件                                                      |
| -fpic          | 生成适用于共享库的与地址无关的代码（PIC）（如果机器支持的话）                                            |
| -fPIC          | 生成与位置无关的的代码，适用于使用动态库，与“-fpic”的区别在于去除去全局偏移表的任何限制（如果机器支持的话） |
| -fPIE          | 使用与地址无关的代码生成可执行文件                                                                    |
| -w             | 不输出任何警告信息                                                                                   |
| -Wall          | 开启编译器的所有警告选项                                                                              |
| -g             | 生成调试信息，方便gdb调试                                                                            |
| -v             | 查看gcc编译器的版本，显示gcc执行时的详细过程                                                           |
| -ggdb          | 加入GDB调试器能识别的格式                                                                            |
| -Werror        | 将所有的警告当成错误进行处理，在所有产生警告的地方停止编译                                               |
| -M             | 生成适合于make规则的主要文件的依赖信息                                                                |
| -MM            | 与“-M”相比忽略由“#include”所造成的依赖                                                                |
| -MD            | 与-M作用类似，将输出导入到 .d 文件中                                                                  |
| -MMD           | 与-MM作用类似，将输出导入到 .d 文件中                                                                 |
| --help         | 查看帮助信息（注意前面是两个“-”，一个“-”不行）                                                         |
| --version      | 查看版本信息（注意前面是两个“-”，一个“-”不行）                                                         |

![<center>程序生成过程</center>](vx_images/273504513251905.png =1140x)

## 实例
```
#include <stdio.h>
int main() {

    signed char signed_num = -1;    // 有符号数为 -1
    unsigned char unsigned_num = 255;    // 无符号数为 255
    if (signed_num < unsigned_num) {
		printf("signed_num < unsigned_num");
    } else if (signed_num > unsigned_num) {
		printf("signed_num > unsigned_num");

    }

    return 0;
}
```
### 參數-v

Using built-in specs.
> COLLECT_GCC=gcc

指定 gcc 编译器的可执行文件路径

> Target: x86_64-linux-gnu

指定目标平台为 x86_64 架构的 Linux 系统
> Configured with: /usr/src/gcc/configure --build=x86_64-linux-gnu --disable-multilib --enable-languages=c,c++,fortran,go

显示了编译 gcc 编译器时使用的配置选项。
> Thread model: posix

指定了线程模型为 POSIX 标准
> Supported LTO compression algorithms: zlib zstd

列出了支持的 LTO（链接时优化）压缩算法。

>gcc version 12.3.0 (GCC)
 
显示了 gcc 编译器的版本号

> COMPILER_PATH=/usr/local/libexec/gcc/x86_64-linux-gnu/12.3.0/:/usr/local/libexec/gcc/x86_64-linux-gnu/12.3.0/:/usr/local/libexec/gcc/x86_64-linux-gnu/:/usr/local/lib/gcc/x86_64-linux-gnu/12.3.0/:/usr/local/lib/gcc/x86_64-linux-gnu/

指定了编译器的搜索路径。

> LIBRARY_PATH=/usr/local/lib/gcc/x86_64-linux-gnu/12.3.0/:/usr/local/lib/gcc/x86_64-linux-gnu/12.3.0/../../../../lib64/:/lib/x86_64-linux-gnu/:/lib/../lib64/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib64/:/usr/local/lib/gcc/x86_64-linux-gnu/12.3.0/../../../:/lib/:/usr/lib/

指定了库文件的搜索路径，-L 可以增加搜索路徑
> COLLECT_GCC_OPTIONS='-v' '-E' '-o' 'main.c' '-mtune=generic' '-march=x86-64' '-dumpdir' 'main.'

列出了 gcc 编译器当前使用的编译选项

### 预处理
`gcc -v  -E main -o main.c `
递归的增加头文件，并且展开宏
```
# 0 "main.c"
# 0 "<built-in>"
# 0 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 0 "<command-line>" 2
# 1 "main.c"
# 1 "/usr/include/stdio.h" 1 3 4
# 27 "/usr/include/stdio.h" 3 4
# 1 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 1 3 4
# 33 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 3 4
```
解析：这些行是源文件经过预处理后的结果。每一行都以#开头，表明它们是预处理指令，用于指示编译器处理源文件的方式。具体解释如下：

0 "main.c"：这是一个标识源文件的指令，表示当前正在处理的文件是名为 "main.c" 的源文件。
0 "\<built-in\>"：指示接下来的代码是由编译器内部生成的，而不是从外部文件导入的。
0 "\<command-line\>"：指示接下来的代码是从命令行传入的，而不是从文件中导入的。
1 "/usr/include/stdc-predef.h" 1 3 4：表示接下来的内容是从标准预定义头文件 "/usr/include/stdc-predef.h" 中导入的。
0 "\<command-line\>" 2：类似于之前的命令行指令，但是数字 2 表示该指令的级别为 2。
1 "main.c"：指示处理的源文件又回到了 "main.c"。
1 "/usr/include/stdio.h" 1 3 4：表示接下来的内容是从标准头文件 "/usr/include/stdio.h" 中导入的。
27 "/usr/include/stdio.h" 3 4：这是头文件的开头，位于 "/usr/include/stdio.h" 中的第 27 行。
1 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 1 3 4：表示接下来的内容是从 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 中导入的。
33：指示该行在源文件中的行号。
"/usr/include/x86_64-linux-gnu/bits/libc-header-start.h"：指示该行在源文件中的文件路径。
数字 3 和 4 表示预处理指令的类别和级别。在这里，3 表示该行是一个“#pragma system_header”指令，用于告知编译器将此文件标记为系统头文件，并禁止生成任何警告信息。4 则是指示该行结束了一个预处理指令。
### 编译
```
	.file	"main.c"    指定源文件名为 "main.c"。
	.text               指定接下来的指令都是代码段。
	.section	.rodata.str1.1,"aMS",@progbits,1    定义一个只读数据段，其中包含一个字符串常量。
.LC0:                定义字符串常量的标签。
	.string	"signed_num < unsigned_num"      存储字符串常量的实际内容。
	.text                     定义字符串常量的标签。
	.globl	main                声明 `main` 函数为全局函数。
	.type	main, @function   指定 `main` 函数的类型为函数。
main:          表示 `main` 函数的起始位置。
.LFB11:           标签，表示一个新的函数块的起始位置。
	.cfi_startproc        开始处理过程的 CFI 指令。
	subq	$8, %rsp        分配8个字节的栈空间。
	.cfi_def_cfa_offset 16    定义了栈帧中的当前位置。
	movl	$.LC0, %edi     ：将字符串常量的地址传递给 `%edi` 寄存器，准备调用 `printf` 函数。
	movl	$0, %eax            将参数个数清零，准备调用 `printf` 函数。
	call	printf              调用 `printf` 函数，输出字符串。
	movl	$0, %eax               将返回值设为 0。
	addq	$8, %rsp             释放之前分配的栈空间。
	.cfi_def_cfa_offset 8          定义了栈帧中的当前位置。
	ret                            返回。
	.cfi_endproc                    结束处理过程的 CFI 指令。
.LFE11:                             标签，表示函数块的结束位置。
	.size	main, .-main                指定 `main` 函数的大小。
	.ident	"GCC: (GNU) 12.3.0"           编译器版本信息。
	.section	.note.GNU-stack,"",@progbits        指定 GNU 栈的信息。
```
### 汇编
`gcc -c main.s -o main.o`
soname：
必须的格式如：lib+函数库名+.so+版本号信息（但是记住，非常底层的C库函数都不是以lib开头命名的）。例子：libreadline.so.3
real name：/usr/lib/libreadline.so.3

注意，编译器编译的时候需要的函数库的名字就是不包含版本号信息的soname，例如上面的例子把最后的.3去掉就可以了。
libreadline.so
生成二进制的库
### 链接
`gcc [目标文件] -o [可执行程序] -l[动态库名]`

## 动态库静态库
### 静态
`ar -cr   libmain.a main.o  生成静态库`
创建静态库
`gcc main.c -L. -lmain -o main`
链接静态库
### 动态
`gcc -c -fPIC main.c -o main.o`
先动态编译.o文件
`gcc  main.o -shared -fPIC -o libmain.so`
编译动态库
或者
`gcc  main.c -shared -fPIC -o libmain.so`
直接编译动态库
***
### 诊断工具
#### ldd
```
查看so文件依赖
> ldd  libmain.so
        linux-vdso.so.1 (0x00007ffcd4132000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f82eb5b2000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f82eb7a4000)
```
***
#### nm
```
> nm libmain.so
0000000000003df8 d _DYNAMIC
0000000000003fe8 d _GLOBAL_OFFSET_TABLE_
                 w _ITM_deregisterTMCloneTable
                 w _ITM_registerTMCloneTable
00000000000020d0 r __FRAME_END__
0000000000002034 r __GNU_EH_FRAME_HDR
0000000000004010 d __TMC_END__
                 w __cxa_finalize@GLIBC_2.2.5
00000000000010c0 t __do_global_dtors_aux
0000000000003df0 d __do_global_dtors_aux_fini_array_entry
0000000000004008 d __dso_handle
0000000000003de8 d __frame_dummy_init_array_entry
                 w __gmon_start__
0000000000001164 t _fini
0000000000001000 t _init
0000000000004010 b completed.0
0000000000001050 t deregister_tm_clones
0000000000001100 t frame_dummy
0000000000001109 T main
                 U printf@GLIBC_2.2.5
0000000000001080 t register_tm_clones
```
| 类型 |                                                             说明                                                              |
| ---- | ----------------------------------------------------------------------------------------------------------------------------- |
| B    | 未初始化数据段（即 .bss 段）全局符号。                                                                                             |
| b    | 未初始化数据段（即 .bss 段）局部符号。                                                                                             |
| C    | 该符号为 common。common symbol 是未初始化数据段。该符号没有包含于一个普通 section 中。只有在链接过程中才进行分配。符号的值表示该符号需要的字节数。 |
| D    | 已初始化数据段（即 .data 段）全局符号。                                                                                             |
| d    | 已初始化数据段（即 .data 段）局部符号。                                                                                             |
| R    | 只读数据段（即 .rodata 段）全局符号。                                                                                              |
| r    | 只读数据段（即 .rodata 段）局部符号。                                                                                              |
| T    | 代码段（即 .text 段）全局符号。                                                                                                   |
| t    | 代码段（即 .text 段）局部符号。                                                                                                   |
| U    | 未定义符号（外部符号）。                                                                                                          |

不建议在编译时为链接器指定选项-ldflags='-s -w'，否则相关的符号表和调试信息将被去除。
#### objdump
***
`objdump   -i  libmain.so`

***
#### 链接问题
如果想用自己的函数覆盖某个库中的一些函数，同时保留该库中其他的函数的话，可以在/etc/ld.so.preload中加入要替换的库（.o结尾的文件），这些preloading的库函数将有优先加载的权利。
每次新增加动态加载的函数库、删除某个函数库或者修改某个函数库的路径时，都要重新运行ldconfig来更新缓存文件/etc/ld.so.cache,此文件保存已排好序的动态链接库名字列表。
在Linux下，共享库的加载是由/lib/ld.so完成的，ld.so加载共享库时，会从ld.so.cache查找。
通过修改 LD_LIBRARY_PATH或者/etc/ld.so.conf文件来指定动态库的目录。通常这样做就可以解决库无法链接的问题了。
