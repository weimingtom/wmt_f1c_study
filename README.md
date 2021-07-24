# wmt_f1c_study  
My F1C200s and F1C100s study  

## 芒果派r3, dfrobot, uname -a  
Linux mangopi-r3 5.4.92 #1 Tue May 11 10:39:00 CST 2021 armv5tejl GNU/Linux  
search baidupan, sysimage-nand-120mb.zip (behide lcpi_factory.rar)  

## Build hello program for Linux mangopi-r3 5.4.92, get a.out    
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

## Flash Linux firmware, and copy file a.out to file system  
* https://mangopi.org/f1c_flashrom  
* mpi-r-tools.zip, zadig-2.5.exe, Device, Create New Device, Allwinner FEL Device, USB ID: 1F3A EFE8, Install Driver    
* mpi-r-tools.zip, zadig-2.5.exe, Device, Create New Device, Allwinner DFU Device, USB ID: 1F3A 1010, Install Driver    
* no TF, hold press BOOT and press RST    
* from-fel-to-dfu.bat  
* dfu-util.exe -R -a all -D output\images\sysimage-nand.img (use sysimage-nand-120mb.zip)    
* reset, and connect board's USB OTG to PC, wait a minute, get a storage driver (named Widora MangoPi R3)     
* Copy elf file (a.out) to storage driver (mangopi-r3), copy to /root  
* Connect board's USB TTL to PC, use putty to get tty console.   
* chmod +x a.out && ./a.out  

## 【荔枝派Nano】F1C100S的串口  
https://www.bilibili.com/read/cv9912248/  
https://gitee.com/cai_xl/F1C100S_examples  
