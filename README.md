# Kilonova (Real-Time, Browser)
Single-file `index.html` kilonova visualization built with Three.js + custom GLSL.

## What It Simulates (Physics Approximation)
- **Act 1 inspiral (PN-inspired):**
  - chirp-style orbital acceleration using mass-ratio/chirp-mass-scaled phase evolution,
  - tidal deformation using Love-number-style scaling,
  - near-contact bar-mode/shear heating and L1 transfer bridge.
- **Act 2 merger/collision:**
  - prompt collision flash + remnant emission proxy.
- **Act 3 kilonova expansion:**
  - multi-component ejecta geometry: polar (fast, lanthanide-poor), equatorial (slower, lanthanide-rich), jet/cocoon channel.
  - homologous-style expansion scaling (`v ~ r/t`) with free-expansion to Sedov-like deceleration blend.
  - forward shock, reverse shock, and contact discontinuity shells with anisotropic emissivity.
- **Radiation / thermodynamics proxies:**
  - r-process heating rate proxy (`Q ~ t^-1.3`),
  - thermalization efficiency evolution,
  - component diffusion-time model (polar/equatorial/cocoon),
  - diffusion-driven photosphere recession and temperature evolution.
- **Composition / opacity / color physics:**
  - `Y_e`-driven lanthanide fraction and opacity contrast (`kappa` split by component),
  - optical-depth (`tau`) and line blanketing/reprocessing surrogates,
  - multi-band pseudo-spectral transport (UV->NIR bands mapped to RGB),
  - recombination-dependent color transfer and time-evolving blue->purple->red balance.
- **Transport and viewing effects:**
  - light-travel-time retardation approximation (equal-arrival-time style correction),
  - relativistic-style beaming terms for jet/shock emissivity proxies,
  - anisotropic scattering via Henyey-Greenstein-like phase function.
- **Instability/turbulence surrogates:**
  - Rayleigh-Taylor-like finger growth in shell interfaces,
  - Kelvin-Helmholtz-like shear rolls in bridge/jet boundary regions.
- **GRB/cocoon visual model (phenomenological):**
  - prompt/direct/cocoon components with axis collimation, shock-ring evolution, and temporal decay.

## Rendering Techniques
- **Volumetric ray marching** through analytic + procedural density fields.
- **Procedural turbulence/instability structure** (fbm/domain warping style) for RT/KH-like filamentary behavior.
- **Multi-pass post-processing** (bloom, chromatic aberration, sharpening, exposure control).
- **Temporal accumulation/filtering** for stable volumetric output.
- **Physically motivated spectral surrogate** (multi-band approximation mapped to display RGB).

## Runtime / UX
- Runs in browser, no build tools, no external assets besides Three.js CDN.
- Real-time controls for mass/ejecta/opacity/jet/render parameters.
- Free mouse camera controls: orbit, zoom, pan.

## Notes
- This is a **physically informed real-time model**, not a full GRMHD + Monte Carlo radiative transfer solver.
- Designed to maximize visual fidelity under laptop-GPU real-time constraints.
