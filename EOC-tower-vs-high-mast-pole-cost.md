# EOC structure cost comparison: antenna tower vs high-mast lighting pole

**Site:** Houston County Emergency Operations Center  
102 Chief Williams Drive, Kathleen, GA 31047 (Fire & Emergency Management Complex)

**Purpose:** Compare installed cost of a new **80 ft AGL** support for two 5.8 GHz AREDN dish antennas (primary to Houston Medical / Warner Robins at 027.5° true, primary to Emory Hospital Perry at 195.3° true).

**Date:** November 2026  
**Prices:** US street / kit / typical municipal bid ranges. Confirm with a PE-stamped quote before purchase order.

---

## Recommendation

If the pole is **new** (not already on site), buy a **communications tilt-over or light lattice**, not a high-mast lighting pole.

A lighting pole **without luminaires and without a raising/lowering mechanism** is usually **as expensive or more expensive** to install than an antenna tower, and it is worse for 5.8 GHz work: it cannot be climbed, cannot be tilted, and is not designed for two 30 dBi dishes.

---

## What is being compared

| Option | What it is | What is excluded |
|---|---|---|
| **A — Antenna tower (preferred)** | 80 ft AGL communications tilt-over or hinged aluminum lattice, sized for antennas | Radios, dishes, Cat6, UPS (already in the RF BOM) |
| **B — High-mast lighting pole** | New 80–100 ft galvanized tapered lighting shaft, **fixed** (no lights, no winch, no luminaire ring) | Same RF gear excluded |

Both options need: PE calculations, foundation, grounding, FAA Form 7460-1 (Robins AFB), Houston County permit, and a mount for two Ubiquiti RD-5G30-LW dishes with Rocket 5AC Lite radios at **80 ft AGL antenna centerline**.

The EOC is an **essential facility**. Size steel and foundation for ASCE 7 Risk Category III (or IV if the county requires it), not a parking-lot lighting catalog rating.

---

## Installed cost summary

| Cost item | A — Antenna tilt-over / light lattice | B — High-mast lighting pole (no lights, no winch) |
|---|---|---|
| Structure | $6,000–$15,000 | $8,000–$16,000 |
| Foundation | $2,000–$5,000 | $6,000–$12,000 |
| Set / crane | $0–$2,500 | $2,500–$6,000 |
| Dish arm / mounts | $400–$1,000 | $800–$2,000 |
| PE stamp + FAA 7460-1 | $1,500–$3,000 | $1,500–$3,000 |
| **Installed total** | **~$12,000–$26,000** | **~$19,000–$39,000** |
| Each later alignment | Tilt down; work on the ground | Bucket truck **$800–$1,500** |

**Typical midpoint for budgeting**

- Antenna tower: **~$18,000** installed  
- Lighting pole (bare): **~$28,000** installed  

---

## Structure examples (hardware only)

### Antenna tower

| Example | Notes | Approx. hardware |
|---|---|---|
| Universal Towers HD 80 ft kit | Freestanding aluminum, hinged base; models HD 8-80 through HD 16-80 | $4,800–$5,800 (3Star Inc., 2026 list) |
| Universal Towers HD 90–100 ft kit | If dish centerline must stay 80 ft with arm below the cap | $5,700–$6,700 |
| Aluma T-75HN | Nested tilt-over, ~71 ft with mast, 18 sq ft / 70 mph class | ~$13,000 new (Sep 2025 classified reference) |
| Aluma T-100HN | Nested tilt-over, ~92 ft with mast; use if 80 ft centerline is required | Quote; expect **higher** than T-75HN |
| Aluma T-75XHD / T-100 class | Prefer XHD if PE requires more than 70 mph / 18 sq ft | Quote |

Two RD-5G30-LW dishes plus radomes and radios are on the order of **8–12 sq ft** wind area. Have the manufacturer or PE confirm the model; do not assume a 70 mph amateur “HN” kit is enough for an EOC.

### High-mast lighting pole (stripped)

| Example | Notes | Approx. hardware |
|---|---|---|
| US municipal 80–100 ft tapered galvanized shaft (Valmont / equivalent) | Fixed top, no ring, no fixtures | $8,000–$16,000 delivered |
| Import “pole only” listings | Often $1,500–$3,500 FOB overseas | **Do not use** for an EOC; no US wind/ice PE trail |

Stripping lights and the winch saves roughly **$3,000–$8,000** (ring/winch) plus fixture cost. It does **not** remove the heavy shaft, caisson, or crane.

---

## Why the lighting pole is not the cheap option

1. **The expensive work stays.** Foundation + crane + thick tapered steel dominate the bill. Lights and the lowering ring are the parts you would delete, and they are not most of the installed cost.
2. **EOC wind rating.** A lighting catalog pole is often Risk Category II. An EOC comms structure is typically **III**. The PE will upsize the shaft and foundation, which erases leftover savings.
3. **Wrong top.** A lighting tenon is useless for two RocketDish mounts. You still buy a custom cross-arm.
4. **Cannot climb, cannot tilt.** Standard high-mast lighting poles are smooth tapered shafts. Service is a bucket truck, not rungs or a tilt-over.
5. **5.8 GHz needs access.** Dish alignment is iterative. A few lift visits cost more than the difference between the two structures.

---

## Lifetime / operations

| | Antenna tilt-over | Lighting pole (fixed) |
|---|---|---|
| Climbable | Not required; tilts to the ground | Generally **no** |
| Align 5.8 GHz dishes | On the ground | Bucket truck |
| Cost per alignment | ~$0 extra (ARES / county staff) | $800–$1,500 |
| Three alignments over the first year | ~$0 | ~$2,400–$4,500 |

---

## What not to buy

- **30–40 ft parking-lot** shoe-box poles — too short (need **80 ft AGL dish centerline**).
- A lighting pole **with** luminaires and a lowering ring “in case we want lights later” — adds cost and occupies the top where the dishes must sit.
- Import high-mast poles without a US PE package.
- Assuming an 80 ft lighting pole gives 80 ft of RF height. Lights or a cap eat the top; dishes on a standoff below that often land at **65–70 ft**. For 80 ft centerline, the shaft must be **taller than 80 ft** or the dishes must be at the very top.

---

## Procurement spec (preferred)

Specify a **communications tilt-over** (or hinged lattice) as follows:

- **80 ft AGL antenna centerline** for both dishes (not pole length with antennas lower)
- Cross-arm for two **RD-5G30-LW** dishes, facing **027.5° true NNE** (Houston Medical) and **195.3° true SSW** (Perry)
- Tilt-over or hinged base so alignment is done on the ground
- PE-stamped foundation and wind/ice for Houston County, essential-facility risk category
- Internal or clipped outdoor Cat6 STP, ground kit to the building electrode
- FAA Form 7460-1 before construction

If county standards require a **steel monopole** appearance, specify a **communications monopole** with step bolts or a tilt base — not a lighting catalog number.

---

## Sources

- Universal Towers HD kit list prices: 3Star Inc. (`3starinc.com`), 2026
- Aluma T-75HN / T-100HN: Jo Gunn / Aluma (quote; T-75HN new ~$13k cited Sep 2025)
- High-mast pole-only vs installed system ranges: industry lighting-pole guides (fixed shaft vs raising-lowering); US municipal tapered-steel practice
- Monopole foundation / crane order-of-magnitude: typical 80–100 ft tubular install ranges
- Dish height and bearings: Houston County AREDN 5.8 GHz backbone design (EOC 32.52204°N, 83.68923°W)

Radios, dishes, PoE, switch, and UPS are **not** in this comparison; they are in `Houston-County-AREDN-BOM.csv`.
