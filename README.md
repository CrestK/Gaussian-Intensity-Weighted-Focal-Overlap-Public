# Gaussian Intensity-Weighted Focal Overlap

An interactive page for the **intensity-weighted focal overlap factor** in ultrafast pump–probe
spectroscopy. Two Gaussian beams (pump and probe) cross inside a sample. The page shows the
beams, integrates their overlap over space and time, and reports how much of it you keep as
you change the geometry or misalign the pump.

## What you can set

* **Experiment**: nondegenerate **2PA**, **transient absorption** (one-photon pump), or
**2P-excited TA** (pump absorbed by two-photon absorption, so the population goes as I²).
* **Each beam**: wavelength (drawn in its color, and sets the Rayleigh range), waist w₀,
pulse duration (FWHM) and peak intensity. Pulse energy and peak fluence are shown.
* **Geometry**: crossing angle θ and sample path length L.
* **Pump position**: Δx, Δy, Δz offset of the pump focus from the probe focus. Use the
sliders, drag the pump in the views, or click the overlap map.
* **Timing**: pump–probe delay and, for TA, an optional excited-state lifetime T₁.

## What it shows

* **f<sub>v</sub>**, the focal overlap. It reads 100% at the best pump position and delay for the current
crossing angle.
* **η**, the absolute overlap: the probe-weighted pump intensity (2PA) or fluence (TA) relative
to its peak. η·I₀ is the effective pump intensity the probe sees, which is the number you need
to turn a measured ΔA into a cross-section.
* **Crossing-angle factor**: the best overlap at θ divided by the best collinear overlap.
* **Crossing plane** (top view, x–z): time-integrated beams with the signal density in white,
or an animation of the pulses crossing in time. The animation shows the pulse-front tilt
that a crossing angle introduces, and in TA mode the excited population left behind by the
pump.
* **Beam cross-section** (x–y at any depth), an **overlap map** of f<sub>v</sub> over pump positions
(Δx–Δy or Δx–Δz, with 50% and 90% contours), a **delay scan**, **position scans** with FWHM,
±90% tolerance and local slope, and the **depth profile** of where the signal is generated.

## Model

The probe travels along z with its focus at the origin. The pump travels in the x–z plane at
angle θ, with its focus at (Δx, Δy, Δz). Both are TEM₀₀ Gaussian beams with Gaussian,
transform-limited pulses propagating in vacuum:

&#x20;   I(ρ, s, t) = I₀ (w₀/w(s))² exp(−2ρ²/w(s)²) exp(−4 ln2 (t − s/c)²/τ²)
    w(s) = w₀ √(1 + (s/z\_R)²),   z\_R = π w₀²/λ


The signal is

&#x20;   S = ∫\_sample d³r ∫ dt D(r, t) I\_probe(r, t)


with D = I\_pump (2PA), D = ∫ I\_pump(t′) e^−(t−t′)/T₁ dt′ (TA), or the same with I\_pump² (2P-TA).
Then

&#x20;   f\_v = S / max S        (max over pump position and delay at the same θ)
    η   = S / (D\_peak · L · E\_probe)


Check value: for collinear beams with no diffraction at zero delay (2PA),
η = w\_pump²/(w\_pump² + w\_probe²) · τ\_pump/√(τ\_pump² + τ\_probe²).

At each depth z the transverse (x, y) and time integrals are done analytically. This includes
the cross-correlation smear from pulse-front tilt across the crossing and the TA rise and
decay. The z integral uses an adaptive trapezoid grid that refines around the crossing region,
the foci and the time-overlap window.

Assumptions: small-signal (linear) response, no pump depletion or saturation, vacuum
propagation (no refraction, dispersion or group-velocity walk-off), and no polarization or
orientation effects. Intensity does not change f<sub>v</sub> or η, because the signal is linear in each beam.
It only sets η·I₀ and the drawing brightness.

## 

