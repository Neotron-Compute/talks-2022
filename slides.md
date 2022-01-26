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
---

# <!-- fit --> Neotron at ACCU 2022

Writing a single-tasking 'DOS' for Arm microcontrollers, in Rust

![](https://icongr.am/octicons/mark-github.svg) https://github.com/neotron-compute

---

# About me...

- Embedded Systems Engineer
- Rust Programmer and Trainer
    - Formerly: C++, Python, Pascal, BASIC...
- Ferrous Systems (www.ferrous-systems.com)

---

# A Journey...

- What is a 'DOS' (or even an 'OS')?
- A Brief History of the OS
- What is Neotron
- Where is Neotron at right now?

---

# What is a DOS?

- D.O.S. = Operating System


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
    - Executes Instructions, has *Registers*
* Has memory:
    - Each location (a byte?) has a address
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

---

### So an application just runs on the CPU?

- Yes, and no.
    * How much memory do you have?
    * What I/O devices do you have?
    * Is that the same as what the author had?
    * Do you really want to write everything from scratch?

---

## So, can we save some work here?

- Like, move the *common* parts out of each application?
- The bits that *operate* the computer

![w:800px](./figs/application-computer.svg)

---

## So, can we save some work here?

- Like, move the *common* parts out of each application?
- The bits that *operate* the computer

![w:800px](./figs/application-os-computer.svg)

---

# Operating Systems are about:

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

# What is Neotorn

---

# Where is Neotron at right now?

---

# Questions!

* @therealjpster on Twitter
* https://github.com/neotron-compute
