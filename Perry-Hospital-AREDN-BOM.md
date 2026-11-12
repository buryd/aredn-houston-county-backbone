# Emory Hospital Perry — AREDN site BOM and installed cost

**Site:** Emory Hospital Perry (Houston Healthcare Perry), 1120 Morningside Drive, Perry, GA 31069  
**Mount:** Highest roof, north-northeast corner; 15–20 ft above parapet; target **50–70 ft AGL** dish centerline  
**Links:** PH-5G-EOC at **015.3° true** (primary to EOC); PH-5G-HMC at **022.9° true** (rollover to Warner Robins)  
**Keep off:** Helipad 4GE7 / Air Evac, Morningside Drive front, ER canopy  
**Date:** November 2026  
**Prices:** Same street prices as `Houston-County-AREDN-BOM.csv`. Confirm before PO. International (non-US-lock) radios only.

This is **Perry only**. It does not include the EOC 80 ft mast, Warner Robins roof, or network-wide spares kept at the EOC.

---

## Installed cost summary

| Bucket | Amount |
|---|---|
| Hardware | **$2,219** |
| Estimated GA tax + freight (8%) | **$178** |
| Licensed roof/rigger (this site) | **$2,800** |
| Electrician — grounding and bonding | **$650** |
| Path walk + dish alignment (this site) | **$400** |
| Contingency 15% | **$937** |
| **Turnkey, Perry site** | **~$7,184** |

**Budget as ~$7,200.** Facilities escort, membrane PE letter, or FAA 7460-1 consultant are extra (see optional).

---

## Bill of materials (this site)

| Category | Item | SKU | Qty | Unit | Ext | Source |
|---|---|---|---:|---:|---:|---|
| RF radios | Ubiquiti Rocket 5AC Lite, International (not -US) | R5AC-LITE | 2 | $135 | $270 | Streakwave / WISP |
| Antennas | Ubiquiti RocketDish 30 dBi lightweight | RD-5G30-LW | 2 | $109 | $218 | Streakwave |
| Antennas | IsoBeam 620 radome | ISO-BEAM-620 | 2 | $69 | $138 | Streakwave |
| Indoor node | MikroTik hAP ac3, International | RBD53iG-5HacD2HnD | 1 | $99 | $99 | MikroTik / Multi-Link |
| Switching | Netgear 8-port Gigabit Smart switch | GS108Tv3 | 1 | $84 | $84 | Micro Center / CDW |
| Protection | Gigabit Ethernet surge protector | ETH-SP-G2 | 4 | $16 | $64 | B&H / Streakwave |
| Power | Spare 24 V gigabit passive PoE injector | POE-24-12W-G | 2 | $18 | $36 | Streakwave |
| Cabling | Outdoor shielded Cat6, 500 ft | Cat6-STP-OUT-500 | 1 | $100 | $100 | TrueCable / Amazon |
| Cabling | Indoor Cat6 patch / run kit | Cat6-IN | 1 | $18 | $18 | Amazon / Graybar |
| Cabling | Shielded RJ45 plugs, boots | RJ45-STP | 1 | $25 | $25 | TrueCable |
| Power | APC Back-UPS Pro 1500 VA sine-wave | BR1500MS | 1 | $280 | $280 | Amazon / CDW |
| Power | Rack/shelf PDU or heavy strip | PDU-6 | 1 | $25 | $25 | Amazon |
| Grounding | 8 ft copper-clad ground rod | ROD-8 | 2 | $28 | $56 | Home Depot / Graybar |
| Grounding | #6 AWG bare copper, 50 ft | AWG6-50 | 1 | $50 | $50 | Graybar / Home Depot |
| Grounding | Ground bar, acorn clamps, lugs | GND-HW | 1 | $45 | $45 | DX Engineering / Graybar |
| Mounting | Hospital roof mast / wall-arm kit, 15–20 ft | ROOF-MAST-20 | 1 | $425 | $425 | Ventev / Tessco / Talley |
| Mounting | NEMA outdoor junction boxes | NEMA-4X | 2 | $28 | $56 | Grainger |
| Mounting | Cable entry / weatherhead kit | ENTRY-KIT | 1 | $45 | $45 | Grainger / Tessco |
| Mounting | Stainless hardware, hose clamps, UV ties, butyl | HW-KIT | 1 | $40 | $40 | Home Depot / Tessco |
| Services host | Raspberry Pi 5 8 GB + case + SD | RPi5-8 | 1 | $95 | $95 | Adafruit / Amazon |
| Consumables | Labels, dielectric grease, tape | CONSUMABLE | 1 | $50 | $50 | Amazon / Graybar |
| | **Hardware subtotal** | | | | **$2,219** | |

Radios ship with 24 V **passive** PoE injectors. The two extra injectors are spares. Do **not** power from hospital 802.3af wall jacks.

---

## Labor (this site)

| Work | Amount | Notes |
|---|---:|---|
| Licensed roof/rigger | $2,800 | Fall protection, hospital escort, ballast or wall-arm, dish aim |
| Electrician — grounding | $650 | Bond mast, dishes, ETH-SP to building electrode |
| Alignment / path check | $400 | 015.3° to EOC and 022.9° to Warner Robins |

---

## Optional (not in the $7,184)

| Item | Est. | When |
|---|---:|---|
| Spare Rocket 5AC Lite, International | $135 | Keep on site if EOC spare is not shared |
| 2.4 GHz local omni (portable node access) | $90 | Indoor/outdoor AREDN AP, not the backbone |
| Facilities after-hours escort | $400–$800 | Typical hospital roof rule |
| PE letter for roof membrane / ballast | $500–$1,500 | If facilities require a stamp |
| FAA 7460-1 filing (consultant) | $0–$300 | Required near 4GE7 / Robins AFB; county can file |

---

## What is on the roof vs in the closet

**Roof (NNE corner):** two Rocket + dish + radome, 15–20 ft mast or wall arms, two ETH-SP at the masts, two Cat6 drops, #6 bond to roof steel.

**Engineering / IT closet:** two passive 24 V injectors, GS108Tv3 (VLAN 2), hAP ac3, Pi, UPS. Cat6 is the only run off the roof.

---

## Notes

- Same RF package as Warner Robins, but **no 80 ft tower**. Perry is a 2–3 story hospital; an EOC-style mast fights helipad 4GE7.
- File FAA 7460-1 and get Air Evac / facilities sign-off before ballast.
- Network-wide cold spares (extra Rocket, extra hAP) stay at the EOC and are in the county BOM, not duplicated here.
