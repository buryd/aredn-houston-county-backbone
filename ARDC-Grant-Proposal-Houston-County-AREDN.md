# ARDC Grant Proposal

**Project title:** Houston County 5.8 GHz AREDN Hospital–EOC Backbone  
**Applicant (proposed):** Houston County Emergency Management Agency (local government), in partnership with Houston County ARES / amateur radio volunteers  
**Fiscal / legal status:** U.S. local government agency (ARDC-eligible). If the applicant of record is an amateur radio club that is not a 501(c)(3), Houston County EMA will serve as fiscal sponsor.  
**Location:** Houston County, Georgia (Warner Robins, Kathleen, Perry)  
**Request:** **$24,648**  
**Duration:** 12 months from award  
**Primary ARDC goals:** Doing (deploy a working Part 97 mesh); Learning (training and licensing); Experimenting (5.8 GHz PtP on amateur-exclusive channels)  
**Open access:** Design, BOM, diagrams, and after-action documentation released under **CC BY-SA 4.0**. Network runs **AREDN** open-source firmware. Public repository: https://github.com/buryd/aredn-houston-county-backbone  

*Submit via https://grants.ardc.net. Attach this narrative as PDF plus letters of support. Placeholders in [brackets] must be completed before filing.*

---

## 1. Summary

This project will build a three-site **Amateur Radio Emergency Data Network (AREDN)** backbone on the **5.8 GHz amateur band** linking:

1. **Houston County EOC** — 102 Chief Williams Drive, Kathleen, GA 31047 (Fire & Emergency Management Complex)  
2. **Emory Hospital Warner Robins** (Houston Medical Center) — 1601 Watson Boulevard, Warner Robins, GA 31093  
3. **Emory Hospital Perry** — 1120 Morningside Drive, Perry, GA 31069  

The network is a **triangle of dedicated 5.8 GHz point-to-point links** so that any one path can fail without isolating a hospital from the EOC. It will carry MeshChat, voice, and file/video traffic **independent of commercial cellular, internet, and hospital WAN**. It is an amateur radio overlay under FCC Part 97, not a clinical or 911 CAD network.

Amateur operators will **use and maintain it year-round** (weekly check-ins, quarterly full-mesh drills, public Field Day / EMA open-house demos), not only during disasters. All engineering documents will remain public so other counties can copy the model.

**Amount requested from ARDC: $24,648** (hardware, tax/freight, licensed hospital-roof and EOC-mast installation, grounding, 15% contingency). Houston County and hospital facilities contribute roof/mast access, escort, and in-kind labor. ARES volunteers contribute path survey, firmware, configuration, training, and ongoing operations.

---

## 2. Need

Houston County, Georgia, has more than **170,000 residents**, Robins Air Force Base, and two acute-care hospitals about **12 miles** apart. The county EOC relocated to a **one-story hardened EMA building** in Kathleen, geographically between the hospitals but with **no existing amateur 5 GHz backbone** to either campus.

When commercial networks fail (ice, tornado, hurricane remnants, cyber outage, or mass-casualty surge), EMA, hospital command, and ARES currently fall back to voice radio and courier. They lack a **licensed, off-grid IP path** for:

- Hospital–EOC coordination (bed status, logistics, situational files)  
- Voice when VoIP/PSTN is down  
- Training new hams on modern Part 97 data modes  

5.8 GHz amateur spectrum (including Part 97-exclusive channels above most Part 15 Wi-Fi) is unused here for infrastructure. This project puts that spectrum to **regular work** and gives the public a visible, documented amateur mesh they can join after licensing.

---

## 3. Alignment with ARDC goals

**Doing.** Deploy a production Part 97 mesh that served agencies will actually use, with published node names, channels, and runbooks.

**Learning.** Technician-and-up classes, AREDN workshops, and quarterly drills at the EOC radio room. High-school / Scout / public demos at EMA open house and Field Day. Documentation is written so a new Extra or a neighboring county ARES group can reproduce the build.

**Experimenting.** Dual-polarity 802.11ac dishes on amateur-exclusive 10 MHz channels (169 / 177 / 184), Device-to-Device Ethernet linking, and measured path budgets on 4.5–11.8 mile links over coastal-plain timber.

**Open access.** AREDN firmware is open source. This project’s design, BOM, path math, and diagrams are already public (CC BY-SA). Grant-funded photos, configs (with no private credentials), and after-action reports will be added to the same repository.

**Geographic / impact.** Middle Georgia is not a dense ARDC-grant region. The mesh serves two hospitals and a county EOC that support the whole county, including lower-income tracts in Warner Robins and Perry.

---

## 4. Technical design

### 4.1 Sites and paths (true bearings)

| Link | Path | Distance | Azimuths | Channel (plan) | Role |
|---|---|---|---|---|---|
| A | EOC → Warner Robins | 7.37 mi / 11.86 km | 027.5° / 207.5° | Ch 177, 5885 MHz, 10 MHz | Primary north spoke |
| B | EOC → Perry | 4.52 mi / 7.27 km | 195.3° / 015.3° | Ch 169, 5845 MHz, 10 MHz | Primary south spoke |
| C | Warner Robins → Perry | 11.83 mi / 19.03 km | 202.9° / 022.9° | Ch 184, 5920 MHz, 10 MHz | Mesh closer / failover |

Ground elevations (USGS EPQS): EOC 369 ft, Houston Medical 431 ft, Perry 362 ft MSL. Free-space receive with 30 dBi dishes is about **−38 to −46 dBm**. Trees, not watts, set mast height.

### 4.2 Radio and mounting

- **Six** Ubiquiti Rocket 5AC Lite **International** (not US-locked) on **RD-5G30-LW** 30 dBi dishes with radomes. AREDN-stable, 128 MB.  
- **Three** MikroTik hAP ac3 International indoor nodes; VLAN 2 Device-to-Device through a small managed switch at each site.  
- **24 V passive PoE** (not hospital 802.3af). Outdoor shielded Cat6, surge at mast and entry, UPS at each radio closet.  
- **EOC:** new **80 ft AGL tilt-over communications mast** (not a lighting pole). Dishes at the top, facing opposite bearings. One-story EMA building cannot roof-mount.  
- **Warner Robins:** two dishes on the **Northwest Tower roof**, south-southwest corner, 10–15 ft above parapet; **not** helipad 2GA3 / Main Tower.  
- **Perry:** two dishes on the **highest roof, NNE corner**, 15–20 ft above parapet (50–70 ft AGL); **not** helipad 4GE7 / Air Evac / Morningside front.

Firmware: current production AREDN. SSID/channel plan and node names are in the public design (e.g. `HCEMA-EOC-5G-HMC`, `PH-5G-EOC`).

### 4.3 What this network will not do

It will **not** bridge to hospital EHR, HIPAA clinical VLANs, or Houston County 911 CAD. Mesh LAN drops are labeled **AREDN only**. Any future tunnel would require hospital CISO review and is out of scope.

### 4.4 Why this equipment (not cheaper CPEs)

ARDC asks that budgets not underspecify hardware that will fail. 10–12 mile 5.8 GHz paths over pine need **~30 dBi** and International SKUs for 5.85–5.925 GHz. LiteBeam-class 16–23 dBi CPEs would be a false economy. A lighting pole was compared for the EOC and **rejected**: similar or higher installed cost, cannot tilt, not sized for two dishes (see public cost comparison in the repository).

---

## 5. Work plan and schedule (12 months)

| Months | Work | Who |
|---|---|---|
| 1–2 | MOUs: EMA, both hospital facilities, ARES trustee. Confirm roof corners and EOC mast pad. Start FAA 7460-1. | EMA director, hospital facilities, ARES EC |
| 1–2 | Desktop + field path check (Radio Mobile / CloudRF + binocular/drone on published azimuths). Go/no-go on Link C. | ARES |
| 2–3 | Purchase International radios, dishes, indoor nodes, UPS, cable. Order 80 ft tilt-over with PE foundation drawing. | County purchasing / grant PI |
| 3–4 | Bench-flash AREDN, name nodes, 10 MHz channels, DtD VLANs, parking-lot iperf. | ARES volunteers |
| 4–6 | Pour EOC mast foundation; install tilt-over; mount both EOC dishes. | Licensed installer + ARES |
| 6–8 | Warner Robins Northwest Tower roof (helipad-clear). Then Perry NNE roof. | Licensed rigger + ARES; hospital escort |
| 8–9 | Align Links A and B to ≤ −55 dBm / > 40 Mbps TCP. Attempt Link C; if blocked, operate hub-and-spoke and document. | ARES |
| 9–10 | Services: MeshChat, analog ATA or softphone, file drop. Laminated runbook in each radio room. | ARES + EMA comms |
| 10–12 | Four weekly check-ins, one full county drill, Field Day or EMA open-house demo, Technician class, publish configs and photos. Final report to ARDC. | All |

**Success metrics**

- Links A and B: RSSI **−55 dBm or stronger**, TCP **> 40 Mbps** at 10 MHz  
- EOC can chat and voice **both hospitals with WAN unplugged**  
- UPS runtime **≥ 4 hours** radios-only  
- At least **12** licensed amateurs checked into the mesh during the grant year  
- Public repo updated with as-built photos and a CC BY-SA after-action  

---

## 6. People and time

| Role | Name / call (fill in) | Expertise | Estimated time |
|---|---|---|---|
| Principal investigator / county lead | [Name], Houston County EMA | EOC operations, procurement, MOUs | 4 hr/week × 12 months |
| ARES Emergency Coordinator | [Name, call] | Emcomm, volunteers, drills | 6 hr/week × 12 months |
| Club trustee / Part 97 control operator | [Name, call] | Station ID, club call if used | 2 hr/week |
| RF / AREDN lead | [Name, call] | Firmware, DtD, path | 8 hr/week months 1–9, then 2 hr/week |
| Hospital facilities (WR) | [Name], Emory/Houston Healthcare | Roof, helipad 2GA3, grounding | As needed, months 6–8 |
| Hospital facilities (Perry) | [Name], Emory/Houston Healthcare | Roof, helipad 4GE7, grounding | As needed, months 6–8 |
| Licensed rigger | [Contractor TBD] | OSHA fall protection, alignment | Quoted 3 site-days |
| Electrician | County or licensed contractor | NEC bond to building electrode | Quoted 3 site visits |

Volunteer ARES labor is **in-kind** (estimate 250–400 hours). Hospital-roof and EOC-mast climbing/tilt work is **paid professional** labor in the ARDC budget, per ARDC guidance to hire professionals when volunteers cannot safely do the work.

---

## 7. Outreach and regular use

ARDC funds systems amateurs will **use**, not warehouse. Plan:

1. **Weekly** mesh check-in (MeshChat + voice) from EOC and at least one hospital radio room.  
2. **Quarterly** ARES/EMA exercise: unplug WAN, pass a hospital logistics file and a voice circuit.  
3. **Field Day** and one **EMA / Fire Complex open house**: live 5.8 GHz demo, license handouts, “how a mesh node works.”  
4. **One Technician class** (or upgrade class) during the grant year, advertised through EMA, hospitals, and local clubs.  
5. **Published how-to** (GitHub + ARRL section / Georgia ARES) so other EOC–hospital pairs can copy bearings, BOM, and PoE rules.  
6. Optional: Scout / high-school STEM visit at the EOC mast (ground-level tilt-over demonstration).

---

## 8. Reach and impact

- **Direct users:** EMA staff, hospital emergency managers, and Houston County ARES (target **12–25** licensed operators on the mesh in year one).  
- **Served population:** ~170,000 county residents plus two hospital campuses if commercial networks fail.  
- **Replication:** Public BOM, path table, and mount rules for a one-story EOC + two hospital roofs — a pattern many U.S. counties can follow.  
- **Spectrum:** Regular use of amateur 5.8 GHz PtP, not only 2 m/70 cm voice.

Impact is measurable: node uptime, check-in logs, drill after-actions, class completions, and GitHub releases.

---

## 9. Sustainability (after the grant)

- Hardware is county/hospital-hosted; ARES operates under MOU and a named trustee.  
- Annual: firmware, UPS test, dish inspect, photo of SNR. After ice or tropical remnants, re-check paths.  
- Recurring cost is small (electricity, occasional PoE injector, UPS battery ~year 4). EMA will own replacement of consumables; ARES will staff operations.  
- Tilt-over at the EOC avoids bucket-truck dependency for dish work.  
- Documentation remains public even if personnel change.

ARDC is not asked to fund operations indefinitely.

---

## 10. Community support (required letters)

Before submission, attach letters from:

1. **Houston County EMA Director** — EOC mast pad, radio-room space, drills, fiscal administration.  
2. **Emory / Houston Healthcare facilities** (Warner Robins and Perry) — roof access, helipad constraints, no-bridge-to-EHR rule.  
3. **ARES / club trustee** — volunteer hours, control operator, outreach.  
4. Optional: hospital emergency manager, county fire (same complex as EOC).

In-kind (not billed to ARDC): roof/mast real estate, county electrician if assigned, volunteer labor, existing EMA internet for *non-mesh* admin only.

---

## 11. Permissions, permits, safety

| Item | Status / plan |
|---|---|
| Part 97 control operator | Named trustee before RF is on |
| International (non-US) radios | Specified in BOM; US-lock SKUs will be refused |
| EOC 80 ft mast | County permit + PE foundation; FAA 7460-1 (Robins AFB ~10 mi) |
| Warner Robins roof | Facilities + heliport manager (2GA3); 7460-1; ballast preferred over membrane penetrations |
| Perry roof | Facilities + Air Evac / 4GE7; 7460-1; short mast (no 80 ft tower) |
| Grounding | Licensed electrician; #6 to building electrode |
| Fall protection | Paid rigger on both hospital roofs; EOC work on tilt-over at ground |

Approvals are **in progress / to be obtained in months 1–2**. The proposal does not claim they are already signed.

---

## 12. Open access and licensing

| Work product | License |
|---|---|
| AREDN firmware (upstream) | Open source (existing project) |
| This design, BOM, path math, grant narrative, diagrams | **CC BY-SA 4.0** |
| Photos of completed mounts (no sensitive interiors) | CC BY-SA 4.0 |
| Node configs (passwords stripped) | CC BY-SA 4.0 |
| No proprietary radio firmware will be funded | — |

Repository: https://github.com/buryd/aredn-houston-county-backbone (public).

---

## 13. Budget

ARDC request **$24,648**. Contingency/indirect is **15%** (under ARDC’s 20% cap). No lobbying. Volunteer time is in-kind, not billed.

### 13.1 Requested from ARDC

| Category | Amount | Notes |
|---|---:|---|
| RF radios, dishes, radomes, indoor nodes, spares | $2,682 | 6+2 Rockets Intl; 6 dishes; 6 radomes; 3+1 hAP ac3 |
| Switching, surge, spare PoE, cable | $849 | VLAN switches, ETH-SP-G2, Cat6, RJ45 |
| UPS and PDU (3 sites) | $915 | Sine-wave UPS for radios |
| Grounding | $343 | Rods, #6, bars |
| EOC 80 ft tilt-over mast | $3,200 | Communications mast, not a lighting pole |
| Hospital roof mast kits (2) | $850 | 15–20 ft, helipad-clear |
| Boxes, entry, hardware, Pi, consumables | $833 | |
| **Hardware subtotal** | **$9,521** | |
| Tax and freight (~8%) | $762 | |
| Licensed rigger, 3 sites | $8,400 | Hospital roofs + EOC mast |
| Electrician grounding, 3 sites | $1,950 | |
| Path walk / alignment | $800 | May be volunteer; budget keeps a paid day if needed |
| Contingency / indirect 15% | $3,215 | Unexpected roof fees, steel, shipping |
| **Total requested** | **$24,648** | |

### 13.2 Hardware detail (from project BOM)

| Item | Qty | Unit | Ext |
|---|---:|---:|---:|
| Rocket 5AC Lite International | 6 | $135 | $810 |
| Spare Rocket 5AC Lite International | 2 | $135 | $270 |
| RD-5G30-LW 30 dBi dish | 6 | $109 | $654 |
| ISO-BEAM-620 radome | 6 | $69 | $414 |
| hAP ac3 International | 3 | $99 | $297 |
| Spare hAP ac3 | 1 | $99 | $99 |
| GS108Tv3 | 3 | $84 | $252 |
| ETH-SP-G2 | 12 | $16 | $192 |
| Spare 24 V gigabit PoE | 6 | $18 | $108 |
| Outdoor Cat6 STP 1000 ft | 1 | $185 | $185 |
| Indoor Cat6 kits | 3 | $18 | $54 |
| RJ45 shielded kit | 1 | $45 | $45 |
| APC BR1500MS | 3 | $280 | $840 |
| PDU | 3 | $25 | $75 |
| Ground rods 8 ft | 6 | $28 | $168 |
| #6 AWG 100 ft | 1 | $85 | $85 |
| Ground hardware | 1 | $90 | $90 |
| EOC 80 ft tilt-over | 1 | $3,200 | $3,200 |
| Hospital roof mast kit | 2 | $425 | $850 |
| NEMA boxes | 6 | $28 | $168 |
| Cable entry kits | 3 | $45 | $135 |
| Stainless / UV hardware | 1 | $95 | $95 |
| Raspberry Pi 5 8 GB kit | 3 | $95 | $285 |
| Consumables | 1 | $150 | $150 |
| **Hardware total** | | | **$9,672** |

*Note: line items above sum to $9,672; the county spreadsheet hardware subtotal of $9,521 is the working PO figure. Use $9,521 + tax $762 + labor $11,150 + contingency $3,215 = **$24,648** as the ARDC request. Reconcile to quote at award.*

### 13.3 In-kind (not requested)

| Contribution | Estimated value |
|---|---|
| ARES volunteer labor (~300 hr × $25) | $7,500 |
| EMA radio-room space, power, drills | $2,000 |
| Hospital roof access / escort | $1,200–$2,400 |
| County electrician if assigned in-house | May replace $1,950 line |

### 13.4 Other funders

None committed. ARDC is the sole cash funder in this application. County and hospitals provide access and in-kind only.

---

## 14. Risks and mitigation

| Risk | Mitigation |
|---|---|
| Link C (11.8 mi hospital–hospital) blocked by trees | Operate hub-and-spoke on A and B; document; optional later high site (not in this grant) |
| Hospital roof delay | EOC mast first so training can start; sequential roofs |
| US-locked radios shipped by mistake | PO language “International / non-US”; refuse -US SKUs |
| Helipad objection | Short masts, published keep-out (2GA3 / 4GE7), 7460-1, Air Evac letter |
| Personnel turnover | Public runbook, club trustee, county ownership of hardware |

---

## 15. Attachments (to upload with grants.ardc.net)

1. This narrative (PDF)  
2. `Houston-County-AREDN-BOM.csv`  
3. `EOC-tower-vs-high-mast-pole.md` and cost comparison  
4. `Perry-Hospital-AREDN-BOM.md`  
5. Site diagrams: EOC mast, Warner Robins Northwest Tower, Perry NNE roof  
6. Letters of support (EMA, both hospitals, ARES)  
7. IRS / government eligibility proof; W-9  
8. FAA 7460-1 receipts when filed  

---

## 16. Contacts (complete before submit)

**Applicant organization:** Houston County Emergency Management Agency  
102 Chief Williams Drive, Kathleen, GA 31047  
Phone: (478) 542-2026  

**PI / grant administrator:** [Name, title, email, phone]  
**ARES lead:** [Name, call, email]  
**Part 97 trustee:** [Name, call]  

We will file at https://grants.ardc.net and notify giving@ardc.net if a pre-application call is useful.

---

*This proposal is written to ARDC’s published application instructions (Learning / Experimenting / Doing, open access, amateur-radio regular use, permits, professional labor where required). It is a draft for the applicant to complete, sign, and submit. It is not an ARDC award.*
