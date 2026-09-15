# Why the Compass Lies

An interactive demonstration of the six magnetic compass errors from the FAA
*Pilot's Handbook of Aeronautical Knowledge* (FAA-H-8083-25), **Chapter 8 —
Flight Instruments**.

Open `index.html` in any browser. No build step, no dependencies.

## What it covers

The chapter's list — the one usually memorised as **VDMONA** — organised around
the three underlying causes rather than as six unrelated facts:

| # | Error | Cause |
|---|-------|-------|
| 1 | Variation | Magnetic north isn't the geographic pole |
| 2 | Deviation | The airframe's own magnetic fields |
| 3 | Magnetic dip | Flux lines angle into the ground |
| 4 | Northerly turning error | Dip + bank |
| 5 | Acceleration error | Dip + airspeed change |
| 6 | Oscillation | Dip errors applied erratically by turbulence |

Errors 4, 5 and 6 all follow from error 3, which is the point the page is built
around: set the latitude slider to 0° and they disappear.

## Each error is a working instrument

- **Variation** — move along an isogonic chart strip and watch true and magnetic
  north diverge; the true-to-magnetic arithmetic updates with it.
- **Deviation** — drag a handheld radio around the cockpit and watch the needle
  chase it, with a live compass correction card rebuilding itself every 30°.
- **Magnetic dip** — a dipole field cross-section with the local field vector
  resolved into its horizontal and vertical components.
- **Turning / acceleration** — a compass card driven against actual heading,
  plus an error-vs-heading curve you can scrub. The two curves are mirror
  images: each error peaks exactly where the other is zero.
- **Oscillation** — an animated card swinging in turbulence (respects
  `prefers-reduced-motion`).

Latitude is shared across errors 3, 4 and 5, so changing it in one place moves
all three.

## Accuracy

These are teaching models, not avionics. They reproduce the shape, sign and
rough magnitude of each error — where it peaks, where it vanishes, which way it
swings — using the standard rules of thumb (lead/lag ≈ latitude; dip from
tan I = 2 tan λ). Real deviation depends on the specific airframe and real
lead/lag depends on bank and rate as well as latitude.

## Implementation notes

Single self-contained HTML file. All instruments are SVG generated in plain JS;
no libraries. Light and dark themes are defined as CSS custom properties covering
all three viewer states (explicit light, explicit dark, and unstamped `system`).
The true/indicated colour pair follows sectional chart convention — blue for
true, magenta for magnetic — and was checked for colour-vision separation
against both theme surfaces.
