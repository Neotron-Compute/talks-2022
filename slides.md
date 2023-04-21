---
theme: gaia
paginate: true
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

<!-- _class: lead -->
# Is the Raspberry Pi Pico a computer?
## Jonathan 'theJPster' Pallant

---

## Who am I?

- Embedded Systems Engineer
- Rust Programmer and Trainer
	- Formerly: C++, Python, Pascal, BASIC...
- Ferrous Systems ([ferrous-systems.com](https://www.ferrous-systems.com))
- ![](https://icongr.am/octicons/mark-github.svg) [github.com/thejpster](https://github.com/thejpster)
- ![](https://icongr.am/simple/mastodon.svg) [@thejpster@hachyderm.io](https://hachyderm.io/@thejpster)
- ![](https://icongr.am/clarity/book.svg) [neotron-compute.github.io](https://neotron-compute.github.io)


---

<!-- _class: lead -->

# Our question: Is the Raspberry Pi Pico a computer?

---

<!-- _class: lead -->

# What is a computer?

---

## Some examples...

* IBM System/360
* Altair 8800
* IBM PC 5150
* Commodore Amiga 500
* Apple iPad

---

## Some features...

* Processing Power
* Inputs
* Outputs
* Storage
* Can I run *my* code on it?

---

<!-- _class: photo --> 

![bg cover](./figs/system360.jpeg)

## IBM System/360 Model 30 (1965)
###### Dave Ross - Flickr - CC BY 2.0

<!-- 1965-1978; 64Kx8 memory; 8-bit; microcoded; 1 MHz; 35k op/sec; 8 cycle register access; 2x 5MB Magnetic disk drives; $133k -->

---

<!-- _class: photo --> 

![bg cover](./figs/altair.jpg)

## MITS Altair 8800 (1975)

<!-- 1982; 2.0 MHz 8080; 1K RAM; No ROM; BASIC was optional (and required more RAM and was loaded from paper tape); Serial, Parallel or Audio Cassette interfaces were optional -->

---

<!-- _class: photo --> 

![bg cover](./figs/ibm5150.jpeg)

## IBM PC 5150 (1892)
###### Rama & Musée Bolo - Wikimedia - CC BY-SA 2.0 fr

<!-- 1982; 4.77 MHz 8088; 64K RAM; 320K FDD; BASIC in ROM; Cassette interface, $1500 (C64 was $595) -->

---

<!-- _class: photo --> 

![bg cover](./figs/amiga.jpg)

## Commodore Amiga 500 (1987)
###### Bill Bertram - Wikipedia - CC BY 2.5

---

<!-- _class: photo --> 

![bg cover](./figs/macbook.jpg)

## Apple MacBook M1 Pro (2021)
###### Premeditated - Wikipedia - CC BY-SA 4.0

---

## Processing Power

|      | System 360 | Altair 8800 | IBM PC | Amiga 500 | Mac Book |
| ---- | ---------- | ----------- | ------ | --------- | -------- |
| MIPS | 0.03       |

---

## Processing Power

|      | System 360 | Altair 8800 | IBM PC | Amiga 500 | Mac Book |
| ---- | ---------- | ----------- | ------ | --------- | -------- |
| MIPS | 0.03       | 0.3         |

---

## Processing Power

|      | System 360 | Altair 8800 | IBM PC | Amiga 500 | Mac Book |
| ---- | ---------- | ----------- | ------ | --------- | -------- |
| MIPS | 0.03       | 0.3         | 0.4    |

---

## Processing Power

|      | System 360 | Altair 8800 | IBM PC | Amiga 500 | Mac Book |
| ---- | ---------- | ----------- | ------ | --------- | -------- |
| MIPS | 0.03       | 0.3         | 0.4    | 1.4       |

---

## Processing Power

|      | System 360 | Altair 8800 | IBM PC | Amiga 500 | Mac Book |
| ---- | ---------- | ----------- | ------ | --------- | -------- |
| MIPS | 0.03       | 0.3         | 0.4    | 1.4       | ~200,000 |

---

## Inputs

|       | System 360 | Altair 8800 | IBM PC    | Amiga 500 | Mac Book |
| ----- | ---------- | ----------- | --------- | --------- | -------- |
| MIPS  | 0.03       | 0.3         | 0.4       | 1.4       | ~200,000 |
| Input | Serial     | Serial      | KB/Serial | KB/Serial | KB/USB   |

---

## Outputs

|        | System 360 | Altair 8800 | IBM PC  | Amiga 500 | Mac Book |
| ------ | ---------- | ----------- | ------- | --------- | -------- |
| MIPS   | 0.03       | 0.3         | 0.4     | 1.4       | ~200,000 |
| Input  | Serial     | Serial      | KB      | KB        | KB/etc.  |
| Output | Serial     | Serial      | Monitor | TV        | LCD/etc. |

---

## Storage

|         | System 360 | Altair 8800 | IBM PC     | Amiga 500 | Mac Book |
| ------- | ---------- | ----------- | ---------- | --------- | -------- |
| MIPS    | 0.03       | 0.3         | 0.4        | 1.4       | ~200,000 |
| Input   | Serial     | Serial      | KB         | KB        | KB/etc.  |
| Output  | Serial     | Serial      | Monitor    | TV        | LCD      |
| Storage | Mag Tape   | Paper Tape  | 5.25" Disk | 3.5" Disk | SSD      |

---

## Can I run *my* code on it?

|          | System 360 | Altair 8800 | IBM PC   | Amiga 500 | Mac Book |
| -------- | ---------- | ----------- | -------- | --------- | -------- |
| Input    | Serial     | Serial      | KB       | KB        | KB/etc.  |
| Output   | Serial     | Serial      | Monitor  | TV        | LCD      |
| Storage  | Mag Tape   | Paper Tape  | 5¼" Disk | 3½" Disk  | SSD      |
| Run Code | Yes        | Yes         | Yes      | Yes       | Yes      |

---

<!-- _class: photo --> 

![bg cover](./figs/ipads.jpg)

## Apple iPad (2010)
###### Maurizio Pesce - Wikipedia - CC-BY 2.0

---

## Is the iPad a computer?

|          | iPad (2010) |
| -------- | ----------- |
| MIPS     | 10,000      |
| Input    | Touchscreen |
| Output   | LCD         |
| Storage  | SSD         |
| Run Code | ....?       |

---

<!-- _class: lead -->

# What is the Raspberry Pi Pico?

---

## A PCB with a Microcontroller

* Processor
* RAM
* Sometimes ROM
* Serial/Parallel Interfaces
* Clock / Phased-Locked-Loop

---

## The RP2040

* Two Arm Cortex-M0+ Processors
* 264 KiB RAM
* Interface for example Flash ROM
* Lots of serial/parallel interfaces
* Requires external 12 MHz crystal

---

## Inputs/Outputs

|          | Pi Pico     |
| -------- | ----------- |
| MIPS     | 120         |
| Input    | Serial      |
| Output   | Serial      |
| Storage  | Flash       |
| Run Code | ....        |

---

## Can I run *my* code on it?

* Not without another computer!

---

<!-- _class: lead -->

# The Neotron Project

---

## What is it?

* An open-source computing platform, designed around Arm Microcontrollers.
* The BIOS and OS are written in Rust

---

## Why it exists

> Neotron is an attempt to make computers simple again, whilst also taking advantage of the very latest in programming language development.

---

## The Neotron 32

![centre h:500px](./figs/neotron-32.jpg)

---

## The Neotron Pico

![centre h:500px](./figs/neotron-pico-pcb.jpg)

---

## The Neotron Pico

* PS/2 Keyboard Input
* VGA Video Output
* SD Card for storage
* 16-bit stereo audio
* Four expansion slots

---

# Conclusions!

---

<!-- _class: lead -->

# Is the Pi Pico a computer?
# No

---

<!-- _class: lead -->

# Can you turn it into a computer?
# Yes

---

<!-- _class: lead -->

# Would you like to see it?
# It's on display outside!

---

## Where can I found out more?

* <https://neotron-compute.github.io>
* My hackaday.io blog
* Bil Herd's YouTube channel
* @thejpster@hachyderm.io on Mastodon
