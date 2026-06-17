# Subsea Coning Calculator

**Developed by Blue Gator Subsea, LLC**

A browser-based operational planning tool for deepwater subsea lift operations in the Gulf of America. Calculates critical trigger points for both deployment and recovery operations based on the Safe Over-Boarding Zone (SOZ) coning principle.

---

## What It Does

During a subsea lift, the vessel must maintain a safe horizontal distance from the work site relative to the load's height off bottom (HOB). This relationship forms a cone-shaped exclusion zone. Breaching the cone means the load is too close to the seabed asset before the vessel is in final position — a potentially catastrophic outcome.

This calculator solves two operational questions:

- **Deploy mode:** Given a target vessel transit speed, at what load depth can the vessel begin moving toward the work site without breaching the cone at any point during transit?
- **Recovery mode:** Given crane recovery speed, how far must the vessel travel from the work site before the crane can begin recovering the load?

---

## Key Features

- **Deploy & Recovery modes** — full operational workflow for both directions
- **Trigger point calculation** — the primary output: one number the operator acts on
- **Cone boundary verification** — checks clearance at every step of transit, not just at initiation
- **ROV monitoring alert** — flags when continuous ROV monitoring is required (configurable threshold from seabed)
- **Rigging inspection holds** — models the pre-transit rigging check (deploy) and both bottom and pre-deck checks (recovery)
- **Independent HOB inputs** — separate set-down and lift-off heights for deploy vs recovery
- **Ft/m unit toggle** — inspection depths can be entered in feet or meters per company SOP
- **Cone diagram** — visual plot of load path against exclusion zone boundary
- **Timeline table** — step-by-step record with cone clearance, HOB remaining, and ROV status at each point
- **Mobile & desktop** — fully responsive, works offline, no installation required

---

## Operational Definitions

| Term | Definition |
|------|-----------|
| **Water Depth (WD)** | Depth from surface to seabed at the work site |
| **SOZ %** | Safe Over-Boarding Zone — horizontal distance from work site as a percentage of water depth |
| **SOZ Distance** | WD × SOZ% — the horizontal distance in feet from the work site where the vessel begins the lift |
| **Crane Speed (CS)** | Wire deployment/recovery rate in m/s — the fixed operational limit |
| **Transit Speed (TS)** | Vessel speed in knots moving between SOZ and work site |
| **HOB** | Height Off Bottom — target depth to stop the load above the seabed or nearest asset |
| **Trigger Depth** | Deploy: the load depth at which vessel may begin transit at the set speed |
| **Trigger Distance** | Recovery: the distance vessel must travel before crane may begin recovering |
| **Cone Boundary** | At any horizontal distance D from work site, the minimum safe load depth = WD − (D ÷ SOZ%) |

---

## How the Coning Principle Works

The cone defines the relationship between horizontal distance and vertical clearance. At any moment during transit:

```
Required separation ≥ HOB remaining × SOZ%
```

As the vessel closes horizontal distance, the load must be deep enough that the required separation is satisfied. The calculator checks this constraint at every point during transit — not just at initiation — and flags any breach.

**Deploy trigger depth formula (worst-case solve):**

If vessel speed ÷ SOZ% > crane speed (vessel closes faster than cone shrinks):
```
Trigger Depth = WD − (SOZ Distance ÷ SOZ%) + Transit Time × (TS_fps ÷ SOZ% − CS_fps)
```

If vessel speed ÷ SOZ% ≤ crane speed:
```
Trigger Depth = WD − (SOZ Distance ÷ SOZ%)
```

**Recovery trigger distance:**
```
Trigger Distance = HOB × SOZ%
```

---

## Operation Sequence

### Deploy
1. Vessel holds at SOZ — crane lowers load at CS m/s
2. Crane stops at inspection depth — rigging check by ROV or visual
3. Crane resumes lowering to trigger depth — vessel remains stationary
4. Vessel begins transit at calculated trigger depth — crane continues simultaneously
5. Load reaches HOB as vessel arrives at work site

### Recovery
1. Load lifted to recovery HOB — rigging check at set height above seabed
2. Vessel begins moving toward SOZ — crane holds at bottom check depth
3. After trigger distance is traveled — crane begins recovering at CS m/s
4. Crane stops at pre-deck inspection depth — final rigging check
5. Load recovered to deck at SOZ

---

## ROV Monitoring

Per standard operating procedure, continuous ROV monitoring is required whenever the load is within a set threshold of the seabed while the vessel is in motion. The default threshold is 500 ft. This is configurable in the calculator to match company SOP.

---

## Usage

No installation required. Open `index.html` in any modern browser on desktop or mobile. The calculator runs entirely client-side with no internet connection needed after the page loads.

**To add to your home screen on mobile:**
- iOS: Share → Add to Home Screen
- Android (Chrome): Menu → Add to Home Screen

---

## Live Tool

[**Launch Subsea Coning Calculator**](https://bluegatorsubsea.github.io/Coning_Calculator/)

---

## About

Developed by **Chris Petersen** — 30+ years deepwater Gulf of America experience in subsea construction, IMR, SURF, RLWI, and FPSO field development.

**Blue Gator Subsea, LLC** — Independent subsea consulting and operational planning.

---

*This tool is provided for operational planning reference. All lift operations must be conducted in accordance with applicable company procedures, regulatory requirements, and the judgment of qualified offshore personnel.*
