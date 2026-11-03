# Mooring Design Simulator

[Version française](README-fr.md).

**Design, simulate and prepare subsurface oceanographic moorings.**

The MooringDesignSimulator is a desktop application that combines a graphical design tool, a component catalog, and static elongation calculations. It allows users to compare different mooring configurations based on various current profiles and to prepare the reports and workshop documents needed for their implementation at sea.

**Documented version: 2.1.0-RC15 — test candidate.**

The documentation and GitHub download links below refer to the RC15 test candidate.

[Download from GitHub](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC15) · [OneDrive folder](https://1drv.ms/f/c/be92ea594b94cdce/IgAfXMAZMKe4RaSl96BxX8dJAfWHU9u-r8ky-FK3yJPCdiw?e=hUyrJx) · [User documentation](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home) · [French documentation](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home-fr) · [Version history](CHANGELOG.md)

## Features

- Adopt validated prepared cable lengths and clamp positions as the editable design, retain scientific immersion targets and recalculate current scenarios consistently; identify the geometry source in results and record preparation in PDF reports and Deployment Sheets.
- Design several moorings in separate tabs, duplicate a mooring, or copy groups of components along with their clamped instruments.
- Impose design positions, protect prepared rope lengths and adapt the line to the bathymetry.
- Manage a catalogue of floats, instruments, cables, ropes, releases, terminals and anchors.
- Define current profiles manually or import CSV, TXT or NetCDF data.
- Compare depths, tensions, stretch, anchor guidance and deployment/recovery estimates using tables and charts.
- Generate PDF reports and A3 preparation sheets with rope markings and serial number fields for instruments.
- Import and export projects in the legacy Mooring Simulator V1 format with compatibility checks.

![RC13 design view](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-designer-rc13.png)

<p align="center"><em>RC13 — Two-column design, instrument library, component editor and simulation tabs.</em></p>

![Simulation results](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-simulation-results-rc8.png)

<p align="center"><em>Simulation results without current or with current.</em></p>

## Getting started

1. Download the installation archive from [GitHub](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC15), matching your operating system and processor: `mooringDesignSimulator-windows-amd64.zip`, `mooringDesignSimulator-linux-amd64.tar.gz` or `mooringDesignSimulator-linux-arm64.tar.gz`. Extract the archive completely. macOS builds are available only on demand and are not included in this RC15 publication.
2. Keep the application with the supplied `library/` and `examples/` folders.
3. Open an example, adapt its design and run the simulation.

**Updating on Windows:** if a previous installation already contains the `library/` and `examples/` folders, you can download only `mooringDesignSimulator.exe` and replace the existing executable in that installation folder. Download the full archive if you also want the latest supplied library and examples.

The documentation is available in the [project wiki](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home). Start with [Installation and first use](https://github.com/jgrelet/MooringDesignSimulator/wiki/Installation), then read the [user guide](https://github.com/jgrelet/MooringDesignSimulator/wiki/UseApplication). The application uses a static solver and simplified launch and recovery models; it does not perform a full dynamic simulation.

The source code is maintained in a private repository. This public repository presents the software; its documentation is maintained in the wiki.

**Author: J. Grelet.**
