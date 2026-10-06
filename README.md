# Mooring Design Simulator

[Version française](README-fr.md).

**Design, simulate and prepare subsurface oceanographic moorings.**

The MooringDesignSimulator is a desktop application that combines a graphical design tool, a component catalog, and static elongation calculations. It allows users to compare different mooring configurations based on various current profiles and to prepare the reports and workshop documents needed for their implementation at sea.

**Documented version: 2.1.0-RC10 — prerelease.**

[Download the application](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC10) · [User documentation](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home) · [French documentation](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home-fr) · [Version history](CHANGELOG.md)

## Features

- Design several moorings in separate tabs, duplicate a mooring, or copy groups of components along with their clamped instruments.
- Impose design positions, protect prepared rope lengths and adapt the line to the bathymetry.
- Manage a catalogue of floats, instruments, cables, ropes, releases, terminals and anchors.
- Define current profiles manually or import CSV, TXT or NetCDF data.
- Compare depths, tensions, stretch, anchor guidance and deployment/recovery estimates using tables and charts.
- Generate PDF reports and A3 preparation sheets with rope markings and serial number fields for instruments.
- Import and export projects in the legacy Mooring Simulator V1 format with compatibility checks.

![Multiple mooring design](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-designer-rc8.png)

<p align="center"><em>Two-column design, multiple open moorings and simulation tabs.</em></p>

![Simulation results](https://raw.githubusercontent.com/wiki/jgrelet/MooringDesignSimulator/images/mooring-simulation-results-rc8.png)

<p align="center"><em>Simulation results without current or with current.</em></p>

## Getting started

1. [Download the installation archive](https://github.com/jgrelet/MooringDesignSimulator/releases/tag/v2.1.0-RC10) (`mooringDesignSimulator-release.zip`) and extract it completely.
2. Keep the application with the supplied `library/` and `examples/` folders.
3. Open an example, adapt its design and run the simulation.

The documentation is available in the [project wiki](https://github.com/jgrelet/MooringDesignSimulator/wiki/Home). Start with [Installation and first use](https://github.com/jgrelet/MooringDesignSimulator/wiki/Installation), then read the [user guide](https://github.com/jgrelet/MooringDesignSimulator/wiki/UseApplication). The application uses a static solver and simplified launch and recovery models; it does not perform a full dynamic simulation.

The source code is maintained in a private repository. This public repository presents the software; its documentation is maintained in the wiki.

**Author: J. Grelet.**
