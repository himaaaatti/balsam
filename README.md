# balsam

balsam is Operating System and, use the Linux kernel as reference.

Kernel Image
---

```
BOOT=arch/x86/boot  
+-----------------------------------+ 0 byte    (1st sector)
| $(BOOT)/loader/loader.img         |   
+-----------------------------------+ 512 byte  (2nd sector)
| $(BOOT)/bootsector/bootsector.img |  
+-----------------------------------+ 1024 byte (3th sector)
| $(BOOT)/header.img                |  
+-----------------------------------+ 1536 byte (4th sector)
| kernel.img                        |
+-----------------------------------+ (1536 + 180KiB(10 cylinder)) byte  
```

Memory Map in boot
---
```
x86_32
+-----------------------------------+ 0x00000000
| Real Mode Interrupt Vector Table  |   (1 KibB)
+-----------------------------------+ 0x00000400
| BIOS data area                    |   (256 bytes)
+-----------------------------------+ 0x00000500
| Stack for setup                   |   
+-----------------------------------+ 0x00007C00
| Boot Loader is loaded by BIOS     |   (512 bytes)
+-----------------------------------+ 0x00007E00
| Kernel Image (bootsector)         |   (512 bytes)
+-----------------------------------+ 0x00008000
| Kernel Image (setup code)         |   (512 bytes)
+-----------------------------------+ 0x00008200
| Temporary Kernel Image (protected)|
+-----------------------------------+ 0x00080000
| Free Memory                       |
+-----------------------------------+ 0x0009FC00
| Extended BIOS bata area           |
+-----------------------------------+ 0x000A0000
| Video RAM area                    |
+-----------------------------------+ 0x000BFFFF
| Monochrome video memory           |
+-----------------------------------+ 0x000BFFFF
| ROM and etc area                  |
+-----------------------------------+ 0x00100000

```

Global Segment Descriptor Table 
---
```
before kernel entry point

+-----------------------------------+ 0x00
| Null Segment Descriptor           |   
+-----------------------------------+ 0x08
| Code Segment Descriptor           |   
+-----------------------------------+ 0x10
| Data Segment Descriptor           |   
+-----------------------------------+ 0x18

```

swapper page directory
---
```

```

License
---
Copyright (c) 2015 Shunsuke Mie  
This software is released under the GNU General Public License v2.0.  
Please see below link.  
[gpl-2.0.txt](https://www.gnu.org/licenses/old-licenses/gpl-2.0.txt)


