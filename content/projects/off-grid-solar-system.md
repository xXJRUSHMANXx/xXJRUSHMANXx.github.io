+++
title = "Grid-Off Solar System – Low-Cost Apartment Installation"
date = 2024-01-28
summary = "A progressive low-cost solar system built in stages using flexible panels, MPPT controllers and LiFePO4 storage."
description = "A complete off-grid solar installation for an apartment balcony, built with low-cost components from AliExpress and progressively upgraded over several years."
tags = ["Solar Energy", "Off-Grid", "MPPT", "LiFePO4", "DIY", "Energy Systems"]
type = "projects"
+++


This project is a **low-cost off-grid solar system** installed on the balcony of an apartment, built progressively over several years using affordable components from AliExpress. The system evolved through multiple stages, improving efficiency, safety and power output until reaching a configuration capable of running medium-power appliances such as a portable air conditioner and an electric cooker.

The installation uses **flexible 100W monocrystalline solar panels**, mounted on the balcony using a **braided steel cable** and a **PVC frame** that holds two panels together. The top side is suspended from the cable, while the bottom side is supported by a **prismatic bar** that allows angle adjustment.

---

## Stage 0 — First Prototype (2019)

The project began in 2019 with a very basic and extremely low-cost setup:

- **2× 100W flexible solar panels** — *150€*
- **Basic PWM charge controller** (the typical small blue model included for free with panels)
- **Car lead-acid battery** stored inside a wheeled plastic container
- **1500W car inverter** — *30€*
- **Parallel wiring** using a Y-type 1–2 connector — *7.52€*

**Usage:**
Only light loads such as a small fan and low-power devices.

**Cost of Stage 0:** ~**187.52€**

---

## Stage 1 — First Major Upgrade (22 June 2021)

To increase power production and improve efficiency, the system was expanded:

- **2 additional 100W panels** — *150€*
- **60A MPPT charge controller** — *60€*
  Much higher efficiency and safer operation than the PWM controller.
- **25A fuse** (later found to be undersized for real current)
- **100Ah LiFePO₄ battery** — *200€*
- **Y-type 4–1 connector** — *11.96€*
- **10m of 10AWG cable** — *53.25€*
- **Solar connectors** — *4.18€*

This configuration allowed powering **medium loads**, but still not enough for the main goal:
running a **portable AC** or **electric heater**.

**Cost of Stage 1:** ~**479.39€**
**Total so far:** ~**666.91€**

---

## Stage 2 — High-Power Expansion (4 July 2023)

To reach higher power output, the system was expanded again:

- **4 additional 100W panels** — *287.33€*
  Total panels: **8×100W**
- Configuration changed to **4S2P**
- **Victron Energy 150/60 MPPT controller**
- **EDECOA 2kW pure sine wave inverter**

With this setup, the system was finally able to power:

- A **portable AC unit** (EcoFlow Wave 3 — 1537 Frigorías)
- An **electric cooking pot**
- Other medium-power appliances during peak sunlight

**Cost of Stage 2:** ~**287.33€** (panels only; inverter + Victron not included in original prices)
**Estimated total including inverter + MPPT:** ~**1,200–1,300€**

---

## Stage 3 — Battery Failure & System Optimization (2025–2026)

In 2025, the LiFePO₄ battery began to fail:

- It no longer provided energy after sunset.
- Even during the day, performance dropped significantly.
- The portable AC worked for one year, then the system could not even power the TV in the evening.

### Root cause (2026 analysis)

The inverter was discharging the battery down to **10.3V**, a value that **damages lithium batteries**.
This cutoff voltage **could not be configured** because it was hardcoded inside the EDECOA inverter.

### Solution

A custom control system was implemented:

- The **relay output of the MPPT controller** was wired to the **ON/OFF switch of the inverter**.
- The relay now controls when the inverter turns on or off.
- This allowed setting:
  - **Minimum voltage to shut down**
  - **Minimum voltage to restart**

### Result

Two critical bottlenecks were solved:

1. **Battery replaced**
2. **Inverter now controlled safely by the MPPT relay**

The system went from being **battery-limited** to being **panel-limited**, which is expected after years of use.

---

## Final Cost Summary

| Stage | Description | Cost |
|------|-------------|------|
| Stage 0 | Initial prototype | ~187.52€ |
| Stage 1 | MPPT + LiFePO₄ + wiring | ~479.39€ |
| Stage 2 | Additional panels + high-end inverter + Victron | ~550–650€ (estimated) |
| Stage 3 | Battery replacement + control optimization | ~200–300€ (estimated) |

### **Total estimated cost of the full system:**
# **≈ 1,400–1,600€**

---

## Conclusion

This project demonstrates how a **low-cost off-grid solar system** can evolve over time through experimentation, upgrades and problem-solving. Starting from a simple PWM setup with a car battery, it grew into a **high-power balcony installation** capable of running demanding appliances such as a portable AC unit.

The system is the result of:

- continuous learning
- practical engineering
- creative solutions
- and a strong focus on efficiency and safety

It stands as a complete example of **DIY renewable energy engineering** in an apartment environment.