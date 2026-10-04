# Mooring Design Simulator — Installation and first use

[Version française](INSTALLATION-fr.md).

## Package Contents

The delivery archive usually contains:

- the MooringDesignSimulator application;
- the `library` folder, with the Excel component library;
- the `examples` folder, with sample projects;
- this `INSTALLATION.md` file;
- the `CHANGELOG.md` file.

## Installation

1. Download the archive matching your system.
2. Extract the full archive to a folder of your choice.
3. Keep the application, the `library` folder, and the `examples` folder together.
4. Launch the application from the extracted folder.

Platform notes:

- Windows: launch `mooringDesignSimulator.exe`.
- macOS: launch `mooringDesignSimulator.app`. On first launch, if macOS blocks the application because it was downloaded from the Internet, use right click then `Open`, and confirm.
- Linux: launch `mooringDesignSimulator`. If needed, make the file executable with `chmod +x mooringDesignSimulator`.

Important:

- do not separate the application from the `library` and `examples` folders;
- do not rename the default library unless you also update its path in the application;
- avoid running the application directly from an archive that has not been extracted.

## Upgrading from a previous version

If you upgrade Mooring Design Simulator while a project already uses a loaded component library (for example from v2.0.12 or earlier):

1. replace the installation `library` folder with the one from the new archive, or load the new `library/Library-v2.xls` ;
2. in the `Library` menu, use **Reload current library** to reload the Excel catalogue.

This step is required to show the **new terminal entries** (shackles, galvanised ring, Dyneema thimble link) and apply their **updated properties** in the palette and open projects.

## First Launch

At first startup, the application automatically creates:

- a user configuration file;
- a local database for the temporary working project;
- a local SQLite cache for the component library.

These files are created in the system user configuration directory.

## Getting Started

1. Load the library
   - open the `Library` menu
   - if needed, use `Load new library`
   - the default library is `library/Library-v2.xls`

2. Open or create a project
   - use `File > Open mooring` to open an existing project
   - or `File > New mooring` to start a new mooring

3. Test with an example
   - open `examples/test-1.mooring.sqlite3` for a ready-to-use V2 project
   - or import a legacy V1 project: `examples/mouillage_luckyscale_2021/luckyscale_2021_dyneema.py` or `examples/mouillage_microrio_2021_ATALANTE/MICROMOORING2021_atalante.py`

4. Build or edit the mooring line
   - select a component in the library
   - click `Add selected` or use drag and drop
   - use the `After | Before` selector in the design toolbar
   - the default mode is `After`
   - this mode is applied consistently to drag and drop and to insertions relative to the selected segment
   - use right click on a segment to open the context menu

5. Set the environment
   - open `Configuration > Set environmental conditions`
   - define or import a current profile

6. Run a simulation
   - use `Simulate > Start simulation`
   - then inspect the results in the `Simulation` page

7. Open the built-in help
   - use `Help > Help Content`
   - a local help page summarizing the main features is available inside the application

8. Generate a report
   - use `Report > Generate report`

## Component Library

The component library is read from an Excel file.

If you modify the Excel file:

1. save the file;
2. return to the application;
3. use `Reload current library`.

Some boolean columns in the Excel file are important for clamping:

- `supports_clamp`: tells whether a support can receive a clamped instrument;
- `is_clampable`: tells whether a component may be clamped on a support.

These values must be adapted by the user to match the real operating context.

On the **Anchors** sheet, **Mass (kg, dry)** stores the measurable dry mass for catalogue ballast (for example **Concrete ballast cylinder 1 m**). Leave it empty when ballast mass should be calculated automatically by simulation (solver). **Density (kg/m³)** stores the material density used to convert that dry mass to submerged mass. The application shows the estimated submerged mass in simulation results.

To refresh the shipped **Anchors** sheet: `python tools/update_library_anchors.py`.

Detailed Excel column guide (formulas, projected areas, masses, coefficients):
[docs/component-library-excel.en.md](https://github.com/jgrelet/MooringDesignSimulator/wiki/Component-library).

## File Formats

- Main V2 project: `.mooring.sqlite3`
- Readable export: `.json`
- Legacy V1 project: `.py`
- Library: `.xls`
- Current profiles: `.csv`, `.txt`, `.nc` / NetCDF
