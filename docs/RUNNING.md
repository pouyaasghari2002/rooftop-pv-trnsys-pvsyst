# Reproducing the project

## TRNSYS

1. Make a working copy of `trnsys/TRNSYS_Files/` so a new run does not overwrite archived logs and outputs.
2. Open the desired Simulation Studio `.tpf` project: `a_IV_Curves`, `b_RadTemp`, `b_PVPower`, or `b_PVPower.monthly`.
3. Confirm component availability in your installation. The archived paths reference TRNSYS18.
4. Obtain a compatible `IR-Teheran-407540.tm2` weather file. It is referenced by the decks but is not included as a standalone dependency.
5. Update input-data and output paths in the project, then regenerate the deck if needed. The original paths point to the author's Windows installation.
6. Verify PV electrical parameters and coefficient units against the supplied catalog before accepting a new result.
7. Run the working copy, inspect the log, and save new outputs with application/component versions and settings.

The monthly-average deck uses 720-hour integration and printing intervals and divides integrated power by 720. Twelve blocks cover 8640 hours, not the full 8760-hour year. These are equal-duration averages rather than exact calendar-month energy totals.

## PVsyst

1. Use a compatible PVsyst installation. The supplied report records PVsyst 7.4.8.
2. Restore/import one project backup from `pvsyst/Files/` using PVsyst's project import workflow.
3. Restore the other backup separately: both ZIPs contain the internal filenames `HW1_c_Project.PRJ`, `HW1_c_Project.VC0`, and `Tehran_MN81_SYN.MET`.
4. Check module, inverter, site, weather data, orientation, near-shading scene, and module count before simulating.
5. Compare each restored design with the original eight-page report. Do not assume that the 21-panel narrative scene is the same as its 16-module exported variant.

The portrait and landscape labels come from the supplied archive filenames. The backups have not been opened in PVsyst during this conversion. Their MET data are not a direct substitute for the TRNSYS TMY2 dependency.

## Additional code

The supplied decks already contain equations and model connections. Add separately stored scripts under `code/`, including helper modules and required inputs. Document the actual language, dependencies, entry point, and output paths. Do not invent a dependency file or mark commands as tested until they have been verified.

## Technical checks

- Reconcile panel counts and saved variants before publishing a definitive final design.
- Resolve the negative cosine in the printed shadow-distance formulas using consistent solar-angle conventions.
- Treat quoted edge clearance as a source assumption; applicability to the actual roof was not established here.
- Separate power in W from energy in Wh or kWh.
- Keep original results distinct from any new runs or corrections.

No TRNSYS/PVsyst execution or experimental validation was performed during preparation of this package.
