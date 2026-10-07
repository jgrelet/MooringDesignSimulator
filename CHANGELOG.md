# Changelog

Notable product changes in Mooring Design Simulator are listed here.

The format is inspired by [Keep a Changelog](https://keepachangelog.com/).
Versions follow the project Git tags.

## [Unreleased]

### Fixed

- Fix Windows startup failures caused by an incompatible Qt runtime.

- Preserve saved component properties when opening or restoring moorings; loading the library no longer marks the first restored tab as modified after Discard. Explicit library selection or reload still updates the active mooring.
- Remember the main window size, position and maximized state automatically, fit restored windows to the available screen, and remove manual screen dimensions from global configuration.
- Fix Linux executable startup by bundling the OpenSSL libraries required by the NetCDF stack.
- Restore PDF report and preparation-sheet previews on Linux by shipping the complete Qt PDF bindings.
- Correct recommended anchor sizing with current by using the horizontal-load magnitude in the formula inherited from V1. V2 measures signed inclination angles from the vertical along the line from top to bottom; their sign must not reduce the recommended ballast, regardless of the surface or seabed depth reference.

### Added

- Add Abort to the clamp-position dialog to cancel the entire operation; distinguish cancellation from No, which keeps drag-and-drop insertion without clamping.

## [v2.1.0-RC10] - 2026-10-06

### Added

- Remind users to return to Conception when attempting to edit a read-only simulated mooring.

### Changed

- Replace components within any library family, including clamped instruments, while preserving their placement and compatible attachments.
- Keep the selected result page and chart when switching between no-current and current simulations, including undocked results.

### Fixed

- Match mooring-profile instrument and float markers to the segment-start or clamped-attachment depths in the results table; position hover details around instrument labels without overlap and show two-decimal coordinates.
- Avoid blank-tab and mooring redraw flashes when quitting after discarding unsaved changes; retain the original active mooring for the next session.
- Align instrument and float markers with the solver geometry in mooring-profile figures, including instruments clamped inside discretized ropes.

## [v2.1.0-RC9] - 2026-10-05

### Added

- Provide SHA-256 checksum files for the executable and release ZIP, with download verification instructions.
- Open the public English/French user wiki from the Help menu.

### Changed

- Use one standard seawater density of 1025 kg/m³ for static equilibrium with or without current, launch/recovery and dry/submerged mass conversions; clarify the difference from V1 in EN/FR documentation.
- Maintain shipped demo projects and current profiles under examples/demo; retire the previous example paths from version control and update installation guidance.
- Align English and French in-app help with the user guide, clarify solver discretisation and recovery limits, and place startup and depth-review guidance in their relevant sections.

### Fixed

- Reuse a pristine unsaved empty designer tab when opening a project, including after restoring an empty working project at startup.
- Reuse the loaded component library and cached palette icons when creating or closing mooring tabs, avoiding unnecessary catalogue reloads and long waits.
- Enable Save and Save As only when the active designer contains at least one segment; prevent saving empty mooring files.
- Fix the Windows release executable missing Qt/Shiboken DLLs; reject incomplete executables before creating the distribution ZIP.

## [v2.1.0-RC8] - 2026-10-03

### Added

- Select every segment in the active designer with Ctrl+A to copy or cut a complete mooring between projects; text fields retain their usual Select All behavior.
- Include depth or height above seabed and its Locked/Free status below the segment number in designer tooltips; identify locked rope lengths separately.
- Press Escape to cancel a designer group selection and restore the previously selected segment.
- Show a padlock after component names in the designer's right-hand column for imposed depths, including clamped instruments, to distinguish them from free positions and locked rope lengths.
- Rename or duplicate a mooring from its tab's right-click menu; renaming a saved mooring saves its edits and changes the project filename.
- Open moorings in independent designer tabs, with separate simulations, undo histories, configurations and save/close prompts.
- Duplicate a complete mooring into a new unsaved tab for preparing nearby campaign stations.
- Select multiple segments with Ctrl/Shift and copy, cut or paste groups between moorings, preserving clamped instruments and locked lengths; convert depth references and reject duplicate ajustable ropes or ambiguous auto spans.
- Warn on V1 export when component names are absent from the supplied V1.1 reference library; explain silent omissions during V1 import and include Library-v1.xls for compatibility checks.
- Show a red [length undef] marker in the designer for ropes without a positive entered or calculated length.
- Choose whether a component position is imposed during conception or follows the mooring line, in either depth reference.
- Lock prepared rope and sling lengths; show their lengths in blue with a lock marker and exclude them from automatic adjustments and correction proposals.
- Apply an exact proposed rope correction from the component editor, or choose another eligible rope in the affected interval; corrections preserve imposed clamp positions and can be undone.
- Explain configuration inputs with hover tooltips in project information, global settings, current profile cells and NetCDF selection dialogs, including units and depth-reference conventions.
- Wrap configuration tooltips into lines of at most 40 characters for easier reading.

### Changed

- Share the last project directory between Open and Save dialogs across tabs and application restarts.
- Display Static length, Design depth and Simulated depth with two decimal places in the simulation Segments table.
- Restore all open moorings and the active tab at startup; allow dragging designer tabs to reorder them and retain that order between launches.
- Apply rope corrections immediately after manual rope selection, including the proposed rope; explain insufficient length and name the imposed components bounding the correction instead of an "affected interval" message.
- Explain independent imposed positions in the help; show segment numbers and current lengths in designer tooltips, color the [ajustable] marker with its length, and keep unsuitable correction candidates selected with a precise refusal explanation.
- Rename the adjusted rope mode to "ajustable" in the editor and designer; highlight only its parenthesized length in amber with an [ajustable] marker, leaving the segment row in its normal style.
- Keep the edited segment selected when locking its length; place the depth and length checkboxes below its number, rename the depth checkbox to "Impose this depth", remove the Label editor field, and use only the lock icon beside protected lengths.
- Block simulation of incoherent mooring designs, including incompatible imposed positions, unresolved auto ropes, invalid lengths and components outside the water column; informational review messages remain separate.
- Detect depth-closure discrepancies greater than 1 mm and let the adjusted rope absorb added connection hardware within its constrained interval.

### Fixed

- Dispatch hover tooltips consistently across designer tabs and retain instrument details on clamped cells and compact terminal images.
- Keep component hover tooltips in normal weight when their designer labels are bold.
- Preserve Ctrl/Shift group selection when clicking designer names or depths, so copy/cut transfers every selected segment.
- Name duplicated saved moorings after their source tab and honor confirmed overwrites when native paths use different separators.
- Use a simple SQLite suffix in the native save dialog and normalize malformed mooring extensions, including a missing separator before mooring.sqlite3.
- Normalize repeated or partial .mooring.sqlite3 extensions when saving; update a duplicate's generated name on its first save, refresh its tab immediately, preserve explicitly defined names and reopen corrected legacy filenames from the session or recent files.
- Identify saved mooring tabs by filename, avoiding misleading copied project names when opening a different file; retain the internal project name in the tab tooltip.
- Display the first components immediately in new and duplicated mooring tabs, without requiring a switch to another tab.

## [v2.1.0-RC7] - 2026-10-02

### Changed

- Show the current Depth reference (surface or bottom) in the first row of the component editor, with reference tooltips.
- Label the component editor depth field as Height above seabed in bottom-reference projects, with matching reference tooltips; retain Target depth for surface-reference projects.

### Fixed

- Show calculated segment positions in the component editor when no explicit depth constraint is stored, using the active depth reference without creating constraints when other fields are validated.
- Convert mooring positions and clamp review references when switching between surface and bottom depth references; preserve rope lengths and reject conversions without valid bathymetry or with positions outside the water column.
- Keep clamped instrument positions, height/ratio edits, and rope marking distances consistent in bottom-reference projects.
- Resolve automatic rope lengths between heights above the seabed in bottom-reference projects, including a zero-height anchor, without spurious depth-gap warnings.
- Convert negative target-depth entries to positive values during validation, with an explicit V1-to-V2 sign explanation and the usual geometry checks; flag saved negative targets as input errors instead of suggesting rope-length changes.
- Show the wait cursor over every component editor field during validation and diagram refresh, including Enter, length-mode selection, and Apply changes; restore the normal cursor for dialogs and after errors.
- Keep the first fixed-depth instrument in place when editing the head float depth by resizing the longest fixed rope in that span; reject seabed depths that would lift the fixed-length mooring above the sea surface and clarify rope-length guidance.

## [v2.1.0-RC6] - 2026-09-30

### Added

- Export the designed mooring as a Mooring Simulator V1 text project, with explicit compatibility checks for unsupported clamps, unresolved ropes, depth reference, and anchor wet weight.
- View read-only mooring plans with simulated segment depths beside the No current and numbered Current results; selecting Conception restores the editable design.
- Select one amber-highlighted adjusted rope anywhere above the anchor; changing the anchor target depth updates its length and downstream instrument targets while leaving a fuse rope below the release unchanged.
- Start newly added library ropes in auto length mode, including drag and drop; resolve each unambiguous interval as soon as its bounding depths are known, while leaving intervals with several auto ropes unresolved.
- Resolve separate automatic rope lengths between successive fixed-depth instruments.
- Choose one or two columns for the Conception mooring diagram from its action bar.
- Compare a fixed no-current simulation with closable result tabs for each selected current profile, detach all simulation tabs together, and list every open profile as a depth/speed table in the PDF report.

### Changed

- Use the down arrow for the next PDF preview page and the up arrow for the previous page.

### Fixed

- Limit V1-exported current profiles to the mooring water column, interpolating at the seabed or extending the nearest speed when needed, as in V2 simulation.
- Keep the adjusted rope role after simulation, project save/reopen, and library refresh; disable auto for fixed ropes and reject a second auto rope in the same depth interval with a warning.
- Show the rope's required final length in depth-gap warnings, and apply component-editor text edits with Enter while enabling Apply changes only for pending edits.
- Preserve recent files and user preferences when the application version changes.
- Close an existing depth gap with the adjusted rope when the anchor target depth changes, and identify that rope in the interval warning.
- Convert resolvable saved auto ropes to fixed lengths when opening a project.
- Keep entered float, instrument, and anchor depths in the designer after simulation fixes auto lengths; report incompatible fixed-length intervals without moving a depth target.
- Apply a rope's selected length mode immediately so changing selection does not discard an unconfirmed `auto` choice.
- Restore the selected designer column count across application sessions, with two columns as the default.
- Show a wait cursor while changing the designer's display columns.
- Explain simulation Summary results with tooltips on each label and value, including static convergence diagnostics.
- Balance the simulation Summary columns by placing Depth reference below the anchor values.
- Put the selected anchor dry and wet masses first in Summary and emphasize the dry mass used for the design.
- Identify the no-current and current-profile passes in the simulation progress window title.
- Preserve each clamped instrument's drag coefficients when combining its projected area with its support.
- Report static convergence diagnostics and the actual end condition of the launch calculation; interpolate the final step at seabed contact.
- Keep the Rupture recovery terminal selector synchronized with terminal selections in Conception, in both directions.
- Include a standalone copy of `CHANGELOG.md` in the local `dist` release directory.

## [v2.1.0-RC5] - 2026-09-21

### Added

- Compare recovery after a terminal breaks, with or without ballast release, including the affected equipment and any buoyancy deficit, on screen and in PDF reports.

### Changed

- Explain in the help why only one rope can use auto length and how to choose a different rope.
- Clarify that Segment Angle describes the tension-line direction at pinned terminals, rather than the terminal's mechanical orientation.

### Fixed

- Keep Backup Profile focused on components and their buoyancy down to the release, with a visible zero reference.
- Treat the grounded anchor as a fixed boundary and omit its undefined inclination from angle results; preserve the final anchoring depth after solver convergence.
- Simulation now uses the same auto-rope length calculation as the designer, removing conflicting estimates.
- Preserve projected drag areas for floats, instruments, terminals, releases and anchors when preparing simulations; only rope areas are scaled by length.

## [v2.1.0-RC4] - 2026-09-17

### Added

- Replace a rope or terminal directly from its context menu by clicking a compatible library component, while preserving the segment position, rope length, and clamp attachments; replacement mode returns focus to Conception and its active library list.

### Changed

- Replace the Segments table centre-depth result with the simulated segment-start or clamp-attachment depth, and rename Dz as the cumulative vertical distance from the mooring top.

### Fixed

- Apply rope projected area per metre across the full resolved rope length, restoring current-induced inclination and simulated depth changes.
- Keep the deepest mooring constraint fixed during static simulation so an anchored head submerges as the line inclines under current.
- Warn when an inline component target depth requires an upstream rope-length adjustment.

## [v2.1.0-RC3] - 2026-09-16

### Changed

- Define A3 preparation-sheet serial-number fields exclusively through the optional library column `serial_number_labels` (pipe-separated equipment names); populate the bundled Excel and SQLite catalogues and remove name/image-based label rules.
- Display target depth with one decimal in the component editor while preserving the precision of untouched values.
- Display clamp-dialog validation warnings in red on two lines.

### Fixed

- Allow direct target-depth clamping on an unresolved auto rope, and let any explicitly positioned inline component constrain the auto-length span.
- Recompute the clamp ratio when confirming an unchanged target depth after a support moves, keeping the design and simulation position consistent with the confirmed depth.
- Reject clamp-dialog positions already occupied by another instrument on the same support.

## [v2.1.0-RC2]

### Added

- Explain every Segments table column with a compact three- or four-line header tooltip.

- Show Δz in Mooring Profile hover details and distinguish blue hover text from dark-red fixed instrument labels.
- Continue current-profile keyboard entry with Tab from the last speed cell to a new depth row.
- Add a signed Δz immersion-change column to simulation Segments, comparing nominal and simulated segment starts or instrument attachments.
- Add A3 preparation-sheet S/N boxes for single/tandem releases and integrated Iridium, ADCP and Microcat equipment on lenticular buoys.

### Changed

- Place Define project first in the Configuration menu.

### Fixed

- Preserve source column order in library tables and SQLite caches, including missing properties and filtered views.
- Reject tab-separated current rows with missing depth or speed instead of shifting columns, and omit NetCDF points with missing current components instead of treating them as zero current.
- Preserve zero wet masses during library import, refresh older Excel caches, and keep library values aligned with their named columns when properties are missing.
- Resolve legacy zero clamp ratios from nominal attachment depths, including bottom-anchored FC projects, so Microcat simulation depths and Δz match the design.
- Use the computed attachment depth for clamped instruments in simulation result rows.
- Show the wait cursor while generating a PDF report and preparing its preview window.

## [v2.1.0-RC1]

### Added

- Identify component library formats in Excel and SQLite, reject incompatible versions, and offer conversion of recognized legacy libraries to separate V2 files without overwriting originals.
- Add File > Print > Mooring preparation sheet with an A3 preview, one/two-column pagination, handwritten instrument S/N boxes, PDF export and printing without running a simulation.
- Show nominal Design depth alongside Simulated centre depth in the simulation Segments table, using the selected surface or bottom reference.
- Set target depth or clamp ratio directly in the clamping dialog, using the configured rope-marking tail as the initial position.
- Add rope-counter calibration in global configuration, entered as a percentage or ratio, with calibrated instrument-marking distances from both rope ends alongside nominal distances in the PDF report.
- Record application events in rotating log files and provide Help > View Logs to open the current log in the default text editor for troubleshooting.
- Document log access and storage in the English and French in-app help.
- Preview PDF reports before saving, with shared Save PDF and Print actions, page navigation and zoom for reports and mooring preparation sheets.
- Show an application splash screen before loading the main window, with logo, version, startup date and author contact details.
- Add an Instrument column to PDF rope markings, pairing each instrument with its distances from both rope ends.
- Add a breaking-strength tab and PDF table for rope and terminal static/launch utilization, with colour indicators, rupture-limit legends, project segment numbers and click-to-focus in Conception.
- Allow simulation results to be detached into a synchronized window and docked again.
- Add project-only visual scale editing for all occurrences of a component model, with undo/redo and PDF rendering.

### Changed

- Ship `Library-v2.xls` and `Library-v2.sqlite3` with versioned metadata; relocate missing historical default-library paths to the V2 library.
- Preserve relative component image sizes and centre preparation sheet columns; show a printer preview before printing.
- Clarify inventory labels with Quantity and pcs for counted components in the UI and PDF report.
- Show a wait cursor and suppress repeated input during mooring design edits; clear the previous diagram before loading a project.
- Improve PDF chart readability with two full-width plots per page, preserved proportions, larger text, stronger curves and separated component labels.
- Fix Mooring Profile hover and annotation readability
- Show the rope-piece convergence advice only when hovering over its value in simulation Summary.
- Default the simulation max rope piece to 50 m and show the value used in Summary with guidance for checking the speed/accuracy compromise.
- Display numeric simulation results with one decimal place in the UI and PDF, retaining full calculation precision.
- Use upper-end depths for mainline segments in PDF tables, matching V1, and prevent numeric values from splitting across lines.
- Group supports and clamped instruments in PDF segment tables, showing their combined wet weight once and highlighting instrument information in blue.
- Identify the selected anchor wet weight explicitly in screen and PDF summaries; keep the mooring figure in PDF reports after removing the redundant results tab.
- Render paginated PDF mooring figures using Conception proportions and project visual scales.
- Use red for launch tension and blue for static tension in the launch chart.

### Fixed

- Retain DEBUG diagnostics in rotating log files with an INFO console, and record handled import/export failures, library fallbacks and solver convergence for troubleshooting.
- Use the report Mooring Figure layout for preparation sheets, preserving continuous component placement and adding instrument S/N fields.
- Keep edits and undo/redo in a separate working database so Discard reopens the last explicitly saved project; publish SQLite saves atomically.
- Restore the wait cursor immediately after closing the clamp placement dialog, before applying the position.
- Make the last edited clamp position field authoritative: target depth and clamp ratio update each other without rounded display values overriding the user input.
- Focus the matching Conception segment when clicking a simulation Segments cell or row number, and explain its calculated depth reference in the header tooltip.
- Convert imported V1 wet anchor weights to V2 dry masses using the anchor material density.
- Label all anchor weights as wet or dry in the simulation summary and PDF report.
- Restore Mooring Profile hover-to-focus on vertical curves and float/instrument markers, including clamped instruments, and separate on-screen component labels with leader lines.
- Start launch dynamics with the mooring at the surface and the anchor entering first, followed by the components above it; consistently identify the next entering segment at immersion boundaries.
- Unify chart hover details with offset labels and matching segment highlighting in Conception, including tension, segment angle and head ascent speed charts.
- Base clamp depth-review warnings on each support’s saved geometry instead of global revision counters; preserve project depths when changing unrelated global settings such as simulation rope-piece size.
- Avoid unnecessary clamp depth-review warnings when changing rope-marking tail or moving an already clamped instrument.
- Apply the configured rope-marking tail when placing default clamps by drag-and-drop or context menu, with a matching stored depth and undo support.
- Preserve instrument positions when acknowledging depth-review alerts with unchanged inspector fields.
- Refresh terminal images immediately after visual-scale changes.
- Avoid target-depth review alerts when only ballast mass changes, and size depth badges for the full highlighted value.
- Apply rope and chain mass per metre exactly once to resolved segment lengths before solver discretization.
- Report each component’s own wet weight without double counting clamped instrument loads on supports.
- Hide inapplicable segment context actions and restore the French clamping help link.
- Fix release example projects that shipped as empty SQLite shells without project metadata, by versioning only curated example files in git (`test-1.mooring.sqlite3` plus legacy V1 `.py` scripts for luckyscale and microrio) and validating them in CI.

## [v2.0.13]

### Added

- Add confirmation and cascade deletion when removing a support rope with clamped instruments.
- Add one-click span absorber activation in the design inspector when top and bottom depths need closing.
- Add multi-level undo stack (25 snapshots) with redo (Ctrl+Y) in the edit toolbar.
- Migrate legacy rope segments from `none` to `fixed` length mode when opening a project.
- Materialize `auto` rope lengths as `fixed` on JSON/V1 import and JSON export; remove invalid `auto` flags from non-rope segments.
- Improve span absorber activation button label and visibility in the component editor.
- Add dedicated terminal sprites for shackles (7/16 to 7/8), galvanised ring, and Dyneema thimble link in the default component library.
- Add Shackle 7/8 and Dyneema link terminal catalogue entries to the default library spreadsheet.
- Show bottom-referenced depths in the design view when the project depth reference is set to bottom.

### Changed

- Refresh recent default library spreadsheet revisions: redesign terminal rows for shackles and ring with size-specific artwork in the palette and design view.
- Update terminal submerged mass, axial length, and breaking-strength values for shackles and ring from Crosby manufacturer catalogue data (public specifications).
- Mark Dyneema 6 mm rope as clamp-capable in the default library.
- After upgrading from v2.0.12 or earlier, reload the component library (`Library` menu → **Reload current library**) to pick up new terminal entries and updated catalogue data.
- Keep the anchor fixed on the seabed when both head and anchor depth constraints are set; propagate depths from the anchor and pin the head float at its target depth instead of moving the ballast upward.
- Show the span absorber activation button when several legacy auto ropes block span closure, not only when zero ropes are auto.
- Improve main-line depth propagation and clamp display depths from support rope geometry in the design view.
- Show rope length labels only on rope segments and display span-closed auto lengths in the segment editor.
- Enforce a single main-line auto rope: lock the UI when another rope is already auto and highlight the absorber segment in the diagram.
- Use anchor and head float target depths as layout references; close the mooring span only when both ends are set; show an info message when layout cannot run without head or anchor constraints.

### Fixed

- Fix application startup crash caused by calling `setWordWrap()` on the span absorber `QPushButton`.
- Fix design view showing stale auto rope lengths and depths after window resize or zoom reflow.
- Fix non-monotone main-line depths after head depth changes by removing the head-only pin and always closing the span on the auto rope before propagation.
- Fix layout depths ignoring adjusted auto rope lengths while labels still showed effective values, by using explicit auto overrides from the design layout and aligning rope marking with the same effective lengths.
- Log span absorber activation with the UI segment number instead of the internal database id.
- Fix unsaved-project discard leaving a restorable working database and modified session state after undo/redo edits.
- Hide the anchor dry-mass row in the component editor for non-anchor segments.
- Always re-run span closure when computing design depths so auto rope display lengths track structural edits instead of reusing stale overrides.
- Compute span-absorber activation gaps from fixed main-line lengths only so the offer appears after segment removal when no auto rope is active.
- Keep one-row layout for ropes with a single clamped instrument; show clamp target depth and field marking distance in parentheses as before.
- Bound clamp display depths to the current support rope span so stale imported target depths cannot sit outside their support segment.
- Highlight clamped instruments in red when their stored target depth lies outside the support rope span, including an inspector warning.
- Fix ghosted duplicate mooring diagram after library reload by hiding torn-down widgets immediately and refreshing the design view from the updated catalogue.
- Fix startup diagram flash where the mooring layout appeared, cleared, and rebuilt again by deferring the first visible draw until the window viewport is final and skipping redundant workspace refreshes during library load.
- Highlight stale in-span clamp target depths in orange after mooring layout changes, without auto-resyncing stored targets.
- Fix legacy V1 import marking floats as auto when their name contains “chaine” or “chain”.
- Count only rope segments in main-line auto-length warnings and span-absorber logic.

## [v2.0.12]

### Added

- Normalize component library masses at Excel import: positive Excel magnitudes and consistent submerged, dry, and solver mass fields for anchors.
- Expand integrated help library sections with projected-area rules, mass signs, drag formulas, and anchor conversion examples.
- Add `Density (kg/m³)` to the library **Anchors** sheet and populate steel/concrete catalogue rows (7850 and 2400 kg/m³).
- Add `Mass (kg, dry)` to the library **Anchors** sheet and ship a `Concrete ballast cylinder 1 m` catalogue entry (1885 kg dry, 1 m diameter × 1 m cylinder, `concrete.bmp` icon).
- Show estimated submerged mass in the simulation summary and PDF report after dry-to-wet conversion.
- After each simulation, copy the recommended submerged anchor weight into **Anchor dry mass (kg)** only when that field is still empty, converting from apparent weight with the anchor material density.

### Changed

- Log recovered exceptions through `log_handled_exception()` instead of silent `try/except` fallbacks; use `-d` / `--debug` for tracebacks on expected fallbacks.
- Show a modal simulation progress dialog with named pipeline steps instead of only a wait cursor during `Start simulation`.
- Drive the simulation progress bar continuously from solver iterations instead of fixed pipeline step weights.
- Reserve a wide dynamics band for launch integration so the bar no longer stalls near 98% mid-deployment.
- Avoid a duplicate workspace refresh when restoring the working project at startup.
- Shorten in-app library help: positive Excel mass magnitudes, immersed mass wording, projected-area convention; remove broken links to repository-only Excel guides; document empty anchor dry mass as solver-calculated.
- Align component-library Excel guides and installation notes with solver-based anchor dry-mass calculation.
- Replace French doc wording *magnitude* with *valeur positive* / *valeur négative* and standardize on *masse immergée* in in-app help and the component library Excel guide.
- Use GitHub-compatible `$...$` / `$$...$$` math delimiters in the component library Excel guide.
- Log one worksheet summary line in DEBUG mode when rendering the library dock instead of per-cell column traces.
- Replace the slow JSON example-project GUI test with a lightweight fixture and stubbed library dock load.
- Simplify simulation snapshot building when catalogue rows expose normalized `mass_solver_kg`, while preserving legacy V1 sign inversion and locally stored legacy Excel signs on project segments.
- Document uniform positive mass magnitudes in the component library Excel guide (FR/EN), including workshop-measured submerged weights for terminals, instruments, and releases.
- Flip `library/Library.xls` wet-mass columns to positive magnitudes (option A2).
- Accept an Excel **Laboratory** column as an alias for the legacy **Category** header when importing component libraries.
- Centralize physical and simulation defaults in `mooring/domain/physical_constants.py` (gravity, seawater densities, anchor safety factor, rope discretization, rope marking).
- Show 1-based segment numbers consistently in the component editor, drag-and-drop hints, and simulation segment table row headers.
- Label component editor fields with units for target depth and anchor ballast.
- Convert anchor dry library masses to submerged solver weights using displaced volume or library **Density (kg/m³)** instead of a hard-coded steel default.
- Show **Submerged mass (kg)** in the simulation summary as the apparent submerged weight calculated from dry mass, geometry, or material density.
- Rename the segment-results **Buoy (kg)** column to **Backup buoy (kg)** and leave it empty outside the recoverable branch, matching **Backup Profile** semantics.
- Wrap simulation **Segments** table column headers on multiple lines so labels stay readable when columns are narrow.
- Lay out the simulation **Summary** panel in two columns to reduce vertical space above the result tabs.
- Document anchor dry-mass library conventions and submerged-mass verification in integrated help.

### Fixed

- Convert workshop **Anchor dry mass (kg)** to selected/submerged summary values on legacy V1 imports, which previously skipped dry-to-apparent conversion when mass-sign inversion was active.
- Show **Selected anchor dry** and **Recommended anchor dry** in the simulation summary as dry masses in air, while **Submerged mass** stays as the apparent weight in water for the selected ballast.
- Format displayed mass values with one decimal place in the simulation summary, segment table, PDF report, anchor editor, and component tooltips.
- Show **Density (kg/m³)** and **Mass (kg, dry)** labels in anchor segment tooltips when those catalogue fields are available.
- Preserve anchor dry/submerged masses through simulation preprocessing so the summary **Submerged mass (kg)** field stays populated after a run.
- Resolve the project library cache from `library_source_path` when the stored SQLite path is missing or stale.
- Refresh legacy negative anchor masses from the updated catalogue when building simulation snapshots.
- Convert stale negative anchor catalogue signs to dry mass on V2 projects when density or geometry allows apparent-mass calculation.
- Treat an explicit **Anchor dry mass (kg)** value of zero as no selected ballast instead of falling back to catalogue submerged mass, so **Submerged mass** stays at 0 while **Recommended anchor dry** keeps the simulation guidance in air mass.
- Align top terminal sprites to the top of their row so mooring rings sit flush with the line above.
- Top-align cropped library anchor icons so rings sit near the top of palette thumbnails.
- Resolve imported JSON project library caches through portable repository paths instead of stale absolute `library_db_path` values.
- Unblock JSON project import GUI tests with a portable library fixture and stubbed library dock load.
- Stop `test_logger` from leaving a DEBUG stdout handler attached to the application logger after each run.
- Fix unsaved-project close confirmation calling a missing helper on exit.
- Align clamp-drop confirmation labels with 1-based segment numbering in the design workspace.
- Show a wait cursor while importing or reloading the component library.
- Highlight the full mooring segment row after startup, library reload, or workspace refresh.
- Avoid Qt paint-device crashes when exporting chart images to PDF reports.
- Restore PDF mooring figure and chart chapters after fixing rope-length formatting and chart offscreen export.
- Resolve anchor ballast from library mass when the stored project value is zero or unset, and report anchor inventory rows in kg instead of count.
- Show **Submerged mass (kg)** from dry-to-wet conversion using displaced volume or material density instead of repeating the dry mass entered in the editor.
- Prompt to save modified projects on exit so anchor ballast and other segment edits are not lost silently.
- Isolate launch-speed parity test from repository `Library.xls` resolution so Linux CI no longer compares simulations with mismatched catalogue data.

## [v2.0.11]

### Changed

- Remove root-level import facades and import application code directly from the `mooring/` package tree.
- Move `library_database.py` to `mooring/library/` and delete the unused legacy `simulation_solver_source.py` monolith.
- Move shared helpers, import utilities, domain rules, and Qt resource assets under `mooring/imports/`, `mooring/domain/`, `mooring/core/`, and `mooring/resources/`.
- Read the application release version from a root `VERSION` file through `mooring.core.version`.
- Bundle the root `VERSION` file in PyInstaller builds so frozen executables keep the same version source.
- Write debug log files to the user config directory as `{APPNAME}.log` and print the path when `-l` is used.
- Add configurable simulation max rope piece length in global configuration, show it in the simulation status bar, and document the commissioning-versus-report workflow in integrated help.
- Keep the Simulation tab active when selecting a segment on the mooring design view so chart exploration is not interrupted after a valid run.
- Show segment name and number in hover tooltips on Static Tension and Launch Tension charts.
- Highlight the rupture segment on the mooring design view while hovering Backup Profile points.
- Snap simulation chart hovers to the nearest visible point in screen space for more consistent tooltips and segment highlighting.
- Keep the last chart-hover segment selected when the cursor leaves the curve until another point is hovered.
- Show segment name, number, immersed length, time, and speed in Launch Speed chart hover tooltips.
- Highlight the segment entering the water on the mooring design view while hovering Launch Speed points.
- Added configurable `Rope marking tail (m)` in global configuration for clamp marking distances in the design view and PDF reports.

### Removed

- Drop completed refactor one-shot scripts and unrelated sample files from `tools/`.

### Fixed

- Fixed PyInstaller builds after the package refactor by collecting the `mooring` submodules required at runtime.
- Fixed main window startup when reading the configurable rope marking tail from global settings.
- Fixed rope marking distances on imported v1 projects so each rope segment restarts marking with the 2.6 m lead-in instead of using cumulative main-line depths.
- Fixed PDF rope marking tables to use the same per-rope marking logic as the design view.

## [v2.0.10]

### Added

- Added Linux arm64 release builds for Raspberry Pi 5 and other AArch64 Linux systems.
- Added horizontal scrolling on the design mooring view when the line exceeds the visible width (zoom, long labels, or two-column layout).
- Added iterative rope-stretch coupling in the static solver so equilibrium, tensions, and stretched geometry converge together.
- Added deployment anchor guidance in simulation outputs: min static, min deployment, recommended, and max structural weights, with warnings when the selected anchor sits outside the advised range.

### Changed

- Renamed simulation summary anchor labels to clarify operational meaning: recommended anchor replaces the former safe-anchor label, and the PDF now includes min static and min deployment weights.
- Updated in-app Help content (EN/FR) for v2.0.10: horizontal design scrolling, current-profile export, and deployment anchor guidance.
- Replaced the packaged `Readme.txt` with Markdown installation notes for release archives.

### Fixed

- Fixed macOS release packaging by preserving PyInstaller windowed app bundle generation.
- Added on-demand macOS Intel and Apple Silicon release build options while keeping macOS builds out of the default release matrix.

## [v2.0.9]

### Added

- Added CSV/TXT export for environmental current profiles.

### Changed

- Clarified component tooltips by displaying the technical family as `Component type` and the legacy Excel `Category` column as `Laboratory`.
- Aligned the sprite render lab with the main application component tooltip metadata labels.

### Fixed

- Removed duplicate `Name` entries from segment tooltips.
- Display `Visual Scale: undef` when the visual scale column is missing or empty.
- Improved message box contrast on Linux/WSL.
- Enabled simulation menu and toolbar actions whenever a project is available.
- Restored the missing primary curve legend label on the Launch Tension chart.

## [v2.0.8]

### Added

- Added recovery metrics for release ascent: head-of-line surface arrival time, average ascent speed, estimated head surface drift, and last recoverable float arrival time.
- Added project and author metadata to generated reports.

### Changed

- Bounded the Backup Profile to the recoverable branch above the release, including the release itself and excluding the lost ballast branch.
- Aligned V2 simulation charts with the legacy report conventions, including launch tension, launch speed, mooring profile, and backup profile behavior.
- Improved launch speed and launch tension modeling with progressive immersion and updated chart axes.
- Improved mooring profile rendering and PDF report layout, including rope length labels and multi-column report figures.
- Improved global depth settings by clarifying surface/bottom reference handling and making water depth optional for surface-reference projects.
- Improved library UI polish and project library loading behavior.
- Updated built-in help for recovery metrics, current profile persistence, depth reference behavior, charts, and reports.

### Fixed

- Fixed clamped overlay ordering by resolved target depth.
- Fixed legacy V1 import so saved water depth can be used as a bottom constraint.
- Fixed unsaved project state after legacy V1 import.
- Restored the max anchor weight display in the simulation UI and report.
- Fixed executable packaging for NetCDF4, cftime, certifi, and built-in help content.

## [v2.0.7]

### Added

- Added French built-in help content and a Help menu entry.
- Added print support for built-in help dialogs.
- Added French and English deployment `Readme.txt` files for installation and first use.
- Added selected segment position feedback in the status bar.

### Changed

- Improved built-in help coverage for workspace actions, component editing, simulation outputs, library usage, clamp markings, and default zoom.
- Improved project file opening and library resolution across project formats.
- Improved segment insertion and clamp handling in the workspace.
- Improved rope marking behavior by resetting marking distances at each rope segment.

### Fixed

- Warn before closing an unsaved project.
- Restore the selected segment after undo and reuse it as a drop fallback target.
- Fixed duplicated application name in the configuration file path.
- Fixed application configuration path handling.

## [v2.0.6]

### Changed

- Refined clamp rules and component editor behavior.
- Improved mooring profile chart offsets by using the bottom-referenced convention.
- Improved terminal sprite rendering for rings and chains in the mooring view.

### Fixed

- Fixed clamped depth display and preserved target depth edits.
- Added stale-results messaging when displayed simulation results are outdated.

## [v2.0.5]

### Added

- Added user feedback when top and bottom mooring length constraints are both applied.

### Changed

- Aligned launch model outputs and normalized simulation chart axes.
- Improved depth constraint feedback and balanced mooring layout columns.
- Matched mooring layout sprite proportions to segment sizes in the simulation mooring layout.
- Switched terminal rendering to real terminal sprites.
- Updated the default library loaded by the application.
- Added segment numbers in clamp dialogs.
- Renamed the application display name to MooringDesignSimulator.

### Fixed

- Fixed terminal row layout alignment.
- Fixed legacy V1 depth import to use positive target depths.
- Used legacy V1 water depth as a fallback bottom constraint during import.
- Fixed simulation result ordering and aligned row headers with line indexes.
