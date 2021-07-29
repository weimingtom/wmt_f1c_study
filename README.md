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

## fb-test, fbset  

## ARM9/ARM11裸机开发笔记1之MDK开发环境和点亮LED  
http://www.openedv.com/forum.php?mod=viewthread&tid=45055  

## F1C100s_with_Keil_RTX4_emWin5  
裸机工程： https://github.com/hongxuyao/F1C100s_with_Keil_RTX4_emWin5  
https://gitee.com/xuyao2020/F1C100s_with_Keil_RTX4_emWin5  
https://www.amobbs.com/thread-5708471-1-1.html  
https://www.amobbs.com/thread-5731101-1-1.html  
```
--c99  
E:\Keil_v4\ARM\Segger\emWin\Include  
E:\Keil_v4\ARM\Segger\emWin\Lib\GUI_ARM_L.lib  
```
F1C100s_with_Keil_RTX4_emWin5_spl_v1.rar  
FIXME: Only ddr running (program lost after resetting), not available for nand flash  

## f1c200s(tiny200) linux+emwin稳定运行  
https://whycan.com/t_4739.html  
https://github.com/xiaofengvskuye/f1c200s_emwin/blob/master/Sample/SimpleDemo/main.c  

## 荔枝派Nano使用gcc-linaro-7.2.1进行交叉编译得到的可执行文件，一运行就"segmentation fault"  
https://whycan.com/t_3265.html  

## rt-thread  
https://github.com/vvhh2002/f1c100s_rt-thread  
https://github.com/vvhh2002/lv7_rtthread_f1c100s  
https://github.com/VeiLiang/BoloRTT  

## F1C100s_projects  
https://github.com/nminaylov/F1C100s_projects  
