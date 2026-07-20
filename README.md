# Neuro-Adaptive-Smart-Living-Interfaces
Eye-Gesture Based Smart Assistive Platform for Home Automation, Secure Access Control and Intelligent Mobility


> **A unified assistive technology platform that enables individuals with severe motor disabilities to interact with their surroundings using eye gestures.**
>
> The project integrates **Electrooculography (EOG)** based intention detection, MATLAB-based intelligent control, ESP32-driven IoT communication, secure access control, smart home automation and an intelligent wheelchair into one modular ecosystem.

---

## Overview

This repository presents the design and implementation of a neuro-adaptive assistive platform intended to improve accessibility for individuals with severe motor impairments. The proposed system employs Electrooculography (EOG)-based intention detection to enable hands-free interaction with multiple assistive technologies through a unified control framework.

Unlike conventional assistive solutions that address individual tasks independently, the proposed platform integrates smart home automation, secure access control, emergency assistance, and intelligent mobility into a single modular architecture. Eye movement signals acquired using a BioAmp EXG module are processed in real time and translated into control commands through a MATLAB-based supervisory interface. These commands are transmitted over a wireless TCP/IP network to multiple ESP32-based embedded nodes responsible for device-specific control.

The project was initially developed as a proof-of-concept assistive environment comprising lighting control, fan operation, smart door access, emergency response, and auxiliary automation features. The same design principles were subsequently extended to develop an intelligent eye-controlled wheelchair prototype for the VIT E-Codeathon, demonstrating the scalability of the proposed architecture beyond home automation applications.

The repository documents the complete engineering workflow, including biomedical signal acquisition, embedded system development, distributed wireless communication, MATLAB application development, custom hardware schematic design, prototype implementation, and experimental validation. The work further resulted in the filing of an Indian patent application and recognition at the VIT E-Codeathon with a Third Prize.

---

<img width="802" height="380" alt="image" src="https://github.com/user-attachments/assets/eaadf81c-4ef6-441f-96b9-885ceb7f54e1" />

*Complete Block Diagram of the Proposed Model*

---

## Major Contributions

- Development of a unified EOG-based assistive platform integrating home automation, secure access control, and intelligent mobility.
- Design of a modular distributed embedded architecture employing multiple ESP32 controllers communicating through TCP/IP.
- Development of a MATLAB App Designer-based supervisory interface for centralized device monitoring and control.
- Implementation of real-time EOG signal acquisition and command interpretation using the BioAmp EXG module.
- Prototype implementation of lighting control, fan control, smart security lock, emergency assistance, and auxiliary automation modules.
- Extension of the proposed framework into an intelligent eye-controlled wheelchair featuring obstacle detection and hands-free navigation.
- Progression from breadboard-based validation to a custom hardware schematic suitable for future PCB implementation.
- Filing of an Indian patent application based on the proposed assistive platform.
- Award of Third Prize at the VIT E-Codeathon for the intelligent wheelchair implementation.

---

## Table of Contents

1. [Overview](#overview)
2. [Motivation](#motivation)
3. [Existing Challenges](#existing-challenges)
4. [Selection of Electrooculography (EOG)](#selection-of-electrooculography-eog)
5. [Proposed Solution](#proposed-solution)
6. [System Architecture](#system-architecture)
7. [Hardware Architecture](#hardware-architecture)
8. [Signal Processing Framework](#signal-processing-framework)
9. [Communication Framework](#communication-framework)
10. [MATLAB Supervisory Interface](#matlab-supervisory-interface)
11. [Patent Prototype](#patent-prototype)
12. [Smart Home Automation](#smart-home-automation)
13. [Security Lock System](#security-lock-system)
14. [Intelligent Wheelchair Prototype](#intelligent-wheelchair-prototype)
15. [Repository Structure](#repository-structure)
16. [Hardware Components](#hardware-components)
17. [Software Architecture](#software-architecture)
18. [Installation and Usage](#installation-and-usage)
19. [Experimental Results](#experimental-results)
20. [Achievements](#achievements)
21. [Future Scope](#future-scope)
22. [Citation](#citation)
23. [License](#license)

---

# Motivation

Individuals affected by paralysis, spinal cord injuries, neuromuscular disorders, or other severe motor impairments often encounter significant challenges while interacting with their immediate environment. Routine activities such as operating electrical appliances, unlocking doors, requesting assistance, or navigating indoors generally require physical interaction with switches, controllers, or mobility aids. Existing assistive technologies frequently depend on residual hand movement, speech-based commands, or expensive brain-computer interface (BCI) systems, limiting their accessibility and practical adoption.

Although numerous research efforts have demonstrated individual assistive solutions, most address a single functionality in isolation. Home automation, intelligent wheelchairs, security systems, and emergency response mechanisms are commonly developed as independent systems, resulting in increased hardware complexity, higher deployment costs, and limited interoperability.

The objective of this work was therefore to design a unified assistive platform capable of integrating multiple daily living functionalities under a common supervisory framework while maintaining a low-cost, modular, and scalable architecture suitable for practical deployment.

---

# Existing Challenges

The development of the proposed platform was motivated by several practical limitations observed in existing assistive technologies.

- Commercial EEG-based Brain–Computer Interface systems generally require expensive acquisition hardware, extensive calibration procedures, and sophisticated signal processing algorithms.
- Voice-controlled systems become unsuitable for users affected by speech impairments or environments with significant acoustic interference.
- Joystick-operated wheelchairs and conventional home automation interfaces require voluntary limb movement, making them inaccessible for individuals with severe locomotor disabilities.
- Many existing smart home systems operate as isolated solutions without a centralized supervisory interface capable of coordinating multiple assistive functions.
- Research prototypes often demonstrate proof-of-concept implementations for individual applications but seldom integrate home automation, secure access control, emergency response, and intelligent mobility within a single architecture.

These observations motivated the development of a modular platform capable of serving as a common assistive framework for multiple applications.

---

# Selection of Electrooculography (EOG)

Instead of employing Electroencephalography (EEG) for intention detection, this work utilizes Electrooculography (EOG) to capture voluntary eye movements.

Compared to EEG, EOG provides several practical advantages for assistive applications:

| Aspect | EEG | EOG (Proposed System) |
|---------|-----|-----------------------|
| Signal acquisition | Brain activity | Eye movement potential |
| Calibration | Relatively complex | Minimal calibration |
| Signal amplitude | Very low (µV range) | Higher amplitude |
| Real-time implementation | Computationally intensive | Simpler processing pipeline |
| Hardware cost | High | Low |
| Practical deployment | Moderate | High |

Since eye movement generally remains controllable even in individuals with severe motor impairments, EOG provides an effective non-invasive interface for human-machine interaction while significantly reducing system complexity.

---

Figure 2 illustrates the fundamental architecture of a Brain–Computer Interface, while Figures 3 and 4 summarize the signal processing and acquisition stages employed by the proposed system.

<img width="760" height="220" alt="image" src="https://github.com/user-attachments/assets/46fc5ebd-36a8-4ed3-96c2-f5f42215ce38" />
*Fundamental architecture of a Brain–Computer Interface (BCI).*

<img width="975" height="244" alt="image" src="https://github.com/user-attachments/assets/29e9856c-c129-41a8-80fe-29d107be59ef" />
*Signal processing sequence adopted for the proposed system.*

<img width="510" height="248" alt="image" src="https://github.com/user-attachments/assets/602fd857-b1aa-4fe0-95bc-1854e16e5760" />
*Signal acquisition workflow.*

---

# Proposed Solution

The proposed Neuro-Adaptive Smart Living Platform integrates biomedical signal acquisition, embedded control, wireless communication, and intelligent assistive technologies into a unified architecture.

The system acquires EOG signals using a BioAmp EXG module, which performs the initial analog front-end conditioning of low-amplitude biopotential signals. The conditioned signals are digitized and processed to identify predefined eye-gesture patterns corresponding to user commands.

A MATLAB-based supervisory application interprets these commands and communicates with multiple ESP32 controllers through TCP/IP communication over a local wireless network. Each embedded controller is assigned to an individual subsystem, thereby enabling distributed operation while maintaining centralized supervision.

The modular architecture allows independent implementation of several assistive functions, including:

- Smart lighting control
- Fan operation
- Secure electronic door access
- Emergency assistance (SOS)
- Intelligent wheelchair navigation

This distributed design minimizes controller workload, improves maintainability, and allows additional assistive modules to be incorporated with minimal hardware and software modifications. Figure 5 illustrates the distributed TCP/IP communication architecture adopted for coordinating multiple embedded nodes within the proposed platform.


<img width="758" height="663" alt="image" src="https://github.com/user-attachments/assets/c8366c45-2f71-4bb3-aa52-dd70c86ca1c5" />
*TCP/IP communication architecture between the MATLAB supervisory interface and multiple ESP32-based embedded controllers.*

---

# Power Distribution

The hardware platform is powered using a dual-cell 18650 lithium-ion battery pack supplying a nominal output voltage of 7.4 V.

A DC–DC buck converter is employed to regulate the supply voltage for the embedded controllers, while individual actuators receive appropriate operating voltages according to their electrical specifications.

This arrangement provides electrical isolation between low-power control electronics and higher-current electromechanical loads, thereby improving system reliability during simultaneous operation of multiple devices.

---

# Distributed Embedded Architecture

The embedded architecture employs multiple ESP32 development boards connected through a common wireless network. Rather than assigning all control tasks to a single microcontroller, each controller manages one dedicated subsystem.

The distribution of responsibilities includes:

| Embedded Node | Assigned Function |
|---------------|-------------------|
| ESP32 – Node 1 | Smart Lighting Control |
| ESP32 – Node 2 | Fan Control |
| ESP32 – Node 3 | Security Lock System |
| ESP32 – Node 4 | Intelligent Wheelchair |
| ESP32 – Node 5 | Emergency (SOS) Module |
| ESP32 – Node 6 | Auxiliary Automation Functions |

This distributed approach offers several engineering advantages.

- Reduced computational burden on individual controllers.
- Simplified debugging and maintenance.
- Improved fault isolation.
- Independent firmware updates.
- Straightforward integration of future assistive modules.

---

# System Workflow

The operation of the proposed platform follows a sequential processing pipeline beginning with the acquisition of physiological signals and ending with physical actuation of assistive devices.

1. Eye movements generated by the user are captured using surface electrodes.

2. The acquired Electrooculography (EOG) signals are amplified and conditioned using the BioAmp EXG analog front-end.

3. The conditioned analog signal is digitized and processed to identify predefined eye gesture patterns.

4. The interpreted user command is transmitted to the MATLAB supervisory application.

5. MATLAB validates the received command and determines the corresponding assistive action.

6. The selected command is transmitted over a local wireless TCP/IP network.

7. The respective ESP32 controller receives the command and activates the assigned subsystem.

8. The actuator executes the requested operation while maintaining independent control of the remaining subsystems.

This layered workflow separates signal acquisition, signal processing, communication, and hardware control into distinct functional stages, allowing each subsystem to be independently developed, tested, and upgraded.

---

# Functional Architecture

The proposed system can be viewed as five interconnected functional layers.

| Layer | Primary Function |
|---------|------------------|
| Signal Acquisition Layer | Captures EOG signals using BioAmp EXG and surface electrodes |
| Signal Processing Layer | Processes eye gestures and generates digital control commands |
| Supervisory Control Layer | MATLAB App Designer interface responsible for command interpretation and system coordination |
| Communication Layer | Wireless TCP/IP communication between MATLAB and distributed ESP32 controllers |
| Embedded Control Layer | Individual ESP32 nodes controlling dedicated assistive devices |

The layered implementation improves modularity by ensuring that modifications within one subsystem do not affect the operation of the remaining components.

---

# Hardware Implementation

The hardware implementation was developed with emphasis on modularity, scalability, and ease of integration. Rather than employing a single controller for all assistive functions, the proposed platform distributes individual tasks across multiple embedded nodes interconnected through a wireless local area network. This approach simplifies system integration, enables independent subsystem testing, and facilitates future hardware expansion without major architectural modifications.

The initial prototype was implemented on a breadboard to validate signal acquisition, wireless communication, and embedded control. Following successful validation, the hardware was consolidated into a custom schematic representing the proposed integrated implementation for future PCB realization.

The hardware architecture consists of four principal subsystems:

- EOG signal acquisition subsystem
- Supervisory control subsystem
- Distributed embedded control subsystem
- Actuation subsystem

Each subsystem operates independently while remaining coordinated through the MATLAB supervisory interface.

---

## Hardware Architecture

The proposed hardware architecture integrates biomedical signal acquisition with embedded control and electromechanical actuation through a distributed network of ESP32 development boards.

The EOG acquisition subsystem captures voluntary eye movements using surface electrodes connected to the BioAmp EXG analog front-end. The processed signals are interpreted by the supervisory application, which subsequently communicates with the embedded controllers responsible for device-specific operation.

The distributed embedded nodes independently control the smart lighting system, fan, security lock mechanism, emergency assistance module, auxiliary functions, and intelligent wheelchair platform.

This separation of responsibilities minimizes computational overhead on individual controllers while improving reliability and simplifying future maintenance.

<img width="751" height="424" alt="image" src="https://github.com/user-attachments/assets/4c7fe118-1fcd-4a81-b476-955346d3db7f" />

<img width="752" height="413" alt="image" src="https://github.com/user-attachments/assets/99114205-bee5-4414-accc-3bb77eda8d8d" />

<img width="763" height="446" alt="image" src="https://github.com/user-attachments/assets/24afbdb3-381b-4df6-ae5c-f2a067bf9163" />

<img width="566" height="262" alt="image" src="https://github.com/user-attachments/assets/a109a67a-b01f-4409-b301-d0972927d22f" />

*Custom hardware circuit diagram illustrating the integration of the BioAmp EXG module, ESP32 controllers, sensors, actuators, and power distribution.*

---

## Hardware Configuration

The complete prototype consists of biomedical sensing hardware, embedded controllers, communication modules, sensing devices, actuators, and power electronics integrated into a unified assistive platform.

| Category | Implementation |
|-----------|----------------|
| Signal Acquisition | Surface electrodes with BioAmp EXG analog front-end |
| Supervisory Control | MATLAB App Designer |
| Embedded Processing | Distributed ESP32 development boards |
| Communication | TCP/IP over Wi-Fi |
| User Authentication | Password-based and EOG-assisted security mechanism |
| Home Automation | Lighting, fan, emergency response and auxiliary control |
| Mobility | Intelligent wheelchair platform with obstacle detection |
| Power Supply | Dual-cell Li-ion battery with regulated DC-DC conversion |

---

## Prototype Development

The development of the hardware followed an incremental implementation strategy.

1. Individual hardware modules were initially validated independently.
2. Wireless communication between MATLAB and embedded controllers was established.
3. Home automation modules were integrated into a common supervisory framework.
4. Security lock functionality was incorporated into the control architecture.
5. The complete assistive platform was assembled and experimentally validated.
6. The architecture was subsequently extended to an intelligent eye-controlled wheelchair without modifying the core communication framework.

This staged implementation enabled independent verification of each subsystem before integration into the complete assistive platform, thereby reducing debugging complexity and improving overall system reliability.

---

## Design Considerations

Several architectural decisions were adopted during the hardware development to improve flexibility and long-term maintainability.

- Modular subsystem implementation allowing independent hardware validation.
- Distributed embedded processing to reduce controller workload.
- Wireless communication eliminating extensive interconnecting cables.
- Reusable communication framework for integrating future assistive modules.
- Hardware abstraction through MATLAB-based supervisory control.
- Migration from breadboard validation toward a consolidated hardware schematic suitable for future PCB realization.
