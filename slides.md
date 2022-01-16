---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

# Neotron at ACCU 2022

Writing a single-tasking 'DOS' for Arm microcontrollers, in Rust

https://github.com/neotron-compute

---

# About me...

* Embedded Systems Engineer
* Rust Programmer and Trainer
    * Formerly: C++, Python, Pascal, BASIC...
* Ferrous Systems (www.ferrous-systems.com)

---

# A Journey...

* What is a 'DOS' (or even an 'OS')?
* A Brief History of the OS
* What is Neotron
* Where is Neotron at right now?

---

# What is a DOS?

* It stands for: Disk Operating System


---

## What does it do?

* It runs applications

---

## So what's an application?

```
+---------------+
|  Application  |
+---------------+
```

---

## So what's an application?

* A piece of software (a program)
* You can start it and stop it
* It does a job

---

## What's a computer?

* Has a Central Processing Unit
   * Executes Instructions, has *Registers*
* Has memory:
    * Each location (a byte?) has a address
    * Most memory is volatile
    * Need some Non-volatile memory to boot
* Has Input/Output devices
    * Often pretend to be memory
    * Display, Keyboard, Storage, Communications

---

### So an application runs on the CPU?

* Yes, and no.
* How much memory do you have?
* What I/O devices do you have?
* Is that the same as what the author had?
* Do you really want to write everything from scratch?

---

## So, can we save some work here?

* Like, move the *common* parts out of each application?
* The bits that *operate* the computer

```
+----------------+
|   Application  |
+----------------+
|Operating System|
+----------------+
|    Hardware    |
+----------------+
```

---

# A Brief History of the OS

---

# What is Neotorn

---

# Where is Neotron at right now?

---

# Questions!

* @therealjpster on Twitter
* https://github.com/neotron-compute
