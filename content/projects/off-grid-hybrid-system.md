+++
title = "Off-Grid Hybrid System – Wind + Solar (Experimental and High-Power)"
date = 2026-02-01
summary = "Two-block hybrid energy solution for a remote house: an experimental wind+solar unit and a high-power 48 V hybrid solar system."
description = "Design, evolution and justification of an off-grid hybrid installation sited in a high, remote house inside a natural park. Includes an experimental wind+solar block and a scalable high-power solar hybrid block with wiring, protection and battery architecture."
tags = ["Hybrid Energy", "Wind", "Solar", "LiFePO4", "MPPT", "Off-Grid", "System Design"]
type = "projects"
+++

# Off-Grid Hybrid System — Wind + Solar (Experimental and High-Power)

A remote house located at a high point inside a natural park suffers from **unstable grid supply** and frequent maintenance outages. The system objective is twofold: guarantee **continuous basic lighting and essential services** at any hour, and **secure constant loads** (for example, a refrigerator) against grid interruptions. The solution is split into two coordinated blocks:

- **Block 1 — Experimental low-power wind + solar**: validate wind generation potential and controller behaviour.
- **Block 2 — High-power hybrid solar**: robust, scalable system to supply major loads and support air conditioning and heavy appliances.

Both blocks follow the same operational philosophy: staged upgrades, controller intelligence, correct protection and a strong emphasis on battery health and safety.

---

## Site context and design drivers

The house sits on a high ridge with sea exposure. Grid power arrives but is **unstable** and subject to scheduled cuts. Park regulations and the remote location impose constraints on heavy civil works and turbine siting. Design drivers:

- **Continuity** — lighting and essential services must remain available at all times.
- **Reliability** — refrigerator and other constant loads must be protected from deep discharge and grid interruptions.
- **Scalability** — start with low-cost experiments, then scale to a production-grade hybrid system.
- **Safety** — MPPT controllers, BMS, correct fusing and earthing are mandatory.

---

## Block 1 — Experimental Wind + Solar (low power)

### Purpose

Create a low-cost experimental setup to measure real wind energy potential, test a certified MPPT wind controller with a dump (dumb) load, and observe interactions with aged solar panels and a reused LiFePO₄ battery. The block powers **12–14 V LED lighting** and provides operational data to inform larger investments.

### Components and topology

- **Wind turbine** — low-cost model rated 800 W (supplier claim).
- **Hybrid MPPT wind/solar controller** — certified MPPT with electronic protections and a **dumb-load** output to safely dissipate excess energy when batteries are full. Controller supports up to **1000 W solar** input.
- **Reused flexible solar panels** — limited to ~100 W effective per panel due to age.
- **Reused LiFePO₄ battery** — degraded capacity; used to isolate wind contribution.
- **12–14 V LED lighting** as primary load.
- **Monitoring** — voltage, current and state-of-charge logging recommended.

### Expected behaviour and justification

- **Wind at night, solar by day**: elevated site with sea exposure typically yields more wind at night; combining both sources increases overall availability.
- **Realistic output**: despite an 800 W rating, measured wind power is expected to average **tens of watts** (practical ~50 W) at this site; the experiment quantifies actual yield.
- **Why MPPT + dump load**: diode-rectifier controllers lack active protection and can allow turbine overspeed or battery overcharge. An MPPT with dump load protects turbine and battery and enables controlled operation under high wind and full battery conditions.

### Limitations and safety

- Reused panels and battery intentionally limit contribution so wind performance can be isolated.
- Dump load must be sized to absorb peak turbine power safely.
- Implement basic surge protection and earthing due to exposed location.

---

## Block 2 — High-Power Hybrid Solar (production system)

Block 2 is the production-grade system designed to supply major household loads. The design evolved from a 12 V prototype to a 24 V intermediate and finally to a 48 V architecture to meet multi-kW demands efficiently.

---

### 2.1 Stage A — 24 V intermediate design (lessons from 12 V)

**Problem with 12 V:** high DC currents (~70 A) required heavy, expensive cabling and large voltage drops. Moving to 24 V reduces current for the same power and lowers conductor costs.

**PV array and electrical layout (24 V stage)**

- **PV modules:** 16 × 100 W flexible panels arranged **4S4P** (4 in series × 4 parallel strings).
  - Array nominal: **Vmax ≈ 100.28 V**, **Imax ≈ 29.15 A**.
  - Each string delivers up to **~6 A** under typical conditions.
- **Cabling & protection:**
  - **12 AWG** for string runs (rated ~55 A).
  - **10 A fuse** on each positive string.
  - **4-pole switch** (40 A / 690 V) for series positives.
  - Strings combined on a **terminal block** rated 80 A / 690 V, consolidated to **10 AWG** main feed (~70 A).
- **MPPT:** Victron Energy 150/60. MPPT output uses **6 AWG** cable (~132 A) with **MEGA fuse 80 A**.
- **Battery bank:** 2 × LiFePO₄ 12 V 300 Ah in series → **24 V, 300 Ah**. Battery-to-inverter feed uses **2 AWG** (~218 A) with **MEGA fuse 200 A**.
- **Inverter:** EDECOA pure sine 3500 W (nominal ~145 A at 24 V; possible short peaks up to 300 A).

**Tradeoffs**

- 24 V reduces currents vs 12 V but still requires heavy cabling for multi-kW loads. Proper fusing and conductor sizing are essential to avoid overheating and voltage drop.

---

### 2.2 Stage B — 48 V conversion and high-power hybrid

**Trigger:** demand increased to run two AC units (≈3000 and ≈5000 frigorías). Battery continuous discharge limits at lower voltages made 48 V necessary. Using \(P = V \cdot I\), higher voltage reduces current for the same power and enables reliable multi-kW delivery.

**New architecture (48 V final stage)**

- **PV modules:** 6 × JA Solar 600 W N-type bifacial (JAM72D40-MB) arranged **3S2P**.
  - Per module: \(V_{mp} \approx 52.79\) V, \(I_{sc} \approx 14.04\) A.
  - Array worst-case: ~6392 W (3S2P → ~35.1 A at ~182 V).
- **Hybrid inverter:** EDECOA EG-624B (selected for hybrid operation and automatic transfer between grid and solar).
- **Battery bank:** 4 × LiFePO₄ 400 Ah configured to achieve **48 V** (arrangement to meet capacity and discharge requirements).
- **Protection & cabling:**
  - **15 A fuse** per PV string.
  - 4-pole 40 A / 690 V switch for series switching.
  - Inverter input fuse sized with safety multipliers (example: battery fuse ≈ \(I_{max} \cdot 1.25\)).
  - DC cabling sized to 48 V operation to reduce current and losses.

**Why 48 V**

- Reduces DC current for the same power, lowering conductor cross-section and I²R losses.
- Enables continuous multi-kW delivery without exceeding battery or conductor limits.
- Hybrid inverter supports automatic transfer and grid interaction.

---

## Wiring, fusing and protection strategy (concise rules)

- **String fuses** protect PV strings from reverse currents and short circuits. Size fuses to protect conductors, not to limit normal current.
- **MPPT output fuse** protects MPPT-to-battery cabling. Use MEGA fuses for high-current DC runs.
- **Battery fuses** protect against short circuits; BMS manages normal current limits and cell safety.
- **Switches and terminal blocks** must be rated above expected peak currents and system voltage (e.g., 690 V rating for PV-side switches).
- **Earthing and surge protection** are mandatory in exposed elevated sites.
- **Relay control**: use MPPT relay outputs to control inverter ON/OFF to prevent deep discharge (as implemented previously).

---

## Battery, BMS and operational safety

- **BMS** is mandatory for LiFePO₄ packs: cell balancing, over/under voltage protection, temperature monitoring and overcurrent protection.
- **Deep-discharge prevention**: configure inverter and MPPT relays to disconnect heavy loads when SOC is low.
- **Thermal management**: batteries and inverters must be installed in ventilated, weather-protected enclosures.
- **Monitoring**: log voltage, current, SOC and wind speed to validate performance and detect faults early.

---

## Estimated costs (presented and justified)

| Item | Notes | Estimated cost |
|------|-------|----------------|
| Small wind turbine + MPPT | Low-cost turbine + certified MPPT with dump load | 200–600€ |
| Flexible 100 W panels (reused) | Reused from previous project | 0–200€ |
| Victron MPPT 150/60 | Mid-stage MPPT | 300–600€ |
| EDECOA 3500 W inverter | 24 V pure sine inverter | 300–700€ |
| EDECOA EG-624B hybrid | 48 V hybrid inverter | 1,000–2,000€ |
| LiFePO₄ batteries | 4 × 400 Ah (48 V bank) | 3,000–6,000€ |
| High-power PV (6 × 600 W) | JA Solar N-type bifacial | 2,000–3,500€ |
| Cabling & protection | Heavy gauge DC cabling, fuses, terminal blocks | 300–800€ |
| Mounting & installation | Frames, turbine mount, labor | 300–1,000€ |

**Total rough estimate (final 48 V system):** **≈ 7,000–14,000€** depending on component choices and labor.

---

## Evolution timeline (concise)

- **2019** — Prototype: 2×100 W panels, PWM controller, car battery and inverter (basic loads).
- **2021** — MPPT upgrade, LiFePO₄ 100 Ah, additional panels (improved efficiency, medium loads).
- **2023** — Expansion to 8 panels, Victron MPPT and 2 kW inverter (able to run portable AC during sun).
- **2025** — Battery degradation revealed limits after sunset; system became battery-limited.
- **2026** — Control modification: MPPT relay to inverter ON/OFF; decision to redesign to 48 V and larger panels/inverter for multi-kW loads.

---

## Key lessons and design justification

- **Staged approach** reduces risk and cost while providing real operational data.
- **Controller intelligence** (MPPT + relay + dump load) is essential for turbine safety and battery protection.
- **Voltage scaling** (12 → 24 → 48 V) is the primary lever to reduce DC currents and cable costs for multi-kW systems.
- **Battery health** is often the system bottleneck; BMS and correct charge/discharge logic are critical.
- **Realistic expectations**: low-cost turbines and reused panels rarely meet nameplate ratings; measure actual yield before scaling.

---

## Practical deliverables and next steps

- **Single-line diagram** showing PV strings, turbine, MPPTs, battery bank, inverter and critical loads (placeholder below).
- **Bill of Materials (BOM)** with exact cable lengths, fuse types and ratings.
- **Monitoring plan**: voltage/current logging, wind speed, SOC history for at least one seasonal cycle.
- **Regulatory check**: confirm park rules for turbine installation and electrical work permits.

---

### Single-line diagram (placeholder)
