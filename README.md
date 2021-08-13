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
https://whycan.com/p_33590.html  

## F1C100s_projects  
https://github.com/nminaylov/F1C100s_projects  

## f1c100s, nor flash, licheepi nano, 荔枝派nano  
我把荔枝派nano，f1c100s nor flash版烧录过程跑通了。  
我用的开发板是荔枝派nano，不过需要做手脚，而且这个开发板出厂不支持录音，  
如果要录音的话最好用芒果派r3，但芒果派r3的nand flash版不能用sunxi-fel直接烧录，  
我还在想这个如何解决。关于荔枝派nano，由于出厂是无法直接烧录nor flash的（板载的w25q128），  
需要搭额外的电路，我的做法如下，仅供参考：用一个母对公杜邦线接在GND脚上，  
用一个导线一头弯钩接在w25q128的1脚上（最靠近芯片白色圆点的那个脚），  
另一头接在母对公杜邦线，这两根杜邦线接在一起（通过面包板），  
通过usb线接通开发板，即可进入FEL模式，启动后，需要马上在面包板上断开上述的两根杜邦线，  
否则w25q128会无法片选使能。然后就可以spiflash-read和spiflash-write了，  
可以读出官方的ROM可写入自己的ROM  

## f1c200s, nor flash (also with nand flash, but fail to run widora's mangopi nand rom), 小淘气科技  
我购买了小淘气科技的F1C200s开发板（带nor和nand flash），没有买代码。  
这个板相当于荔枝派nano（UART0是调试输出），但也可以兼容芒果派r3（需要改接UART1，即PA2收PA3发，才能看到调试输出）。  
另外，虽然带有nand flash（通过跳帽来选择），但我试过无法运行芒果派r3的nand flash rom，  
可能是因为nand flash的芯片型号不同，待考。屏幕是接屏线的，下方的排针其实是空出来，没有接到屏幕。  
兼容800x480分辨率（我买的是这个分辨率），即可以忽略掉触摸功能和屏线，屏幕输出是不受影响的。  
带有喇叭，在屏幕转接板的背面，可以拔掉线，或者用耳机来避免声音过大（当然一般情况下不会用到声音输出）  

## 全志F1C200S F1C100S 介绍  
https://blog.csdn.net/tunqimai9331/article/details/95938903  

## 关于荔枝派（LiChee Pi）Nano初体验中的114514个坑   
https://www.stlee.tech/2020/06/25/关于荔枝派（LiChee%20Pi）Nano初体验中的114514个坑/
https://github.com/Icenowy/linux/archive/f1c100s-480272lcd-test.zip

## 【荔枝派Nano】F1C100S的boothead和BROM, 哔哩哔哩专栏  
https://www.bilibili.com/read/cv9477324/  

## mangopi r3  
https://mangopi.org/mangopi_r  
https://github.com/mangopi-sbc/buildroot-mangopi-r  

## dfrobot, mangopi r3  
https://wiki.dfrobot.com.cn/_SKU_DFR0780_MangoPi-R3#target_6  
https://wiki.dfrobot.com/MangoPi_R3_SKU_DFR0780  

## SO YOU WANT TO BUILD AN EMBEDDED LINUX SYSTEM?  
ARM9开发板对比（英文）  
https://jaycarlson.net/embedded-linux/  

## F1C100S/F1C200S系统构建  
https://littlevgl.readthedocs.io/en/latest/Doc/03.F1C100S_Linux/F1C100S_Linux.html  
