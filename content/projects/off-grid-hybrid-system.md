+++
title = "Off-Grid Hybrid System – Wind + Solar (Experimental and High-Power)"
date = 2026-02-01
summary = "A two-block hybrid energy system combining experimental wind+solar generation with a high-power 48V hybrid solar architecture."
description = "A complete off-grid hybrid installation designed for a remote house with unstable grid supply. Includes an experimental wind+solar block and a fully engineered high-power hybrid solar system with detailed justification, wiring, protection and component selection."
tags = ["Hybrid Energy", "Wind", "Solar", "LiFePO4", "MPPT", "Off-Grid", "System Design"]
type = "projects"
+++

# Off-Grid Hybrid System – Wind + Solar (Experimental and High-Power)

This project was developed for a house located at the highest point of a natural park, where the grid supply is extremely unstable. Power cuts are frequent, voltage fluctuates depending on the park’s overall demand, and even basic appliances such as a microwave cannot be used reliably.

The objective was clear:

- **Guarantee uninterrupted lighting and essential services**, regardless of the time of day.
- **Protect constant loads**, especially the refrigerator, from grid outages.
- **Create a scalable hybrid system** capable of supporting heavier loads such as air conditioning.

To achieve this, the installation was divided into two coordinated blocks:

1. **Experimental low-power wind + solar system**
2. **High-power hybrid solar system (final production system)**

---

# 1) Experimental Wind + Solar System (Low Power)

## Purpose

The first block was designed as an **experimental platform** to evaluate:

- Real wind generation potential at the site
- Behaviour of a certified MPPT wind controller
- Interaction between wind and solar inputs
- Performance of reused panels and a degraded LiFePO₄ battery

This block powers **12–14 V LED lighting**, ensuring basic illumination even during grid outages.

---

## Components and Rationale

### **Wind Turbine (800 W nominal)**
A low-cost 800 W turbine was selected due to the house’s elevated position and direct sea exposure.
However, real-world expectations are modest: **~50 W average** is far more realistic than the advertised 800 W.

### **Certified MPPT Wind/Solar Controller**
Most low-cost turbines include a simple diode rectifier with no safety logic.
Instead, a **certified MPPT controller** was chosen because it provides:

- Electronic protections
- Higher efficiency
- A **dumb-load output** to dissipate excess energy during strong winds
- Support for **up to 1000 W of solar input**

This ensures safe operation even when the battery is full and wind speeds are high.

### **Reused Solar Panels**
Old flexible panels from a previous project were reused.
Due to age and degradation, they produce **~100 W or less**, but this is acceptable for experimental purposes.

### **Reused LiFePO₄ Battery**
The battery is also reused and degraded.
This is intentional: the goal is to measure **true wind contribution**, not to build a high-performance system.

---

## Why This Block Exists

This system is **not** meant to power the house.
It is a **test bench** to understand:

- How much wind energy the site can realistically produce
- Whether a larger turbine is justified
- How the MPPT controller behaves under mixed wind/solar input
- How the dump load manages overspeed conditions

It also provides **always-on LED lighting**, independent from the main system.

---

# 2) High-Power Hybrid Solar System (Production System)

The second block is the **real power system** for the house.
It evolved through several stages: 12 V → 24 V → 48 V → and finally a **fully redesigned hybrid system** based on high-efficiency panels and a premium hybrid inverter.

---

# 2.1 Stage A — 24 V System (Intermediate Stage)

The first attempt to scale the system used a 24 V architecture.
This was an improvement over 12 V, but still insufficient for high-power loads.

### Problems with 12 V
- Currents reached **70 A**, requiring extremely thick and expensive cables.
- Voltage drop became significant.
- Efficiency suffered.

### Improvements at 24 V
A 24 V system reduced current and allowed:

- 16 × 100 W flexible panels (4S4P)
- Victron 150/60 MPPT
- 24 V 300 Ah LiFePO₄ bank
- 3500 W EDECOA inverter

However, flexible panels degrade quickly, and the inverter proved to be **just another Chinese unit**, not as reliable as expected.

This stage worked, but it was clear that:

- Flexible panels produce **very little power per square meter**
- Their cost per watt is high
- They degrade rapidly under sun exposure
- The inverter was not ideal for long-term reliability
- The system could not support large AC units

This led to a full redesign.

---

# 2.2 Stage B — Final 48 V Hybrid System (High Power)

## Why 48 V?

Battery discharge limits forced the upgrade:

- LiFePO₄ batteries typically allow **100 A continuous discharge**
- Power = Voltage × Current
- At 12/24/48 V → 1200 / 2400 / 4800 W maximum
- To run **3000–5000 frigorías AC units**, 48 V was mandatory

---

# Component Selection (Final System)

After a detailed market study, the following components were selected:

## **Solar Panels — JA Solar 605 W N-Type Bifacial (JAM72D40-MB)**
- **90 € per panel** → **540 € total**
- High efficiency
- Long lifespan
- Glass-based → far more durable than flexible panels
- Excellent cost per watt
- Bifacial → extra production from reflected light

Flexible panels were discarded because:

- They produce **very little power** for the space they occupy
- Their cost per watt is high
- They degrade quickly under sun exposure
- Glass panels last **much longer** and maintain performance

---

## **Hybrid Inverter — DEYE SUN-6K-SG05LP1-AM2 (6 kW, 48 V)**
- **860 €**
- Accepts **up to 500 V** of PV input
- Accepts **up to 120 A** of battery charge/discharge
- High reliability
- True hybrid operation (grid ↔ solar ↔ battery)
- Excellent monitoring and configurability

This inverter is **far superior** to EDECOA, which turned out to be just another generic Chinese inverter.

---

# Electrical Design (Final Version)

## PV Configuration: **6S1P**

All six 605 W panels are placed **in series**:

- Voltage ≈ **312 V**
- Current ≈ **15 A**

This is ideal because:

- High voltage → low current
- Low current → thinner cables
- Lower cost and lower voltage drop
- Perfect match for the DEYE inverter

### Cable Sizing

Using 12 AWG (55 A rating):

- Resistivity: 5.2 mΩ/m
- Distance: 20 m (worst case)
- Voltage drop:
  - R = 0.0052 × 20 = 0.104 Ω
  - Vdrop = 0.104 × 15 = **1.56 V**
  - Percentage drop ≈ **0.6%** → **excellent**

### String Fuse
- **15–20 A** fuse recommended

---

# Battery Bank and Protection

- 4 × LiFePO₄ batteries
- 48 V configuration
- Battery discharge limit: **100 A**
- Inverter allows configuring max charge/discharge current
- Battery cables: **3 AWG** (short run, 20–30 cm)
- Battery fuse: **150 A MEGA**

---

# Battery Balancing

With 4 batteries in series, balancing is essential.

A detailed study of balancing methods concluded:

### **Chosen solution: HC02 Active Capacitive Balancer (24 €)**
- Active “charge pump” system
- Uses capacitors
- Cheap, robust, reliable
- Slow but effective
- Better than passive resistive balancers
- Simpler and cheaper than inductive DC-DC balancers

This ensures all batteries remain equalized over time.

---

# AC and Grid Cabling

For 6 kW at 230 V:

- Current ≈ **26 A**
- Distance: 25 m
- Recommended cable: **3G6 mm²**
- Supports 40 A
- Voltage drop ≈ **1.7%**
- Cost ≈ **150 €**

---

# Final Summary

The final system is:

- **More powerful**
- **More efficient**
- **More reliable**
- **Cheaper per watt**
- **Easier to maintain**
- **Safer**
- **Fully hybrid**

The transition from flexible panels + EDECOA to **glass panels + DEYE** represents a **major leap in quality and performance**.

This system is now capable of powering:

- Refrigeration
- Lighting
- Electronics
- Two AC units
- And general household loads

Even in a remote location with unstable grid supply.
