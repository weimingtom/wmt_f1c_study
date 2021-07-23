# wmt_f1c_study  
My F1C200s and F1C100s study  

## 芒果派r3, dfrobot, uname -a  
Linux mangopi-r3 5.4.92 #1 Tue May 11 10:39:00 CST 2021 armv5tejl GNU/Linux  
search baidupan, sysimage-nand-120mb.zip (behide lcpi_factory.rar)  

## Build hello program on Linux mangopi-r3 5.4.92  
* search baidupan, armv5-eabi--glibc--stable-2020.08-1.tar.bz2  
https://toolchains.bootlin.com  
select armv5eabi and glibc  
* https://www.icode9.com/content-3-279874.html  
arm-linux-gcc -mcpu=arm926ej-s a.c  
same as: arm-linux-gcc -mcpu=arm926ej-s a.c -static  
same as: arm-linux-gcc a.c  
same as: arm-linux-gcc a.c -static  
* hello program  
```
#include <stdio.h>

int main()
{
	printf("Hello, world!\n");
	return 0;
}
```

## Flash Linux firmware, and copy file to file system  
* mpi-r-tools.zip, zadig.exe, Device, Create New Device", 1F3A EFE8  
* 1F3A 1010  
* 不插TF卡，按住BOOT按钮后插入USB线；或者先插入USB，保持按住BOOT按钮姿势时短按下RST键  
* from-fel-to-dfu.bat  
* dfu-util.exe -R -a all -D output\images\sysimage-nand.img  
* reset后，OTG线进入U盘模式  
* Copy elf file (a.out) to storage driver (mangopi-r3), copy to /root  
* Plug USB TTL, use putty to get tty console.   
* chmod +x a.out && ./a.out  

