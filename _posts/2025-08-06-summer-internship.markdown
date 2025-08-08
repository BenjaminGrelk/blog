---
layout: post
title:  "Interning at Elemental Scientific, Inc."
date:   2025-08-06 20:08:13 -0500
categories: internship software-engineering reflection
---

## 👋 Introduction

Hi! I'm Benjamin Grelk, a software engineering student at the University of Nebraska–Lincoln. This summer, I had the opportunity to intern at Elemental Scientific, Inc. (ESI), a Nebraska-based company that develops hardware and software for automating liquid sample analysis — often in environments where safety, reliability, and efficiency are crucial.

In this blog, I’ll walk through what I worked on, reflect on the challenges I overcame, and share some lessons I’ll carry with me into my future career as a software engineer.

---

## 🧪 About ESI

ESI specializes in instrumentation and software that work with **ICP-MS (Inductively Coupled Plasma Mass Spectrometry)** and other lab equipment. Their automation systems are used in labs, manufacturing, and clinical environments — replacing tasks that would otherwise require chemists to interact with hazardous liquids.

As part of the Software Team (around 20 developers strong), I worked on core systems that enable ESI’s hardware and software to communicate smoothly.

---

## 🔧 Tools and Workflow

Our team used:

- **Languages & Frameworks:** C#, .NET, WinForms, WPF
- **Version Control:** Bitbucket (Git)
- **Project Management:** Jira for issue tracking
- **Documentation:** Confluence
- **Workflow:** Feature branch model off a `BaseDev` branch

Each developer typically owned their own projects and communicated closely with chemists who needed features implemented.

---

## 🛠️ Project Spotlight: Device Simulator Framework

### 🧩 The Context

At ESI, we often need to test our software without having access to the actual physical hardware. To enable this, the software includes **simulators** that mimic device behavior over serial communication. Previously, simulator data was stored in a shared format with real device setup files, distinguished only by having `"Simulator"` in the name. This method was:

- **Unclear** for new developers
- **Unsafe**, mixing simulator and real hardware data
- **Hard to extend** for new device types

### 🎯 The Task

I was tasked with:

- Creating a new file format dedicated to storing simulator data
- Developing a UI to help developers add and edit this data easily
- Refactoring the simulator system for long-term maintainability

### 🧠 My Solution

I introduced a **strongly-typed simulator data model**, starting with an abstract `SimulatorData` class. Each device type would inherit from this base class and define its own properties. These types were serializable to file, providing a clean, isolated storage format for simulators.

For the UI, I used **reflection** to dynamically load these types and their fields into an editable table. Based on field type, the UI rendered the appropriate input:

- **Strings** → textboxes  
- **Integers** with a range → numeric up/down  
- **Booleans** → checkboxes  
- **Enums** → dropdowns  

Attributes on each class controlled things like field names, ranges, and read-only status — so developers could modify behavior without touching the UI code.

Here’s a screenshot of the working editor:

![Device Simulator UI](assets/esi-simulator-configuration-ui.png)

### 🔄 Refactoring and Architecture

Once I had a working prototype, I spent time restructuring the architecture with a focus on:

- **Separation of concerns**
- **Maintainability**
- **Dependency injection**

This system is designed to be extended and updated by future developers without deep familiarity with the underlying code.

---

## 📘 Documentation and Demo

I wrote detailed internal documentation in Confluence, including:

- An overview of the simulator system
- A breakdown of the architecture and key namespaces
- A guide for adding support for new simulators

I also presented my work to the team in a Microsoft Teams meeting to ensure everyone understood how to use and maintain it.

---

## 🧠 Skills Gained

This internship helped me grow in many areas:

- **Code quality**: I learned to write clean, extensible, and testable code.
- **Legacy systems**: I became more mindful of breaking dependencies and bad conventions that can “calcify” over time.
- **Initiative**: I often identified tasks, planned solutions, and carried them out independently.
- **Communication**: I kept the team updated and ensured that my work was accessible and well-documented.

---

## 🤔 Reflection

### ✅ What I Did Well
- Developed a working solution that meets internal needs
- Prioritized good software architecture
- Created helpful tools and documentation that will live beyond my internship

### ❌ What I Could Improve
- I broke some existing functionality early on and had to backtrack
- I sometimes spent longer than expected on tasks due to inexperience

These are natural learning moments, especially in a first internship — and I'm proud of how I handled them.

---

## 🏢 Thoughts on the Company Structure

While I greatly appreciated the autonomy and exposure to production systems, ESI’s **flat organizational structure** posed some challenges.

Requests for software changes came directly from chemists to developers, which led to:
- Vague or incomplete specs
- Unclear prioritization
- Little delegation from above

While this avoids middle management friction, I believe a central intake and delegation system could improve clarity and reduce misunderstandings.

---

## 🧭 Looking Ahead

This internship confirmed for me that I want to be a **professional software engineer**. I’ll be seeking future internships at companies with different structures or domains so I can better understand the kind of work and environment I thrive in.

No matter where I go next, I’ll carry this experience with me — both the technical lessons and the professional ones.

---

Thanks for reading! Feel free to connect or reach out if you want to chat about internships, software engineering, or accessibility in tech.
