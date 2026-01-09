# Awesome-Toolchangers

A curated list of **open-source toolchanger systems** and **hotend module interfaces** for FDM/FFF 3D printers.

> Focus: automatic or semi-automatic **tool / hotend switching** with real docking & locking mechanisms.  
> No “just unscrew the hotend by hand” mounts.

Inspired by [Awesome-Extruders](https://github.com/SartorialGrunt0/Awesome-Extruders) and [Awesome-Toolheads](https://github.com/SartorialGrunt0/Awesome-Toolheads).

---

## Table of Contents

- [Awesome-Toolchangers](#awesome-toolchangers)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Part 1: Mature and Widely Used Solutions](#part-1-mature-and-widely-used-solutions)
    - [1.1 E3D ToolChanger / Motion System](#11-e3d-toolchanger--motion-system)
    - [1.2 Jubilee — Reference Open-Source Toolchanger](#12-jubilee--reference-open-source-toolchanger)
    - [1.3 StealthChanger — Leader of the Voron Ecosystem](#13-stealthchanger--leader-of-the-voron-ecosystem)
    - [1.4 TapChanger — Fundamental Voron Toolchanger](#14-tapchanger--fundamental-voron-toolchanger)
    - [1.5 MadMax — Maxwell Coupling for Static Gantry](#15-madmax--maxwell-coupling-for-static-gantry)
    - [1.6 Blackbox CE — Water-Cooled Kinematic System](#16-blackbox-ce--water-cooled-kinematic-system)
  - [Part 2: New, Experimental, and Alpha/Beta Projects](#part-2-new-experimental-and-alphabeta-projects)
    - [2.1 DAKSH V2 — Prusa XL-Style Without Servo (HIGH PRIORITY)](#21-daksh-v2--prusa-xl-style-without-servo-high-priority)
    - [2.2 FoxChanger — Prusa XL Latch Without Custom Metal](#22-foxchanger--prusa-xl-latch-without-custom-metal)
    - [2.3 ClickChanger — CPAP Cooling in Shuttle](#23-clickchanger--cpap-cooling-in-shuttle)
    - [2.4 MissChanger — Toolless Conversion](#24-misschanger--toolless-conversion)
    - [2.5 Rotating Magnet Toolchanger — Ultra-Low Cost](#25-rotating-magnet-toolchanger--ultra-low-cost)
    - [2.6 Lineux Toolchanger — Pure Klipper Macros](#26-lineux-toolchanger--pure-klipper-macros)
    - [2.7 Doot Changer — $20 BOM](#27-doot-changer--20-bom)
    - [2.8 Proforge 4 — Quad-Core-XY](#28-proforge-4--quad-core-xy)
    - [2.9 3D Printed Magnetic Toolchanger (D\_P\_R)](#29-3d-printed-magnetic-toolchanger-d_p_r)
  - [Part 3: Hotend Module / Hotend Pod Interfaces](#part-3-hotend-module--hotend-pod-interfaces)
    - [3.1 Maxwell Kinematic Coupling](#31-maxwell-kinematic-coupling)
    - [3.2 Kelvin Kinematic Coupling](#32-kelvin-kinematic-coupling)
    - [3.3 Bushing/Pin Interface (StealthChanger style)](#33-bushingpin-interface-stealthchanger-style)
    - [3.4 Pogo Pin Interface](#34-pogo-pin-interface)
    - [3.5 CAN Bus Toolhead Interface (Modern Standard)](#35-can-bus-toolhead-interface-modern-standard)
    - [3.6 Prusa XL-Style Mechanical Latch](#36-prusa-xl-style-mechanical-latch)
  - [Part 4: Comparative Analysis](#part-4-comparative-analysis)
    - [4.1 Locking Mechanics](#41-locking-mechanics)
    - [4.2 Tool Mass and Impact on Speed](#42-tool-mass-and-impact-on-speed)
    - [4.3 Scaling (Number of Tools)](#43-scaling-number-of-tools)
    - [4.4 Firmware Requirements](#44-firmware-requirements)
  - [Part 5: Selection Recommendations](#part-5-selection-recommendations)
    - [Quick-Release Latch WITHOUT Spring-Loaded Nuts (High Priority)](#quick-release-latch-without-spring-loaded-nuts-high-priority)
    - [Maximum Precision / Research Cases](#maximum-precision--research-cases)
    - [Minimum Cost / Experimental Level](#minimum-cost--experimental-level)
    - [Maximum Number of Tools](#maximum-number-of-tools)
  - [Part 6: Sources and Useful Links](#part-6-sources-and-useful-links)
  - [Contributing](#contributing)
  - [License](#license)

---

## Introduction

**Automatic tool changing without servos** opens new possibilities for multi-material printing on CoreXY printers. Over the past few years, the open-source toolchanger ecosystem has significantly expanded — from academic reference designs to production-ready kits with CNC-machined components.

Key trend: transition from **servo-driven cam lock** to **kinematic coupling** with magnetic retention or fully mechanical latches like the Prusa XL, as well as active use of **CAN bus** instead of pogo contacts.

Below is a catalog of systems divided into:

1. Mature and widely used solutions.
2. New, lesser-known, experimental (alpha/beta) projects.
3. Meta-level: hotend module / hotend pod interfaces and docking standards.

---

## Part 1: Mature and Widely Used Solutions

### 1.1 E3D ToolChanger / Motion System

**Status**: Stable / Legacy reference design
**License**: Open-source hardware (E3D)
**GitHub / Docs**:
- https://github.com/e3donline/Motion-System  
- Documentation and assembly: https://e3d-online.com  

**Locking Mechanics**:
- **Type**: Maxwell kinematic coupling + servo-driven cam lock.
- **Coupling**: 3 balls on tool + 3 conical sockets on carriage (6 contact points).
- **Locking**: Bayonet cam lock with spring, driven by micro-servo.
- **Parking docks**: Magnetic dock stations for tool storage.

**Supported Tools**:
- Up to 4 tools: extruders, laser, light mill, grippers, etc.
- Used as reference for multi-material and multi-process printing.

**Hotend Compatibility**:
- E3D V6, Volcano, Hemera, Chimera, Revo (via tool plates).
- Any hotends that can be mounted on E3D tool plate.

**Interface**:
- Tool boards Duet (CAN-like bus) or classic wiring.
- Uses macros in RepRapFirmware for T0/T1/... with docking.

**Features**:
- Essentially the **originator of the E3D-compatible tool plates standard**.
- Inspired Jubilee and many open-source replicas.
- Requires CNC parts (V-grooves, cam-lock), but provides reference-level repeatability.

---

### 1.2 Jubilee — Reference Open-Source Toolchanger

**Status**: Stable (reference design)
**License**: CC BY 4.0 (OSHWA Certified)
**GitHub**: https://github.com/machineagency/jubilee
**Developer**: Joshua Vasquez, Machine Agency, University of Washington

**Locking Mechanics**:
- **Type**: Maxwell kinematic coupling + Remote Elastic Lock (twist lock).
- **Coupling**: 3 steel balls + 3 V-shaped grooves = 6 contact points.
- **Locking**: Wedge plate (cast Delrin) + cable twist lock with spring.
- **Repeatability**: ~**5 µm** (documented).
- **Lifespan**: tens of thousands of cycles before wedge plate replacement.

**Supported Tools**:
- 3D extruders (direct / Bowden).
- Pen plotter, syringe extrusion, laser modules.
- Up to **4–5 tools** (409 mm horizontal rail).

**Hotend Compatibility**:
- E3D V6 (native), Dragon, Revo Six, Mosquito, etc.
- Hemera (community mods).
- Any E3D-compatible tool plates.

**Interface**:
- Individual wiring for each tool (pogo-pins not standardized).
- Duet/RepRapFirmware controllers (native), Klipper via JubileeKlipper.
- Kinematically coupled bed plate with auto-tramming.

**Tool Mass**: ~200 g (typical direct extruder).
**Features**:
- **No spring-loaded nuts** — heat-set inserts.
- Academic-level documentation and examples.
- Used in scientific installations (liquid handling, circuit printing).
- CAD: STEP, STL, SolidWorks assemblies.

---

### 1.3 StealthChanger — Leader of the Voron Ecosystem

**Status**: Stable V1.1
**License**: GPL-3.0
**GitHub**: https://github.com/DraftShift/StealthChanger
**Developer**: DraftShift Design
**Stars**: ~970+

**Locking Mechanics**:
- **Type**: Bushings + pins + magnets (kinematic/friction fit).
- **Locking**: Vertical engagement, fixed by pins and bushings, magnets provide additional retention.
- **NO servo, NO wires on shuttle.**
- **Repeatability**: no worse than TapChanger (confirmed by input-shaper tests).

**Supported Printers**:
- Voron 2.4 (primary target).
- Trident (via liftbar mods).

**Toolhead Compatibility**:
- StealthBurner, Dragon Burner, Rapid Burner.
- Yavoth, AntHead, A4T, XOL.
- Mini StealthBurner (usermod).

**Number of Tools**:
- 300 mm: up to **5 tools**.
- 350 mm: up to **6 tools**.

**Interface**:
- **CAN bus** strongly recommended (EBB36, Nitehawk-36, etc.).
- OptoTap (or Revo PZ) as Z-probe sensor on each tool.
- Backplate pins: 4×12 mm and 4×13 mm.

**Tool Mass**: less than TapChanger (optimized design).
**Firmware**: Klipper + DraftShift fork of `klipper-toolchanger`.

**Features**:
- **No spring-loaded nuts** — bushings on hardened pins.
- All wear parts replaceable without reprinting the entire system.
- LDO Motors produces commercial kits with CNC shuttles.
- Requires ~200 mm tophat for stable operation in enclosed chamber.

---

### 1.4 TapChanger — Fundamental Voron Toolchanger

**Status**: Stable V4.3
**License**: GPL-3.0
**GitHub**: https://github.com/viesturz/tapchanger
**Developer**: Viesturz (Latvia)

**Locking Mechanics**:
- **Type**: Oversized linear rail concept (~4 mm travel).
- **Coupling**: Bearings "rolling" on steel pins/plates (kinematic self-alignment).
- **Variants**: Plates, Rods, Square Rods.
- **NO servo** — uses printer movement (XY+Z).

**Supported Printers**:
- Voron 2.4 (reference).

**Toolhead Compatibility**:
- Dragon Burner (primary) — up to **6 heads on 350 mm frame**.
- StealthBurner, MiniStealthBurner.
- Rapid Burner, Xol-Toolhead (experimental).

**Interface**:
- OptoTap sensor for nozzle Z-probing.
- CAN bus recommended (EBB36/42, SB2040, etc.).
- Liftbar dock variant (V4.0+) for static-gantry printers.

**Tool Mass**: HGX gears toolhead ~17 g lighter than stock.
**Firmware**: Klipper + `viesturz/klipper-toolchanger`.

**Features**:
- **No spring-loaded nuts** — heat-set inserts + standard M3 screws.
- Spring-steel nozzle pads (V2.3+) — don't warp from temperature.
- Reference design on which StealthChanger was built.

---

### 1.5 MadMax — Maxwell Coupling for Static Gantry

**Status**: Active Beta (12+ completed builds)
**License**: GPL-3.0
**GitHub**: https://github.com/zruncho3d/madmax
**Developer**: Zruncho3d

**Locking Mechanics**:
- **Type**: Magnetic Maxwell kinematic coupling (pins and screws).
- **Coupling**: 6 contact points (Maxwell geometry).
- **Locking**: **Magnets only** — no positive-lock mechanism.
- **Detection**: Firmware-based safety (coordinate convergence monitoring and contact sensors).

**Key Innovation**:
> Coupling mechanism **is** the probe — used for Z-probing instead of Tap/Boop.

- Accuracy: range ~**0.002 mm**, std dev ~**0.0005 mm** (per author's test results).

**Supported Printers**:
- Voron Trident (native static gantry support).
- Voron Zero, Micron, Salad Fork.
- Tri-Zero, Pandora's Box.
- Ender3→Trident conversions.

**Toolhead Compatibility**:
- DragonBrick, RapidBrick.
- AntHead, A4T, A4TBrick, OmniBrick.
- XOL, MiniSB, OmniBurner.

**Interface**:
- Front-mounted MGN9H/MGN12H linear rail.
- Keyslot docks + magnets.
- SpeedClips for quick belt attachment.

**Number of Tools**:
- 2 (tested/proven), theoretically more (limited by frame width).

**Firmware**:
- Klipper with `klipper-toolchanger`, KTC2, or Bikin configs.

**Features**:
- **No liftbar** for static-gantry printers.
- XY-only toolchanges — very fast.
- **No spring-loaded nuts** — magnets + pins + screws.
- Automatic offset calibration (Nudge).
- Conversion cost: ~**$100**, fully reversible.

---

### 1.6 Blackbox CE — Water-Cooled Kinematic System

**Status**: Stable (Community Edition)
**License**: CERN-OHL-W
**GitHub**: https://github.com/Kbreezy24/blackbox
**Support**: KB3D, LDO Motors

**Locking Mechanics**:
- **Type**: Jubilee-style kinematic coupling + wedge lock.
- **Cooling**: Passive water cooling for all tools (shared water manifold).
- **Sharing**: Single motor, shared among tools (optional configurations in original Blackbox multi-tool concept).

**Features**:
- Build volume: 300×300×275 mm.
- Up to **5 tools**.
- X-axis mounted extruder motor (weight/cost savings).
- TAMV automatic tool alignment.
- Silicone nozzle wiping/sealing.
- Repeatability: ~22 µm.

**Firmware**:
- Duet 3 (RRF), Klipper configuration possible.

---

## Part 2: New, Experimental, and Alpha/Beta Projects

### 2.1 DAKSH V2 — Prusa XL-Style Without Servo (HIGH PRIORITY)

**Status**: Open Beta
**License**: CC0-1.0 (Public Domain)
**GitHub**: https://github.com/ankurv2k6/daksh-toolchanger-v2
**Developer**: Ankur Verma (3D Unplugged)

**Locking Mechanics**:
- **Type**: Prusa XL-inspired mechanical latch — fully servo-less.
- **Material**: Fully 3D-printed, with metal inserts in critical zones.
- **Locking**: Sliding latch with friction-engagement + PTFE pins.
- **No spring-loaded nuts** — lock/unlock via XY carriage movement.

**Performance**:
- Tool change time: **< 4 seconds**.
- Tested: **2000+ cycles** without degradation.

**Compatibility**:
- Voron Trident, 1.8, 2.4.
- RatRig VCore 3 and other CoreXY.

**Features**:
- Intelligent Error State Detection and Recovery.
- Automatic XYZ calibration across tools.
- Integrated nozzle ooze blockers.
- Status LED on each toolhead (4×4 matrix).
- Wire looms inside frame.
- Recommended latch material — PETG-CF.

**CAD/STL**:
- Complete STL package + CAD (Fusion 360/STEP via community).

---

### 2.2 FoxChanger — Prusa XL Latch Without Custom Metal

**Status**: Beta/Alpha
**GitHub**: https://github.com/Noisyfox/FoxChanger
**Developer**: Noisyfox

**Locking Mechanics**:
- **Type**: Prusa XL-style twist-lock latch.
- **100% off-the-shelf parts** — no custom metalwork.
- **Latch print**: PETG-CF, 100% infill.

**Compatibility**:
- Voron 2.4, Trident.
- Toolhead: Dragon Burner (primary target).

**Probing**:
- BambuLab-style **heatbed piezo sensor** (toolhead space given to latch mechanics, Z-sensor on bed).

**Features**:
- Inspired by Prusa XL latch analysis (3DUnplugged) and DAKSH V2.
- Works with modified Sherpa Zero ECAS.
- CAN boards from KayosMaker.

---

### 2.3 ClickChanger — CPAP Cooling in Shuttle

**Status**: Beta V2.0
**License**: BSD-3-Clause
**GitHub**: https://github.com/viesturz/ClickChanger
**Developer**: Viesturz

**Locking Mechanics**:
- **Type**: Vertical attach/detach + Revo PZ hotend probe.
- **Coupling**: Rigid connection of Y-rail to heatsink.
- **Pogo-pins**: For connecting shared CPAP fan.

**CPAP System (required V2.0)**:
- CPAP fan (mount for WS7040).
- ~1 m tubing, Ø ~15 mm.
- 2-gram micro-servo for CPAP valve.

**Hotend Compatibility**:
- Revo Voron (primary, with Revo PZ).
- Dragon / Dragon HF.
- Rapido HF (not UHF).

**Extruder Compatibility**:
- HGX Large Gears (lightest).
- Orbiter V2, Sherpa mini.

**BOM shuttle** (key):
- 3×6×2.5 mm bearing.
- 2g micro-servo (+ M2×4 screws).
- CPAP fan + tube.

**BOM toolhead**:
- 4×12 mm steel pins.
- 2× 4×6×6 mm bushings.
- Kailh micro-switch (3 mm).
- 30×30×10 mm axial fan.
- 2× 6×3 mm magnets.

---

### 2.4 MissChanger — Toolless Conversion

**Status**: Stable V1.1
**GitHub**: https://github.com/VIN-y/MissChanger
**Developer**: VIN-y

**Locking Mechanics**:
- **Type**: MGN9H-based tapping system (compatible with Voron TAP mechanics).
- **Tap&Change**: for StealthBurner toolheads.

**Key Feature**:
- **Toolless conversion** between modes:
  - full toolchanger;
  - single-nozzle mode with "regular" StealthBurner.

**Compatibility**:
- Voron 2.4, Trident (WIP).
- Revo-Voron (recommended hotend).

**Dimensions**:
- Dock width: 80 mm.
- Bar-ends: 28 mm.
- Profile — fits 2020 extrusion slot.

**Firmware**:
- Fork `klipper-toolchanger` (NOT compatible with upstream TapChanger/StealthChanger configs).

---

### 2.5 Rotating Magnet Toolchanger — Ultra-Low Cost

**Status**: Experimental/Alpha
**GitHub**: https://github.com/totaldesaster/toolchanger
**Developer**: totaldesaster

**Locking Mechanics**:
- **Type**: Rotating magnet ring + Maxwell coupling.
- **Magnets**: Ring of neodymium magnets with alternating N/S polarity.
- **Motor**: 28BYJ-48 stepper rotates "lockplate".
- **Coupling**: Steel balls + L-profiles = 6 contact points.

**Principle**:
- Opposite poles aligned → attraction (locked).
- Same poles aligned → repulsion (unlocked).
- Stepper motor switches modes.

**Features**:
- Almost entirely 3D-printed.
- Very low BOM cost.
- **No servo** — only small stepper.
- Tolerant to light collisions (tool self-seats).
- Good for light Bowden tools.

**Firmware**:
- Klipper (macros in repository).

---

### 2.6 Lineux Toolchanger — Pure Klipper Macros

**Status**: Working
**GitHub**: https://github.com/Bikin-Creative/Lineux-Toolchanger
**Developer**: Bikin-Creative / 3dfiy My Life

**Locking Mechanics**:
- **Type**: Front-mounted docks with DockSlide.
- **Control**: Pure Klipper macros (no third-party plugins).

**Compatibility**:
- VzBot 330, Voron 2.4.
- Hotends: E3D Revo Voron, Trianglelab CHC.
- Toolheads: DragonBurner, Lineux One.

**Requirements**:
- ~120 W per tool (experimental high-flow hotends).

---

### 2.7 Doot Changer — $20 BOM

**Status**: Beta (abandoned but functional)
**GitHub**: https://github.com/AmyTheCute/The-Doot-Changer
**Developer**: Amy / AmyTheBun

**Locking Mechanics**:
- **Type**: Magnetic coupling with locating pins.
- **Variants**: Mag (purely magnetic) and Twist (with motor lock).

**Compatibility**:
- Hypercube Evolution and derivatives.

**Cost**:
- **~$20 BOM**, ~$150 full upgrade (including additional hardware).

---

### 2.8 Proforge 4 — Quad-Core-XY

**Status**: Commercial / Open-source hybrid
**GitHub**: https://github.com/Makertech3D/Proforge-4
**Developer**: Makertech3D

**Mechanics**:
- E3D-style kinematic coupling based on Quad-Core-XY motion.

**Features**:
- Build volume: 400×300×400 mm.
- 4 print heads.
- 60k mm/s² acceleration (claimed).
- ~13 min ABS Benchy (marketing demonstration case).

---

### 2.9 3D Printed Magnetic Toolchanger (D_P_R)

**Status**: Prototype / Concept (legendary prototype)
**Instructables**: https://www.instructables.com/Magnetic-3D-Printed-Toolchnager/
**Author**: D_P_R

**Locking Mechanics**:
- **Type**: Kinematic coupling + servo-driven magnetic twist-lock.
- **Coupling**: 3 balls + 3 V-grooves (E3D-style).
- **Locking**: Servo rotates magnet sector, providing attraction/repulsion.

**Goal**:
- Replicate E3D ToolChanger idea **without CNC parts**,
- Use only 3D-printed parts and off-the-shelf hardware.

**Compatibility**:
- CoreXY with MGN9H X-axis.
- Requires custom belt adapter.

**Features**:
- One of the first fully open-source magnetic toolchanger prototypes.
- Author honestly marks it as "prototype, not finished project", but CAD files are available and serve as excellent reference for own experiments.

---

## Part 3: Hotend Module / Hotend Pod Interfaces

Here is the **meta-level**: docking geometry, interfaces, and standards that can be used for your own modular hotends or mini-toolchangers.

### 3.1 Maxwell Kinematic Coupling

**Geometry**:
- 3 V-grooves × 2 contact points = 6 constraints.
- V-grooves positioned at 120° to each other and "face" the center.
- Provides sub-micron repeatability with proper mechanics.

**Implementations**:

| Project                   | Balls material    | Groove material      | Features                      |
|--------------------------|-------------------|----------------------|-------------------------------|
| E3D ToolChanger          | Precision steel   | Hardened V-grooves   | Servo cam lock                |
| Jubilee                  | 8 mm balls        | Dowel/shoulder pins  | Wedge plate + cable lock      |
| MadMax                   | Ferrous screws    | Printed sockets      | Magnetic-only coupling        |
| totaldesaster toolchanger| Steel balls       | Steel L-profiles     | Rotating magnet lockplate     |

**DIY**:
- Many OpenSCAD/STEP implementations of Maxwell-coupling exist, including adapters for hotend pods.

---

### 3.2 Kelvin Kinematic Coupling

**Geometry**:
- Cone (3 points) + V-groove (2 points) + Flat (1 point) = 6 constraints.
- Central support defined by cone.

**Features**:
- Easier to implement in printing: one conical seat, one groove, one flat surface.
- Used in bed plates of some DIY printers, and can also be adapted for hotend-pods.

Examples:
- Jubilee bed plate.
- UMMD (Mark Rehorst).
- Railcore II bed mounts.

---

### 3.3 Bushing/Pin Interface (StealthChanger style)

**Geometry**:
- Bronze/hybrid bushings slide on hardened pins.
- Usually 2–3 bushing/pin pairs for fixation.

**Typical Dimensions**:
- Pins: 4×12 mm, 4×13 mm (mix/match).

**Advantages**:
- Simpler than balls + V-grooves.
- Worn bushings easily replaced.
- Prints well, doesn't require complex metalwork.

**Implementations**:
- StealthChanger shuttle/backplate.
- ClickChanger toolheads (in combination with other elements).

---

### 3.4 Pogo Pin Interface

**Typical Parameters**:
- Ø ~1.5 mm body, press-fit ring ~1.6–1.7 mm.
- Pitch: ~1.27 mm for SLA, ~2.3 mm for FDM (realistic).

**Application**:
- Power/sensor transmission to swappable module without wires.
- Used in:
  - ClickChanger (CPAP fan connection, sensors).
  - Various custom toolchangers (contacts on dock stations).

**Trend**:
- Pogo pins giving way to **CAN toolhead boards** with 4-wire bus — fewer problems with wear and contact contamination.

---

### 3.5 CAN Bus Toolhead Interface (Modern Standard)

**Advantages**:
- Only 4 wires: **CANH, CANL, +24V, GND**.
- No wear contacts (connector fixed on tool).
- Unique ID/UUID for each head.
- Hot-swap support at firmware level (Klipper/RRF).

**Popular Boards**:

| Board         | Form-factor | Features                                    |
|---------------|------------|---------------------------------------------|
| BTT EBB36     | 36×36 mm   | TMC2209, ADXL345, 1 heater, 2 fans          |
| BTT EBB42     | 42×42 mm   | Same, but larger                            |
| LDO Nitehawk-36 | 36×36 mm | Tailored for StealthChanger/Voron           |
| Mellow SB2040 | Compact    | RP2040-based, high integration              |
| Huvud         | ~42×42 mm  | STM32F103, TMC2209, classic DIY CAN        |

**Electrical**:
- CAN speed: typically 1 Mbit/s.
- CANH/CANL pairs — twisted pair 22–24 AWG.
- 24 V power — heavy 20 AWG.
- 120 Ω termination at bus ends.

---

### 3.6 Prusa XL-Style Mechanical Latch

**Principle**:
- XY carriage movement actuates sliding latch on tool.
- No servo required.
- Support surfaces create self-tightening wedge.

**Materials**:
- Main latch body — 3D-printed (PETG-CF / PA-CF).
- Key stress points — brass/steel inserts.

**Open-source Implementations**:
- **DAKSH V2** — most mature toolchanger with this principle.
- **FoxChanger** — variant using 100% available parts.
- Several prototypes on Discord/Reddit, inspired by Prusa XL mechanism teardown.

---

## Part 4: Comparative Analysis

### 4.1 Locking Mechanics

| System            | Type                          | Servo/Stepper?              | Spring nuts? | Repeatability (reference)  |
|-------------------|-------------------------------|-----------------------------|--------------|----------------------------|
| E3D ToolChanger   | Maxwell + cam lock            | Micro-servo                 | No           | ~5 µm                      |
| Jubilee           | Maxwell + twist lock          | Cable-driven (remote)       | No           | ~5 µm                      |
| StealthChanger    | Bushings/pins + magnets       | No                          | No           | Very high                  |
| TapChanger        | Bearings on rods              | No                          | No           | "Tap-equivalent"           |
| MadMax            | Maxwell + magnets             | No                          | No           | ~0.002 mm range            |
| DAKSH V2          | Prusa XL latch                | No                          | No           | High                       |
| ClickChanger      | Bushings + pogo + CPAP        | Micro-servo for CPAP only   | No           | Good                       |
| FoxChanger        | Prusa XL latch                | No                          | No           | TBD (beta)                 |
| totaldesaster     | Rotating magnets + Maxwell    | Stepper for lockplate       | No           | Experimental               |
| 3D Printed Mag TC | Maxwell + servo magnet lock   | Servo                       | No           | Prototype                  |

---

### 4.2 Tool Mass and Impact on Speed

| System          | Approximate toolhead mass | Impact on acceleration         |
|-----------------|---------------------------|--------------------------------|
| Jubilee         | ~200 g                    | Medium                         |
| E3D ToolChanger | 250–350 g (Hemera)        | Below average                  |
| StealthChanger  | < TapChanger              | Low                            |
| TapChanger      | ~stock Voron toolhead     | Medium                         |
| MadMax core     | ~50 g core + toolhead     | **Minimal** (XY-only TC)       |
| ClickChanger    | "bare" head + CPAP        | Low                            |
| DAKSH V2        | Stock Voron head          | Medium                         |

---

### 4.3 Scaling (Number of Tools)

| System        | Frame 300 mm | Frame 350 mm | Practical maximum      |
|---------------|-------------|-------------|------------------------|
| E3D           | 4           | 4           | 4                      |
| Jubilee       | 4           | 4–5         | 5                      |
| StealthChanger| 5           | **6**       | 6+                     |
| TapChanger    | 5           | **6**       | 6                      |
| MadMax        | 2 (tested)  | 2+          | TBD (geometry-dependent)|
| Blackbox CE   | 4–5         | 5           | 5                      |
| DAKSH V2      | Frame-dependent | Depends | Printer-dependent      |

---

### 4.4 Firmware Requirements

| System         | Primary firmware | Extension / Notes                        |
|----------------|------------------|------------------------------------------|
| E3D ToolChanger| RRF (Duet)       | T-tools macros, docking/undocking        |
| Jubilee        | RRF / Klipper    | JubileeKlipper                           |
| StealthChanger | **Klipper**      | DraftShift fork `klipper-toolchanger`    |
| TapChanger     | **Klipper**      | `viesturz/klipper-toolchanger`           |
| MadMax         | **Klipper**      | `klipper-toolchanger`, KTC2, Bikin       |
| DAKSH V2       | **Klipper**      | Custom modules + macros                  |
| ClickChanger   | **Klipper**      | `klipper-toolchanger`                    |
| Blackbox CE    | RRF (Duet 3)     | Native TAMV                              |

---

## Part 5: Selection Recommendations

### Quick-Release Latch WITHOUT Spring-Loaded Nuts (High Priority)

1. **DAKSH V2** — best candidate for fully mechanical, servo-less system with proven reliability (2000+ cycles).
2. **StealthChanger** — optimal for Voron builds, good community support and commercial kits (LDO).
3. **MadMax** — best for **static gantry** (Trident and derivatives) without liftbar: fast XY-only toolchanges.

### Maximum Precision / Research Cases

- **Jubilee** and **E3D ToolChanger** — academic standard, ~5 µm repeatability and excellent documentation.

### Minimum Cost / Experimental Level

- **MadMax** — ~$100 for conversion.
- **Rotating Magnet Toolchanger (totaldesaster)** — minimal BOM with geared stepper.
- **Doot Changer** — $20 BOM, suitable for Hypercube-class.

### Maximum Number of Tools

- **StealthChanger** and **TapChanger** — up to 6 tools on 350 mm Voron 2.4 frame.
- **Blackbox CE / Proforge 4** — commercialized implementations with 4–5 heads.

---

## Part 6: Sources and Useful Links

**Mature Projects**:
- E3D ToolChanger / Motion System:
  - https://github.com/e3donline/Motion-System
  - https://e3d-online.com
- Jubilee: https://github.com/machineagency/jubilee
- StealthChanger: https://github.com/DraftShift/StealthChanger
- TapChanger: https://github.com/viesturz/tapchanger
- Blackbox CE: https://github.com/Kbreezy24/blackbox

**Beta / Experimental**:
- MadMax: https://github.com/zruncho3d/madmax
- DAKSH V2: https://github.com/ankurv2k6/daksh-toolchanger-v2
- ClickChanger: https://github.com/viesturz/ClickChanger
- FoxChanger: https://github.com/Noisyfox/FoxChanger
- MissChanger: https://github.com/VIN-y/MissChanger
- Lineux Toolchanger: https://github.com/Bikin-Creative/Lineux-Toolchanger
- Doot Changer: https://github.com/AmyTheCute/The-Doot-Changer
- Rotating Magnet Toolchanger: https://github.com/totaldesaster/toolchanger
- 3D Printed Magnetic Toolchanger:
  - https://www.instructables.com/Magnetic-3D-Printed-Toolchnager/

**Firmware / Tooling**:
- klipper-toolchanger (viesturz): https://github.com/viesturz/klipper-toolchanger
- KTC2 (TypQxQ): https://github.com/TypQxQ/Klipper_ToolChanger
- JubileeKlipper: https://github.com/SteveJWallace/JubileeKlipper

**Community**:
- Voron / DraftShift / Toolchanger Discord servers.
- DoomCube Discord (`#madmax-toolchanger`).
- ERCF/Multimaterial servers (discussions of StealthChanger, MadMax, DAKSH).

---

## Contributing

Pull requests are welcome:

- Add **only open-source** projects (GPL, CC, CERN OHL, MIT, BSD, …).
- Be sure to include:
  - link to repository / Instructables / documentation;
  - license (if specified);
  - type of mechanics (kinematic, magnetic, mechanical latch, …).
- Preferably attach a link to an image showing **the dock mechanism**.

---

## License

List content is under **GPL-3.0** license, similar to Awesome-Extruders (can be changed to CC-BY/CC0 before publication if needed).
