# BiVO4 / Au FDTD Simulation

I prepared a Lumerical optical-simulation workflow for a BiVO4/gold-particle study, including a saved simulation project, geometry helpers, optical-constant inputs and transmittance extraction. The electromagnetic time-domain solver is provided by Lumerical; I did not implement that solver.

Developed by [Vavan Farizzaman](https://github.com/VavanZaa).

## Algorithm

1. Open the saved Lumerical FDTD project and inspect the geometry, material assignment, source and transmission-monitor configuration.
2. Use the geometry helper to compute an equal-area particle radius from the declared total radius and particle count, and place a gold circle at explicit coordinates.
3. Use the supplied BiVO4 refractive-index tables and the selected Lumerical gold-material definition.
4. Run the finite-difference time-domain simulation in the external application.
5. Read the transmission monitor's wavelength and power-transmittance arrays, then plot or export them for comparison.

## Workflow

```mermaid
flowchart LR
Setup["Saved geometry and optical inputs"] --> Parameters["Particle-area helper and material assignment"] --> Solver["Lumerical FDTD run"] --> Monitor["Transmission monitor"] --> Analysis["Wavelength / transmittance extraction and plots"]
```

## Run

Commands below assume a Windows terminal at the repository root unless stated otherwise.

```powershell
# Requires a licensed Lumerical FDTD installation.
# Open "single particle run.fsp".
# Inspect/run "single particle run.lsf" for the geometry helper.
# After a simulation, run "single particle run_T.lsf" for transmittance plotting.
```

## Code map

`.fsp`: saved simulation setup; `.lsf`: geometry and extraction helpers; BiVO4 `.txt` / `.mdf` inputs: optical data; notebook and small images: retained analysis materials.

## Scope and evidence

The helper places one explicitly positioned particle; it is not a complete random-particle generator. Geometry/area calculations do not establish optical improvement. Results depend on the saved project, material data, boundary conditions, mesh and convergence. Commercial application binaries and presentation files are excluded.

This is a focused source snapshot. Installed dependencies, local environments and bulk generated research assets are rebuilt or supplied separately. See [VALIDATION.md](VALIDATION.md) for the checks performed on this export and any remaining setup requirements.
