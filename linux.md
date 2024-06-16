# linux
ELF可执行文件类型
PATH是可执行程序的路径  echo $PATH
LIBRARY_PATH是链接时的路径
LD_LIBRARY_PATH是运行时查找的路径

# 60daysOS
## qemu

vshmem-client/server：这是一个 guest 和 host 共享内存的应用程序，遵循 C/S 的架构。
qemu-ga：这是一个不利用网络实现 guest 和 host 之间交互的应用程序（使用 virtio-serial），运行在 guest 中。
qemu-io：这是一个执行 Qemu I/O 操作的命令行工具。
qemu-system-x86_64：Qemu 的核心应用程序，虚拟机就由它创建的。
qemu-img：创建虚拟机镜像文件的工具，下面有例子说明。
qemu-nbd：磁盘挂载工具。

>qemu-system-x86_64 -L . -m 32 -rtc base=localtime -vga std -fda helloos.img
>..\..\..\tolset\z_tools\nask.exe helloos.nas helloos.img
> ..\tolset\z_tools\nask.exe helloos.nas helloos.img
```
qemu-system-x86_64：这是 QEMU 的可执行文件名称，用于启动 x86_64 架构的虚拟机。
-L .：这个选项指定了 QEMU 在哪里寻找 BIOS、固件以及其他必要的系统文件。. 表示当前目录，也就是告诉 QEMU 在当前目录下查找这些文件。
-m 32：这个选项指定了虚拟机的内存大小为 32MB。你可以根据你的需要调整这个值，比如 -m 512 表示虚拟机内存大小为 512MB。
-rtc base=localtime：这个选项设置了虚拟机的实时时钟（RTC），将其基准设置为本地时间。
-vga std：这个选项指定了使用标准的 VGA 显示模式。这意味着虚拟机将使用标准的 VGA 显示适配器来显示图形。
-fda helloos.img：这个选项指定了虚拟机启动时要加载的软盘映像文件。helloos.img 应该是你的操作系统映像文件的名称。
```
> qemu-system-arm -M xilinx-zynq-a9 -cpu cortex-a9 -nographic -kernel $BUILD_DIR/mm.elf -m 512M -s -S

使用机器 xilinx-zynq-a9
处理器 cortex-a9
因为这是裸机，所以可执行文件是一个自包含的ELF文件
-m 512M 表示平台具有512 MiB的RAM
-s 是的快捷方式 -gdb tcp::1234 （也就是说qemu自带了gdbserver，可以让gdb连它）
-S 表示在启动时冻结CPU
