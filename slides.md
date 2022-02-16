---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
style: |
    section.photo h1,section.photo h2,section.photo h3,section.photo h4,section.photo h5,section.photo h6 {
        background-color: #888;
        color: #FFF;    
    }
    h6 {
        font-size: 30%;
    }
    img[alt~="centre"] {
        display: block;
        margin: 0 auto;
    }
marp: true
---

# Writing a single-tasking 'DOS' for Arm microcontrollers, in Rust

### Jonathan 'theJPster' Pallant
### ![](https://icongr.am/octicons/mark-github.svg) https://github.com/neotron-compute

---

# About me...

- Embedded Systems Engineer
- Rust Programmer and Trainer
	- Formerly: C++, Python, Pascal, BASIC...
- Ferrous Systems (www.ferrous-systems.com)
- ![](https://icongr.am/octicons/mark-github.svg) [thejpster](https://github.com/thejpster)
- ![](https://icongr.am/devicon/twitter-original.svg) [therealjpster](https://twitter.com/therealjpster)

---

# A Journey...

1. What is a 'DOS' (or even an 'OS')?
1. A Brief History of the OS
1. What is Neotron
1. Where is Neotron at right now?

<!-- let's play a game! Everytime I mention a company that's no longer with us, you wave your hands in the air -->

---
# What is a 'DOS' (or even an 'OS')?

- O.S. = Operating System
- D.O.S. = Disk Operating System

---

## What does a DOS do?

- It runs applications
- It runs on a computer
- It manages files (on disk)

---

## So what is an application?

![drop-shadow](./figs/application.svg)

---

## So what is an application?

![drop-shadow](./figs/application-in-out.svg)

<!--
Talk about batch processing, paper tapes, etc
-->

---

## What does a DOS do?

- ~~It runs applications~~
- It runs on a computer
- It manages files (on disk)

---

## What is a computer?

* Has a Central Processing Unit
	- Executes *Instructions*, has *Registers*
* Has memory:
	- Each location (a byte?) has a numeric address
	- Volatile vs Non-Volatile
* Has Input/Output devices
	- Often pretend to be memory
	- Display, Keyboard, Storage, Communications

<!-- You will need *some* non-volatile memory to boot, unless you want to flip toggle switches -->

---

<!-- _class: photo --> 

![bg cover](./figs/system360.jpeg)

## IBM System/360
###### Dave Ross - Flickr - CC BY 2.0

<!-- 1965-1978; 64K core memory; 8-bit; microcoded; 2x 5MB Magnetic disk drives; $133k -->

---

<!-- _class: photo --> 

![bg cover](./figs/pico.jpeg)

## Raspberry Pi Pico
###### Michael  Henzler - Wikimedia - CC BY-SA 4.0

<!-- 2021; 256K RAM; 2MB Flash; 2x 32-bit @ 133 MHz; $3 -->

---

## So an application just runs on the CPU?

- Yes, and no.
	* How much memory do you have?
	* What I/O devices do you have?
	* Is that the same as what the author had?
	* Do you really want to write everything from scratch?

---

## So, can we save some work here?

- Like, move the *common* parts out of each application?
- The bits that *operate* the computer ... *system* ?

![w:800px](./figs/application-computer.svg)

---

## So, can we save some work here?

- Like, move the *common* parts out of each application?
- The bits that *operate* the computer ... *system* ?

![w:800px](./figs/application-os-computer.svg)

---

## Operating Systems are about:

* Making applications smaller
* Making applications portable to other computers

---

# A Brief History of the OS

<!--

MULTICS
UNICS / UNIX
Control Program for Microcomputers CP/M
Xerox PARC
SCP-DOS / PC-DOS / MS-DOS / DOS Plus / DR-DOS
Lisa OS / Macintosh OS / System
OS/2
DR GEM
16-bit Windows 
AmigaDOS / Workbench
Digital VMS
16/32-bit Windows
Windows NT
-->

---

## IBM System/360

* 1965
* Basic Programming Support - punched cards only!
* BOS/360
* TOS/360
* DOS/360
* OS/360

<!-- OS/360 was a bit big, so smaller alternatives made -->

---

## MULTICS

* MIT / GE / Bell Labs - 1969
* Time-sharing for GE-645/Honeywell 6180
* No distinction between files and RAM
* Dynamic linking
* Hierarchical File System
* Kernel/User-space
* Written in PL/I

<!--
Multiplexed Information and Computing Service
Honeywell bought GE's computer division
you can still run PL/I on z/OS -->

---

## UNIX (or Unix)

* Bell Labs / AT&T - 1973
* Single-tasking; non-portable
	- They fix that later
* Devices are Files
* It kinda took off...

<!-- Uniplexed Information and Computing Service -->

---

### /dev/what?

* _Devices_ are usually memory mapped
* They have state.
* They are mutable.
* They are shared.
* Shared mutable state is _the worst_

---

### /dev/what?

* Make devices look like files
	* Now it's the OS's problem!
* __System Calls__
	* `open` and `close`
	* `write` and `read`, maybe `lseek`
	* `ioctl` for the weird stuff
* `/dev/tty` is a __file__ with *special properties*

<!-- You make them with mknod. Or use udev, which makes them in a tmpfs -->

---

### The UNIX family tree

* Bell Labs' "Research Unix" V1..V10
* AT&T System III, System V
* Microsoft Xenix, HP-UX, SGI IRIX, IBM AIX, Sun Solaris
* Berkeley System Distribution
	* Net/Open/Free BSD
	* Mac OS X (userland)

<!-- 4th Ed. was re-written in C -->

---

### The UNIX family tree

![h:500px](./figs/unix-history-simple.svg)

<!-- This is the simple version!! -->
---

## Digital Research CP/M

* For 8-bit Intel 8080 machines - 1974
	* Altair, IMSAI, Osborne, KayPro, Commodore, Sinclair, Amstrad
* Needs an ASCII Terminal, floppy drive, 16 KiB RAM
* OEM ports the BIOS, Digital Research supply BDOS + CCP
* ~~Hierarchical~~ File System
* `CON:` is a __psuedo-file__ with *special properties*

<!-- single user, single tasking -->

---

## PC-DOS / MS-DOS

* The IBM 5150 'Personal Computer' - 1981
	* 16-bit Intel 8088
	* Microsoft BASIC in ROM, Tape interface, 16 to 64KB RAM
* Microsoft buy 16-bit CP/M clone SCP-DOS and licence it to IBM
	* IBM BIOS, Microsoft DOS + `COMMAND.COM`
* First 'PC Compatible' from Columbia Data Products
	* Microsoft sell MS-DOS to anyone - CP/M is doomed
* `CON` is a __psuedo-file__ with *special properties*

<!-- it was also sold with CP/M-86 and UCSD p-System but not at launch -->

---

<!-- _class: photo --> 

![bg cover](./figs/ibm5150.jpeg)

## IBM PC 5150
###### Rama & Musée Bolo - Wikimedia - CC BY-SA 2.0 fr

---

## Apple

* Almost nothing on the Apple I
* BASIC on the Apple II
* Lisa OS
	* Includes a GUI based on the Xerox Star
* Macintosh System
	* Cut-down Lisa OS
	* Later ported from 68k to a PowerPC microkernel
* Mac OS X is *bone-fide* UNIX

<!-- 256 bytes of Wozmon! System isn't multi-tasking, and has a dumb name -->

---

## Commodore

* Microsoft BASIC on the 8-bits
	* Commodore DOS ran on the Floppy Drive!
* AmigaOS...
	* *Exec* was the multi-tasking Kernel
	* *AmigaDOS* was the OS (based on TRIPOS)
	* *Intuition* was the GUI
	* Partially in ROM (Kickstart)

---

## Atari

* Atari OS + Atari DOS + Atari BASIC on the 8-bits
* TOS on the 16-bit machines
	* Digital Research GEM Desktop + GEMDOS
* MultiTOS on the 32-bit machines

---

## Acorn

* MOS on the 8-bit machines (like the BBC Micro)
	* Disk Filing System
	* BBC BASIC was amazing
* RISC OS on the 32-bit machines
	* Advanced Disk Filing System
* Still going!

---

### RISC OS 

![centre h:500px](./figs/riscos.gif)

---

## Microsoft

* MS-DOS
* Xenix UNIX
* OS/2 with IBM
* 16-bit Windows (1.x, 2.x, 3.x)
* 16/32-bit Windows (95, 98, ME)
* 32-bit Windows NT (3.1, 3.5, 4, 2000, XP, Vista, 7, 8, 10, 11)

---

### Microsoft Windows 1.0

![centre h:500px](./figs/windows10.png)

<!-- Non-overlapping windows! -->

---

### Microsoft Windows NT

* Released in 1993 as Windows NT 3.1
* Portable
	* MIPS, x86, DEC Alpha, PowerPC, Itanium, x86-64, arm
* Compatible
	* OS/2, POSIX, Win16, Win32...
* Dave Cutler + co. came from doing VMS at Digital

---

![h:500px centre](./figs/vms-nt-manual.jpeg)

Microsoft said sorry with $100M + added DEC Alpha port

---

## Linux

* Is a Kernel
* GNU is Not Unix: C compiler, C library, shell, utilities
	* (more and more non-GNU components these days...)
* X11 compatible *Display Server* plus a *Window Manager*
* *Distributions* like Ubuntu, Arch, Slackware
	* It's like pick-n-mix

<!-- systemd, pipewire, Wayland - it's a pick-and-mix OS! -->

---

## The Aftermath

* ~~Commodore~~
* ~~CP/M~~
* ~~IBM~~ (well...)
* Microsoft Windows NT (Win32)
* POSIX (Portable Operating System Interface ... X?)
* ... WASI?

---

# What is Neotron

---

# Where is Neotron at right now?

---

# Questions!

* @therealjpster on Twitter
* https://github.com/neotron-compute
  