# Introduction

## What is an Embedded System?

An embedded system is a computer system with a dedicated function within a larger mechanical or electrical system, often with real-time computing constraints. It is embedded as part of a complete device often including hardware and mechanical parts. Embedded systems control many devices in common use today. Ninety-eight percent of all microprocessors are manufactured as components of embedded systems.

Even though often nearly invisible, embedded systems are ubiquitous. Embedded systems are present in many industries, including industrial automation, defense, transportation, and aerospace. For example, NASA s Mars Path Finder, Lockheed Martin s missile guidance system, and the Ford automobile all contain numerous embedded
systems.

A general definition of embedded systems is: embedded systems are computing systems with tightly coupled hardware and software integration, that are designed to perform a dedicated function.

They are often used in applications where a computer would be too expensive, too large, or too power hungry. Examples of embedded systems include:

* Digital cameras
* Video game consoles
* Automobiles
* Medical devices
* Smartphones
* Smart watches
* Smart TVs
* Smart refrigerators
* ...

Embedded systems may as well exist as a standalone system such as internet router.

### What is Embedded Software Engineering?

Embedded software engineering is the process of developing software for embedded systems. Embedded systems are computers that are designed to perform a specific task.

## Embedded Processors and Application Awareness

The processors found in common personal computers (PC) are general-purpose or universal processors. They are complex in design because these processors provide a full scale of features and a wide spectrum of functionalities.
They are designed to be suitable for a variety of applications. The systems using these universal processors are programmed with a multitude of applications. For example, modern processors have a built-in memory management unit (MMU) to provide memory protection and virtual memory for multitasking-capable, general-purpose operating systems. These universal processors have advanced cache logic. Many of these processors have a built-in math co-processor capable of performing fast floating-point operations. These processors provide interfaces to support a variety of external peripheral devices. These processors result in large power consumption, heat production, and size. The complexity means these processors are also expensive to fabricate. In the early days, embedded systems were commonly built using general-purpose processors.

Because of the quantum leap in advancements made in microprocessor technology in recent years, embedded systems are increasingly being built using embedded processors instead of general-purpose processors. These embedded processors are special-purpose processors designed for a specific class of applications. The key is application awareness, i.e., knowing the nature of the applications and meeting the requirement for those applications that it is designed to run.

## Hardware and Software co-design model

Commonly both the hardware and the software for an embedded system are developed in parallel. Constant design feedback between the two design teams should occur in this development model. The result is that each side can take advantage of what the other can do. The software component can take advantage of special hardware features to gain performance. The hardware component can simplify module design if functionality can be achieved in software that reduces overall hardware complexity and cost. Often design flaws, in both the hardware and software, are uncovered during this close collaboration.
The hardware and software co-design model reemphasizes the fundamental characteristic of embedded systems they are application-specific. An embedded system is usually built on custom hardware and software. Therefore, using this development model is both permissible and beneficial.

## Cross Development Platform

Another typical characteristic of embedded systems is its method of software development, called cross-platform development, for both system and application software. Software for an embedded system is developed on one platform but runs on another. In this context, the platform is the combination of hardware (such as particular type of processor), operating system, and software development tools used for further development.

**The host system** is the system on which the embedded software is developed. **The target system** is the embedded system under development.

## Software Storage and Upgradability

Software storage is a critical aspect of any embedded system, as it determines where and how the software is stored on the device. In general, there are two main types of storage: non-volatile and volatile. Non-volatile storage is typically used for long-term storage of software, while volatile storage is used for short-term storage during runtime.

In terms of software upgradability, there are two primary ways to achieve this in an embedded system: in-system programming (ISP) and bootloader.

**ISP** is the process of programming a device while it is still installed in the target system, and it requires a special hardware interface. This interface allows the user to connect to the device and reprogram it without having to physically remove it from the target system. ISP is useful in situations where the device is not easily accessible, such as in a remote location or in a sealed environment.

**A bootloader** is a small program that is stored in non-volatile memory on the device, and it is responsible for loading the main application into memory during the boot process. Bootloaders can be used to upgrade the software on the device without the need for external programming equipment. This is accomplished by sending a new software image to the device over a communication interface, such as UART or USB. The bootloader then stores the new image in non-volatile memory and reboots the device to start the new application.

One advantage of using a bootloader is that it allows for **over-the-air** **(OTA)** software updates, which means that the software can be updated remotely without physical access to the device. This is useful in situations where the device is in a location that is difficult to access or where there are a large number of devices that need to be updated.
