# 👻 Lazy by Design - QGIS Plugin

A collection of **23 powerful Processing algorithms** for GIS workflows.

## 📊 Progress Report

| Status            | Version        | Lines of Code | Delta      | Load Time  | Notes                                               |
| ----------------- | -------------- | ------------- | ---------- | ---------- | --------------------------------------------------- |
| **Current** | v1.7.8         | —             | —          | —          | SCS Soils Polygonizer v1.2 added                    |
| Prior             | v1.7.7         | —             | —          | —          | DEFE v2.16 geometry artefact fix                    |
| Prior             | v1.7.6         | 28,059        | +481 LOC   | 0.035 secs | Smart Attribute Join v2.0 added                     |
| Prior             | v1.7.5-hotfix2 | 28,059        | +60 LOC    | 0.035 secs | Input path validation patch (DXF/DWG)               |
| **Current** | v1.7.5-hotfix1 | 27,999        | +563 LOC   | 0.035 secs | KML Exporter performance patch                      |
| Prior             | v1.7.5         | 28,059        | -2,255 LOC | 0.035 secs | Net reduction from diagnostic cleanup + SS refactor |
| Prior             | v1.7.4         | 30,314        | +2,321 LOC | 0.03 secs  | THE BEST TIME YET — that's optimisation lmao       |
| Prior             | v1.7.3         | 27,993        | +2,000 LOC | 1.3 secs   | Flawed update                                       |
| Prior             | v1.7.2         | 24,970        | +2,000 LOC | 1.235 secs | —                                                  |
| Prior             | v1.6.7         | 22,860        | +2,000 LOC | 1.4 secs   | Flawed update                                       |

Milestone: v1.6.6 crossed 16,000 lines of code (comments not included)

## 🚀 Installation

1. Copy the entire `lazy_by_design` folder to your QGIS plugins directory:

- **Windows**: `%APPDATA%\QGIS\QGIS3\profiles\default\python\plugins\`
- **Linux**: `~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/`
- **macOS**: `~/Library/Application Support/QGIS/QGIS3/profiles/default/python/plugins/`
- **(or the easy way, look at the How to install.gif)**

1. Enable the plugin:

- Go to **Plugins → Manage and Install Plugins**
- Find **"Lazy by Design"** in the **Installed** tab
- Check the box to enable it

1. Access the tools from the **Processing Toolbox** (Ctrl+Alt+T)

## 🛠️ Included Tools

| Tool                                              | Description                                                       | Group             |
| ------------------------------------------------- | ----------------------------------------------------------------- | ----------------- |
| 🌊 Multi-Point Watershed Delineation v7.2         | PCSWMM-style watershed analysis with timestamped layer groups     | Hydrology & Water |
| 🌊 Multi-Point Watershed Delineation v7.5 (Smart) | Intelligent resample-based watershed with hybrid pipeline         | Hydrology & Water |
| 🚑 Emergency Vector Edit Rescue v2.5              | Fix geometry issues in edit buffers (10 bug fixes)                | Vector Analysis   |
| 📄 Batch Map Layout Export                        | Parallel PDF/PNG/SVG export                                       | Map Production    |
| 📊 Spatial Weighting v2.5                         | AI-powered field matching and spatial analysis                    | Vector Analysis   |
| 🗺️ Raster Calculator                            | Max/Average with proper NoData handling                           | Terrain & Raster  |
| 🌿 DEFE (SA) v2.16 - Raster Soils                 | Metric intersection, reprojection repair, topology clean, 5 outputs | Hydrology & Water |
| ⛰️ DEM Terrain Boundary Extent v2.1             | Extract DEM boundary as polygon with sparse DEM gap fill          | Terrain & Raster  |
| 🌧️ DRESSA - Voronoi (SA)*                       | Rainfall Voronoi polygon analysis                                 | Hydrology & Water |
| 📋 Add XYZ Table                                  | Add X, Y, Z coordinate fields to layer                            | Data Management   |
| ⛰️ Warping (WGS84 to Project CRS)               | One-click terrain reprojection and clipping                       | Terrain & Raster  |
| 🖼️ Watercourse Buffer                           | 100m watercourse + 500m vlei/pan buffers                          | Hydrology & Water |
| ⛰️ Terrain Styler                               | Apply hillshade, terrain, and contour styles to DEM               | Terrain & Raster  |
| 🧹 Orphaned Data Cleaner                          | Clean and remove unused data from your project                    | Data Management   |
| 🚀 Advanced Catchment Report v2.6                 | Comprehensive hydrological analysis with popup modals             | Hydrology & Water |
| 📁 DXF/DWG Importer v3.3                          | Standalone CAD import with comprehensive attribute mapping        | Import & Export   |
| 🛰️ Multi-Source Imagery Downloader v3.5         | Download imagery with project CRS reprojection + GDAL pyramids    | Import & Export   |
| 🌍 Lazy KML Exporter v5.2-perf                    | Full-featured KML export with QGIS symbology + smart icons/colors | Import & Export   |
| 📦 Vector Tiles Downloader                        | Download and convert MVT/PBF vector tiles to standard vectors     | Data Management   |
| ⏹️ Polygon Overlay Merge                        | Overlay-priority polygon merge with optional dissolve             | Vector Analysis   |
| 🌧️ ERA5-Land Climate Data → Excel*             | Download historical climate data (1950-present) from Open-Meteo   | Climate & Weather |
| 🧠 Smart Attribute Join v2.0                    | Composite key join with conflict control and dry-run preview      | Vector Analysis   |
| 🚜 SCS Soils Polygonizer v1.2                   | Clip, polygonize and dissolve CWRR_TU_SCS_Class.tif               | Hydrology & Water |
| 🗄️ SS Group (optional)                          | Superseded scripts — toggle in Toolbar Settings (off by default) | Super-Seeded (SS) |

** **Backtracked** and rebuilt due to **an **error*

## 🎯 Key Features

### Smart Adaptive Processing (v7.5)

- **Intelligent Resource Analysis**: Automatically analyzes system RAM, CPU, and DEM properties before processing
- **Auto-Optimization**: Selects best processing engine (GRASS/SAGA/Native) or hybrid (SAGA + GRASS) based on data size
- **Dynamic Memory Allocation**: Uses **75% of available system RAM** (no arbitrary 4GB caps)
- **Dynamic Resampling**: Preserves full spatial extent while automatically scaling resolution to fit memory limits (replaces flawed circular clipping)
- **Graceful Warnings**: Warns about potential issues before processing starts
- **Auto-Adjustment**: Can automatically adjust parameters when system limits are exceeded

### Why Two Watershed Tools?

The plugin includes both the **Standard v7.2-v7.4** and **Smart v7.4+ (Resample)** tools:

1. **🌊 Standard (Precise)**:

- **Best for**: Small to medium datasets or pre-clipped DEMs.
- **Accuracy**: Processes at 100% original resolution with zero automated interference.

1. **🌊 Smart (Robust)**:

- **Best for**: Massive datasets (e.g., 200M+ cells) that typically crash QGIS.
- **Intelligence**: Automatically resamples resolution and uses a SAGA + GRASS hybrid pipeline.

> [!TIP]
> Use **Standard** for pre-clipped, manageable areas. Use **Smart** for giant DEMs where you need the tool to "just work".

### Geographic CRS Handling

- **Watershed Delineation v7.1**: Automatically detects when DEM is in geographic coordinates (lat/lon) and converts pixel sizes to meters for accurate area calculations
- **Auto-UTM Selection**: When working with geographic data, automatically selects the correct UTM zone for reprojection
- **Ellipsoidal Calculations**: Uses proper ellipsoidal area and length calculations for geographic CRS accuracy

### Folder Organization

- All outputs are automatically organized into logical folder structures in the QGIS layer tree
- Proper draw order (bottom to top) for overlapping layers
- Both merged and separate output modes supported

### File Output Support

- Optional permanent file outputs (GeoPackage, Shapefile, etc.) while maintaining folder organization
- Memory layers for quick visualization
- Seamless integration with QGIS project structure

## 📝 Version History

### 1.7.8 (2026-04-29)

> **SCS Soils Polygonizer v1.2**

> **Code Stats:** `+771` lines / `-22` lines (Net: `+749`)

**🚜 SCS Soils Polygonizer v1.2**

- NEW: Standalone utility extracted from DEFE (SA) v2.4 to clip, polygonize and dissolve CWRR_TU_SCS_Class.tif.
- Features: Handles Auto UTM detection for metric buffering, Water -> D (Water) remap, Post-polygonize VAT join, Null SCS nearest-neighbour backfill, and more.
- Includes 3 clip modes: No clip (full raster extent), AHR clip (+ buffer), Map canvas extent clip.

---

### 1.7.7 (2026-04-28)

> **DEFE v2.16 — Geometry Artefact Fix**

> **Code Stats:** `+3,013` lines / `-285` lines (Net: `+2,728`)

**🌿 DEFE (SA) v2.16 — Raster Soils**

- Fixed: Intersection crash caused by invalid geometries created during reprojection to metric UTM — `fix_geometries()` now runs immediately after every `reprojectlayer` call before intersection
- Fixed: `native:intersection` now uses `INVALID_FEATURES_FILTERING=1` to skip remaining invalid features instead of aborting
- Fixed: Dimensional filter was applied in degree-space (0.5° ≈ 55 km) — all geometry work now kept in metric CRS throughout the intersection pipeline
- Added: Topology clean (shrink-dissolve-grow) — 1cm negative buffer collapses zero-width shared edges, dissolve merges identical neighbours, 1cm positive buffer restores area
- Added: Dimensional guard — `min(bounds_width, bounds_height) > 0.5m` filter applied after every critical step
- Added: Pre-dissolve option — merge same-value raster polygons before intersection to prevent slivers
- Final result reprojected back to NLC CRS for alignment

---

### 1.7.6 (2026-04-28)

> **Smart Attribute Join v2.0**

> **Code Stats:** `+1,069` lines / `-29` lines (Net: `+1,040`)

**🧠 Smart Attribute Join v2.0**

- NEW: Composite key matching — join on 2, 3, or more fields simultaneously
- NEW: Explicit field selection — choose exactly which source fields transfer, or leave blank to auto-detect all shared + new fields
- NEW: Three conflict policies — Keep Target / Always Overwrite / Fill NULLs only
- NEW: Keep or drop unmatched target features
- NEW: Dry Run mode — full per-feature preview in the log before writing any output
- NEW: Type-mismatch warnings and duplicate key detection
- Registered under 📊 Vector Analysis group with standard + cyberpunk icons

---

### 1.7.5-hotfix2 (2026-04-22)

> **DXF/DWG Importer — Input Path Validation Hotfix**

> **Code Stats:** `+3,661` lines / `-2,562` lines (Net: `+1,099`)

**📁 DXF/DWG Importer v3.3-hotfix2**

- Fixed: File path entered as Output Folder silently fell back to memory layer — now raises a clear error before processing starts
- Fixed: File path entered as Batch Folder produced a confusing "no file selected" error — now explicitly tells the user what's wrong
- Fixed: File path entered as Converted DXF Folder caused silent save failure — now detects and falls back to DWG's own folder with a warning
- Fixed: Non-existent output folder raised an exception — now auto-created with `os.makedirs()` and confirmed in the log
- Fixed: Folder path entered as Single File input produced a misleading "unsupported type" warning — now directs user to the Batch Folder field
- Fixed: Read-only output folder and write failures now explicitly state "returning memory layer instead" with the attempted path

---

### 1.7.5-hotfix1 (2026-04-22)

> **KML Exporter Pro — Google Earth & QGIS Performance Hotfix**

> **Code Stats:** `+3,119` lines / `-2,556` lines (Net: `+563`)

**🌍 Lazy KML Exporter v5.2-perf**

- Fixed: Google Earth crash/hang on KML open — `LabelStyle` scale set to `0` (hidden by default), `StyleMap` normal/highlight pair added, `<Region>` + `<Lod>` injected into `<Folder>` for viewport culling (BUG-001)
- Fixed: QGIS crash/hang exporting large high-vertex shapefiles — renderer symbols pre-cached before feature loop (constant-time lookup replaces O(n — categories) Python work), placemarks streamed to temp file instead of accumulated in RAM, Douglas-Peucker simplification (`tolerance=0.00005`) applied before vertex serialisation (BUG-002)
- Fixed: Guaranteed `NameError: name 'kml_lines' is not defined` at end of every export — stale list-join line removed (BUG-003)

---

### 1.7.5 (2026-04-14)

> **DEFE v2.4 Raster Soils, SS Group & Batch Export Font Fix**

> **Code Stats:** `+2,890` lines / `-2,498` lines (Net: `+392`)

**🌿 DEFE (SA) v2.4 — Raster Soils**

- Replaced vector soils input with raster soils (`CWRR_TU_SCS_Class.tif` + VAT)
- Added 5 named intermediate outputs for full traceability at each processing stage
- Added post-union null SCS backfill via spatial overlay + nearest-neighbour fallback — eliminates sliver polygons caused by null attributes surviving the dissolve
- Added `Water → D (Water)` remap in SCS class field
- Old v2.2 moved to Super-Seeded (SS) group for reference

**🗄️ Super-Seeded (SS) Group**

- Added optional SS group in Processing Toolbox (disabled by default)
- Toggle via Toolbar Settings → Super-Seeded Scripts section
- Exposes superseded algorithm versions without cluttering the main toolbox

**📄 Batch Map Layout Export v9.3**

- Fixed label text wrapping in parallel export — GDI vs DirectWrite font metric correction (ratio 81.28/90.00 applied to renderContext DPI before refresh)
- Fixed `QGIS_CUSTOM_CONFIG_PATH` path level — was pointing to `profiles\` instead of `QGIS3\`, causing path doubling and wrong profile resolution
- Profile fonts now load correctly in worker processes (384 font families confirmed)
- Removed all diagnostic print statements from production build
- Legend symbol sizing difference (subtle, ~10% wider in parallel) documented as Qt 5.15 limitation — suspended after 20 fix attempts

---

### 1.7.4 (2026-04-07)

> **Geometric Logic & Performance Synthesis Update**

> **Code Stats:** `+3,104` lines / `-623` lines (Net: `+2,481`)

**⏹️ Polygon Overlay Merge v1.1**

- **Overlay Mechanic**: Implemented a priority-based spatial merge that erases underlay geometries within the overlay zone, preserving full attribute schemas.
- **Visual Stencil**: Designed frosted glass standard and dotted cyberpunk icons to visually communicate the "selection-cut" operation.

**? Performance Optimization**

- **Watershed Resample Logic**: Refactored `watershed_delineation.py` to prune redundant logic blocks, resulting in a cleaner code footprint and a record-breaking **0.03s** initial load time.
- **Header Synthesis**: Updated global metrics to reflect the new **30,314 LOC** total.

---

### 1.7.3 (2026-03-25)

> Spatial Weighting & Tool Reliability Patch

> **Code Stats:** `+2,150` lines / `-1,450` lines (Net: `+700`)

**📊 Spatial Weighting v2.5**

- Fixed: Overwrite target fields dropdown now correctly displays target layer fields instead of source fields.
- Fixed: Added 'cn' and comprehensive aliases to curve number canonical dictionary category.

**🛠️ Stability & Rendering Updates**

- Watershed Delineation v7.1: CRS auto-reprojection fixes and cell area approximations to prevent GRASS threshold overflow.
- Emergency Vector Edit Rescue v2.5: Implemented actual `makeValid` geometries cascade and slim-polygon filter natively in buffer.
- Batch Layout Export: Resolved broken raster rendering integration during PDF outputs.
- Parallel Raster Calculator: Implemented strict chunk boundary alignment and intermediate temporary cache compression.

---

### 1.7.2 (2026-03-18)

> ***Visual & UX Synthesis****** — ******I—m tired, boss***

> **Code Stats:** `+3,206` lines / `-540` lines (Net: `+2,666`)

- **Premium Icon Phase 3**: Completed the glassmorphism redesign for the entire hydrology and data suite. Every tool now features a unified design language with bold `#2c3e50` borders and high-fidelity frosted textures.
- **Settings ****Dialogue**** v2.0**:
- **Cyberpunk Overhaul**: The "About" section is now a dark, immersive netrunner terminal theme (`0d1117`).
- **Relic Malfunction**: New immersive engram-style easter egg triggered via the ghost mascot.
- **Sign-off Logic**: "Jack Out" exit system with randomised Night City farewells.
- **UX Row-Selection**: Clicking any row in the algorithm selection list now toggles the checkbox; no more need for precise 16px clicks.
- **Checkbox Connectivity Fix**: Resolved a state conflict where clicking the 16px checkbox directly failed to toggle (Bug #0033); both row-text and checkboxes now function reliably.
- **DEFE (SA) v2.2 Additions**: Added HEC-RAS fields (NIMPERV, NPVERV, NPERV, DSIMPERV, DSPERV, ZEROIMPERV, ID_32) for improved compatibility with HEC-RAS 32-character identifiers.
- **DEM Terrain Boundary Extent v2.1**: Upgraded to handle sparse/contour DEMs via auto-buffer gap fill, auto-resampling, and dynamic NoData reading.

---

### 1.7.1 (2026-03-18)

> Core Stability & Under-the-Hood Overhaul
> **Code Stats:*** *`+2,676`* lines / *`-323`* lines (Net: *`+2,353`*)*
> **🛠️ Core Stability Update** — CRITICAL UPDATE**

- **Robust Pathing (Parallel Tools)**: Replaced hardcoded QGIS installation paths with dynamic detection. The tools now resolve `python-qgis.bat` relative to the **active QGIS process**, ensuring parallel processing works seamlessly regardless of folder versioning (e.g., QGIS 3.44 vs 3.38).
- **Dynamic CRS Defaults**: Standardized on `'ProjectCrs'` as the default for Raster Calculator, CAD Importer, Warping, and Add XYZ tools. This eliminates the "WGS84 trap" where tools default to lat/lon instead of the user's active map context.
  **🎨 Icon Refresh Phase 2**
- **Vibrant & Professional**: Finalized the redesign of `batch_export.svg` (premium paper stack + vivid export arrow) and `raster_calc.svg` (new 2x3 pixel-grid visualization replacing the abstract plus sign).
- **User Preference Alignment**: Tuned `add_xyz.svg`, `voronoi.svg`, and `catchment_report.svg` to retain their specific "identifiable" symbols (e.g. the addition '+' for table data and the vivid rain cloud) while boosting overall color vibrancy.

---

### 1.7.0 (2026-03-18)

> DEFE Area_km2 Calculation Fix & Spatial Weighting Fixes
> **Code Stats:*** *`+640`* lines / *`-32`* lines (Net: *`+608`*)*
> **🌿 DEFE (SA) v2.2**

- Fixed: Area_km2 calculation was previously happening before the dissolve step, resulting in artificially tiny area values (e.g. `0.000801` instead of `5.593`). Moved the Area_km2 field calculation to happen after the dissolve step so that the area correctly represents the total area of the dissolved geometries.
  **📊 Spatial Weighting v2.5**
- Fixed: "Target fields to overwrite" dropdown failing to show actual target layer fields. Overwrite mode now correctly reflects target polygon fields natively.
- Fixed: "Preview/Dry Run" mode wrongly running extensive geometry repair. Dry runs now explicitly bypass `native:fixgeometries` to instantly show field mapping evaluation strings.
  **🌧️ DRESSA - Voronoi (SA) v1.0**
- Fixed: CRS projection pitfall in UTM calculation (now safely reprojects to WGS84 before detecting zone).
- Fixed: Layer grouping logic to prevent duplicate "ghost" layers on repeated runs; uses new `QgsProcessingLayerPostProcessorInterface` for clean renaming and stale layer eviction.
  **🔌 Toolbar / Core**
- Added: Split DWG / DXF canvas drop handler preferences. Users can natively choose whether QGIS intercepts `.dwg` or `.dxf` Drops directly (prevents the QGIS native unsupported format error gracefully).
- **🎨 Icon Design Refresh v2.0**: Re-designed all 21 plugin icons (`.svg`) for maximum professionalism and visibility.
- Standardized on rounded square bases with vibrant, high-contrast overlay symbols.
- Fixed dimensional clipping in `watercourse_buffer.svg` and `spatial_weighting.svg`.
- Re-themed `raster_calc.svg`, `add_xyz.svg`, and `batch_export.svg` with modern, vibrant palettes (replacing muted/black-heavy designs).
- Unified stroke weights (1.5px) and 24x24 ViewBox across the entire toolkit.

---

### 1.6.9 (2026-03-17)

> Toolbar Fixes & Canvas Drop Handler
> **Code Stats:*** *`+720`* lines / *`-12`* lines (Net: *`+708`*)*
> **Toolbar**

- Fixed: All algorithm IDs corrected to match exact `name()` returns — watercourse buffer, warping, add xyz table, and DEM extent were all silently broken
- Fixed: `_make_run_handler` now uses `algorithmById()` directly with a clean name-match fallback — no more silent click failures
- Added: Canvas-level DWG/DXF drop handler — drop a `.dwg` or `.dxf` file onto the QGIS map canvas to auto-open the DXF/DWG Importer with the file pre-filled
- Added: "Hide settings gear button" option in the settings dialog
- Added: "Enable DWG/DXF canvas drop" toggle in the settings dialog
- Removed: DWG drop zone from settings dialog (replaced by canvas-level handler)
- Redesigned: `defe_sa.svg` (4-patch land cover mosaic), `voronoi.svg` (rain cloud + Voronoi cells), `watershed_smart.svg` (bowl basin + lightning bolt)

---

### 1.6.8 (2026-03-17)

> DEFE v2.2 Critical Bug Fixes
> **Code Stats:*** *`+550`* lines / *`-15`* lines (Net: *`+535`*)*
> **🌿 DEFE (SA) v2.2**

- Fixed: UTM zone detection failed when AHR was in a projected CRS (e.g. ESRI:102568) — `get_utm_zone()` now reprojects the AHR center to WGS84 before calculating the UTM zone, producing a valid EPSG code.
- Fixed: `QgsSpatialIndex.SpatialIndexNotPresent` attribute error on QGIS 3.44 — replaced with unconditional try/except index creation.
- Fixed: `gdal:cliprasterbymasklayer` caused a "File too large regarding tile size" GDAL error — replaced with `gdal:cliprasterbyextent` using the buffer bounding box, matching the original working model approach.

### 1.6.7 (2026-03-17)

> *Spatial Weighting v2.5 Update** — complete overhaul**, optimisation** bug features**,** **etc.*
> **📊 Spatial Weighting v2.5**

- **Geometry Fixes**: Invalid geometries now repaired BEFORE any processing (via native:fixgeometries preprocessing step)
- **Compatibility Fix**: Fixed `isvalid()` bug that caused failures on newer QGIS versions due to QGIS source iteration rejecting invalid features.
- **Smart Mapping**: Comprehensive PCSWMM dictionary mappings with typo tolerance.
- **Preview & Override**: Added Preview/Dry Run mode for reviewing matches before processing, and a Manual Override system for field mapping corrections.

### 1.6.6 (2026-03-04)

> **The "Lazy User" Update (API & CAD Overhaul) — I want rusks. Did I ever mention I like rusk and we have none here — **imagine sad*
> **🌧️ ERA5-Land Climate Data (v2.2)**

- **Expanded Date Range**: Added ERA5 archive support (25 km) for 1940—1949, seamlessly merging with ERA5-Land (10 km) starting in 1950.
- **Enhanced Outputs**: Excel files now include **Latitude, Longitude**, and a **Data Source** column (to verify ERA5 vs ERA5-Land usage).
- **Proactive Quota Estimator**: Added a real-time console breakdown of "equivalent calls" and daily capacity based on your selected variables and date range.
- **Variable Expansion**: Added **Tmax/Tmin** (daily max/min temperature) to the download catalogue.
- **Optimised**** API Strategy**: High-efficiency single-call paradigm with recursive timeout fallback.
- **Smart Rate Limiting**: Robust sliding-window limiter enforcing triple ceilings (600/min, 5,000/hr, 10,000/day) with exponential backoff.
  **📁 DXF/DWG Importer (v3.3 Pro)**
- **Dual-Converter Engine**: Cascading strategy using **LibreDWG** (Primary) with **ODA File Converter** (Fallback).
- **Auto-Detection**: Automatically finds ODA File Converter in standard installation paths across Windows, macOS, and Linux.
- **Improved Batch Mode**: Enhanced support for recursive folder scanning with mirrored output directory structure.
  **📦 Vector Tiles Downloader**
- **QGIS 3.44.6+ Stability**: Fixed legend grouping crashes and optimised main-thread execution patterns.
- **Rich Documentation**: Completely redesigned help interface with segmented features, visual workflow, and pro tips.
  **🌊 Shared Improvements**
- Unified "Import & Export" group logic for consistent tool location in the Processing Toolbox.
- *Overall **o**ther:**Many other minor tweaks **are **not worth mentioning here.*

### 1.6.5 (2026-03-04)

> The "Complete Output" Update (Watershed v7.5) - thanks, Beth, for finding the bugs... so happy lol, and yes, it needed this detail dev log update
> **Zero Third-Party Dependencies**** *****(******I forgot my****** ******.******env****** has lots of cool things******,****** which I take for granted******,****** my bad******)***

- Removed `psutil` dependency entirely
- Native RAM detection via `ctypes` (Windows), `/proc/meminfo` (Linux), `os.sysconf` (macOS)
- Automatic fallback to conservative defaults (8GB/4GB) if detection fails
- CPU core count detected natively across all platforms
  **Full Output Suite Now Actually Works**
- Fixed many critical bugs where subbasins, streams, and junctions were never extracted
- All 5 output layers are now correctly generated per basin:
- → Watershed Basin (polygon)
- → Subbasins (polygons)
- → Stream Networks (lines)
- → Stream Junctions (points)
- → Snapped Pour Points (points)
  **Proper Stream Centerlines**
- Stream vectorization now uses GRASS `r.thin` + `r.to.vect` for true centerlines
- The old method produced cell outlines (rectangle edges), not actual stream paths
- Automatic fallback to `polygonstolines` if GRASS thinning fails
  **🐛 Bugs Fixed**

| Bug                                                                 | Impact                                                                     | Fix                                                                                                 |
| ------------------------------------------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Subbasins/streams/junctions never extracted from r.watershed output | Only basin + pour point were created — users got 2 layers instead of 5    | Added `_extract_subbasins`, `_extract_streams`, `_extract_junctions` methods called per-basin |
| GDAL clip failed silently with memory layers                        | `cliprasterbymasklayer` requires a file path, not a QGIS memory layer ID | Basin polygon now materialised to GeoPackage before clipping                                        |
| Stream raster filter rejected valid streams                         | Expression `"value" = 1` missed stream segment IDs (1, 2, 3...)          | Fixed to `"value" > 0 AND "value" != 255 AND "value" != -9999`                                    |
| Junction tolerance was 1.0 map units                                | For geographic CRS, 1.0— = ~111 km — every endpoint became a "junction"  | CRS-aware tolerance: 1m (projected) / ~0.00001— (geographic)                                       |
| Junction detection O(n—) performance                               | Slow on dense stream networks                                              | Replaced with grid-bucket spatial hashing (O(n))                                                    |
| No explanation when outputs were missing                            | Users saw 2 layers and had no idea why                                     | Clear per-point and summary reporting with parameter recommendations                                |
| Threshold too aggressive after resampling                           | 0.25m DEM resampled to 0.5m still produced threshold of 2M cells           | Threshold calculation now correctly uses effective (post-resample) cell area                        |

**Improved Reporting**

- **Per-Point Diagnostics**: When a basin produces fewer outputs than expected, the log now explains exactly why

### 1.6.4 (2026-03-04)

> The "Never Clip" Update (Intelligent Resampling)

- **OVERHAUL: Dynamic Resampling Paradigm (Watershed v7.4)**
- Replaced the flawed circular clipping logic (which truncated upstream catchments) with **Intelligent Dynamic Resampling**.
- Full spatial extent of the DEM is now preserved, while resolution is automatically scaled (e.g. 0.25m → 0.5m) to fit memory limits.
- **NEW: Hybrid Processing Pipeline (SAGA + GRASS)**
- Implemented a more robust end-to-end engine-aware pipeline.
- Uses SAGA `catchmentareaparallel` (multi-threaded) for high-performance flow accumulation on massive rasters.
- Falls back to GRASS for drainage and stream extraction on the resampled data.
- **IMPROVED: Memory & Stability**
- Removed arbitrary 4GB memory caps — now dynamically allocates based on **75% of actual available system RAM**.
- Enabled GRASS `-m` (memory-efficient) flag by default for disk-backed processing on large datasets.
- Full cascading engine fallback chain (SAGA <-> GRASS) for every processing stage.

### 1.6.3 (2026-03-04)

> Massive DEM Stability Fixes

- **FIXED: Native Engine Limitation & GRASS Hanging**
- Resolved issue where GRASS tools were incorrectly called for >100M cell DEMs even when NATIVE engine was selected.
- Added "Engine-Aware" sink filling to respect user/auto strategy selection.
- **FIXED: `UnboundLocalError` in `_analyze_dem`**
- Corrected variable scope error for `cell_size_x_m` in projected CRS workflows.
- **IMPROVED: Resource Detection**
- Refined `psutil` integration for more accurate RAM and CPU core detection.

### 1.6.2 (2026-03-03)

> *Consolidated groups for better organization** (pushed in this version)*

- **IMPROVED: Group Consolidation (13 → 7 groups)**
- 🌊 Hydrology & Water (5 algorithms): Watershed, Catchment Report, DRESSA, Watercourse Buffer, DEFE
- ⛰️ Terrain & Raster (4 algorithms): DEM Boundary, Warping, Terrain Styler, Raster Calculator
- 📊 Vector Analysis (2 algorithms): Spatial Weighting, Emergency Vector Rescue
- 📋 Data Management (3 algorithms): Add XYZ, Orphaned Data Cleaner, Vector Tiles Downloader
- 🌍 Import & Export (3 algorithms): DXF/DWG Importer, KML Exporter, Imagery Downloader
- 🌧️ Climate & Weather (1 algorithm): ERA5-Land Climate Data
- 📄 Map Production (1 algorithm): Batch Layout Export

### 1.6.1 (2026-03-03)

> Better dependency error messages

- **IMPROVED: ERA5-Land Climate Data → Excel**
- Enhanced dependency error messages with multiple installation options
- Clearer instructions for pip install commands

### 1.6.0 (2026-03-02)

> Vector tiles and climate data made easy

- **NEW: Vector Tiles Downloader (MVT/PBF → Vectors)**
- Download and convert XYZ vector tiles to standard vector layers
- Full attribute preservation with proper type handling (int, float, bool, string)
- Automatic geometry type separation (points, lines, polygons)
- Smart layer grouping by semantic category (Transport, Water, Buildings, etc.)
- Deduplication of overlapping features from adjacent tiles
- Optional clipping to AOI polygon boundary
- Style-aware filtering (exports only visible layers at chosen zoom)
- Output CRS matches current Project CRS
- Uses only QGIS built-ins - no pip installs required
- **NEW: ERA5-Land Climate Data → Excel**
- Download historical climate data from Open-Meteo (1950-present)
- One Excel file per feature with daily data and monthly climatology sheets
- 11 climate variables: temperature, precipitation, wind, soil moisture, ET0, etc.
- Point and polygon support (with grid sampling for spatial averaging)
- Automatic date range chunking for large requests
- Progressive rate limiting with retry logic
- Requires: pandas, openpyxl (pip install pandas openpyxl)

### 1.5.9 (2026-02-27)

> KML exporting should not be this hard, so I made it lazy

- **NEW: Lazy KML Exporter Pro v5.0**
- Full QGIS symbology export (colors, transparency, line widths)
- Smart Icon Matching: per-feature icons from attribute field ("donut", "star", "pushpin red")
- Smart Color Matching: hex codes, named colors ("red", "blue"), or auto-category grouping
- 30+ Google Earth icon shapes with case-insensitive alias matching

### Why the version jump?

> *This update includes a range of theoretical explorations, plugin refinements, and performance **optimisation**. While these improvements are significant in terms of development effort, they do not always result in user-facing features** **(so many **behind-the-scenes** changes)** that would typically warrant a detailed version log. Below are **some of **the key updates** and dev log**:*

- Field Selection: Export all attributes or handpick specific fields for greater flexibility.
- ExtendedData Export: Enhanced compatibility with Google Earth/Maps popups, ensuring seamless data visualisation. (for the KML exporter novel script)
- Automatic CRS Reprojection: All exports now automatically reproject to WGS84, improving interoperability.
- Vector Downloader: A novel approach, inspired by the image downloader script, was theorized and successfully implemented.
- KML Exporter: Developed to overcome QGIS limitations, automating symbol and ID handling that previously required manual intervention.
- 0.25m LiDAR Dataset Processing: Through troubleshooting, a novel approach for handling high-resolution LiDAR data was developed. The underlying algorithms, their limits, and the specific circumstances for optimal performance were thoroughly tested and documented.

### 1.5.8 (2026-02-23)

> The fix was relative to one's IQ (mine was low this morning) - pain

- **FIXED: DXF/DWG Importer v3.3**
- Fixed numerical rounding not working in bulk mode

### 1.5.7 (2026-02-23)

> I want to know why we don't have Rusk in the office. I cry

- **UPDATED: DXF/DWG Importer v3.3**
- **Bulk Processing:** Added bulk `.dxf`/`.dwg` file processing
- **Known Bug:** Numerical rounding not working in bulk mode

### 1.5.6 (2026-02-23)

> Starting the week on a high note, lol it's a Monday, save me.

- **UPGRADED: Multi-Source Imagery Downloader v3.5.0**
- Added CDNGI source via the Apollo endpoint
- **UPDATED: DXF/DWG Importer v3.2**
- Added disclaimer requiring users to verify Z values

### 1.5.5 (2026-02-20)

- **UPGRADED: Multi-Source Imagery Downloader v3.4.0** — 10 Major Improvements
- **Performance (P1-P3):**
- P1: GDAL pyramids built automatically for instant rendering at any zoom
- P2: 5x faster tile downloads (100 req/s vs 20 req/s) with true rate limiting
- P3: 50% faster health checks (single GET vs HEAD+GET)
- **Correctness (C1-C3):**
- C1: → **Project CRS reprojection** - outputs match your project CRS automatically
- C2: Pre-flight tile validation prevents wasted downloads
- C3: Proper ipaddress module usage
- **User Experience (U1-U2):**
- U1: Attribution metadata embedded in GeoTIFF
- U2: Real-time WMS download progress
- **Code Quality (Q1-Q2):**
- Q1: Removed unused imports
- Q2: Optimized location lookup table
- **UNIFIED: DXF/DWG Importer v3.2**
- Consolidated two versions into single optimized script
- GDAL error suppression for cleaner output
- Enhanced attribute mapping and progress feedback
- Better memory efficiency for large datasets

### 1.5.4 (2026-02-19)

- **NEW: Multi-Source Imagery Downloader v3.3.7**
- Download georeferenced imagery from 7 global sources
- Automatic source fallback if primary fails
- Smart layer naming with source + location + resolution
- Parallel tile downloading for speed
- Proper CRS handling and validation
- **IMPROVED: DXF/DWG Importer v3.1 PRO**
- Optimized Z-value extraction for all geometry types
- Enhanced attribute transposition logic
- Better memory efficiency for large datasets

### 1.5.3 (2026-02-19)

- **Advanced Catchment Report v2.6** — Critical Unicode Fixes & UI Polish
- FIXED: CSS content property now uses proper CSS unicode escapes (e.g. `\2139`) instead of HTML entities, fixing broken icons in PDF exports.
- FIXED: Removed raw 4-byte emojis from source code to resolve `UnicodeEncodeError` on Windows systems.
- IMPROVED: Detailed interpretation bullets moved to interactive popup modals (`showDetail`) for a cleaner report.
- CHANGED: Removed opinionated hydrological model suggestions from interpretation text.

### 1.5.2 (2026-02-19)

- **Emergency Vector Edit Rescue v2.5** — Patched release with 10 bug fixes:
- FIXED: Tool slowdown on layers with complex/nested GeometryCollections (unnecessary instance copies removed)
- FIXED: Cancel button sometimes failed to stop processing (overly broad exception handling)
- FIXED: Progress bar stuck at 0% on small layers or jumping ahead on large layers
- FIXED: QGIS UI freeze when layer had large number of pending deletions (log output truncated)
- REMOVED: Unused geometry caching system that wasted memory
- IMPROVED: Cheap O(1) checks run before expensive GEOS validity check
- ADDED: RAM usage warning every 50,000 features loaded
- IMPROVED: Exploded feature IDs now clearly labelled as temporary edit-mode IDs
- FIXED: Geometry type validation now uses correct enum reference values
- FIXED: Provider capability check now uses class-level lookup

### 1.5.1 (2026-02-18)

- Watershed Delineation v7.2: Replaced `postProcessAlgorithm` with direct layer tree manipulation
- NEW: Timestamped group folders (e.g. "🌊 Watershed Delineation [11:45:12]") — each run gets its own group
- ADDED: `FlagNoThreading` for robust, race-condition-free layer organization
- IMPROVED: ~300 lines of state-tracking code removed for cleaner, faster execution
- FIXED: DXF/DWG Importer no longer uses emoji in `displayName` (uses QGIS theme icon instead)
- ADDED: Custom icon for DXF/DWG Importer algorithm
- FIXED: Layer stacking order — Pour Point (#1) on top, Watershed Basin (#5) on bottom

### 1.5.0 (2026-02-18)

- ADDED: 📁 DXF/DWG Importer & Geometry Organizer (v3.1 PRO)
- Standalone DWG conversion via LibreDWG (no ODA required)
- One-time consent-gated download for conversion binary
- Automatic geometry separation (Points/Lines/Polygons)
- CAD attributes and Z-elevation extraction support

### 1.4.4 (2026-01-28)

- Batch Layout Export - UI Responsiveness Patch
- FIXED: Critical UI freeze during parallel export operations
- ADDED: Reentrancy guard to prevent concurrent execution attempts
- OPTIMIZED: Event loop yielding via processEvents() injection
- REDUCED: I/O polling frequency by 80% (100ms → 500ms)
- ENSURED: Cleanup guarantee with finally-block flag reset
- VERIFIED: Full backward compatibility, zero export regression

### 1.4.3 (2026-01-22)

- Spatial Weighting v2.0 - Ultra-Optimized
- ENHANCED: Smart CRS detection with auto UTM zone calculation
- REINFORCED: Comprehensive input validation with field type checking
- OPTIMIZED: Spatial indexing for both source and target layers
- IMPROVED: Grid-based intersection for precision and performance
- ADDED: Configurable decimal rounding for PCSWMM compatibility
- ENHANCED: Better progress feedback with processing statistics
- Streamlined: Maintains O(1) caching and vectorized operations
- DRESSA - Voronoi (SA) v1.0 - Ultra-Optimized
- ENHANCED: Smart CRS detection with auto UTM zone calculation
- OPTIMIZED: Metric buffering (3000m) even when AHR is in WGS84 degrees
- REINFORCED: Input validation with required field checks (X, Y, 100_24hr)
- IMPROVED: Grid-based intersection for precision and performance
- ADDED: Dual area fields (m— and hectares) for reporting flexibility
- Streamlined: 13 steps with spatial indexing at 4 critical stages
- DEFE (SA) v3.0 - Production Ready with critical fixes
- FIXED: Removed forced EPSG:4326 assignment on soils layer (prevents data shifting)
- OPTIMIZED: Dissolve happens BEFORE Area % calculation (100x faster on large datasets)
- REINFORCED: Better CRS handling with proper reprojection from source CRS
- ENHANCED: Added input validation and progress feedback
- IMPROVED: Uses gdal:cliprasterbymasklayer with LZW compression and multi-threading
- Streamlined workflow: 11 steps instead of 17 for better performance
- Watercourse Buffer v1.0: Complete rewrite with proper sink handling for flexible file/temporary outputs
- Fixed CRS detection and reprojection logic for accurate meter-based buffering
- Improved reservoir filtering with better field handling
- Enhanced step-by-step progress reporting with detailed feedback
- Added proper error handling and validation
- Critical Fix: Geographic CRS handling in Watershed Delineation v7.1
- Fixed massive threshold values when using lat/lon DEMs
- Auto-detects UTM zone and reprojects geographic data
- Proper cell area calculation using latitude-corrected meter conversion
- Threshold overflow protection with sensible limits
- Ellipsoidal area/length calculations for geographic CRS accuracy

### 1.4.0 (2026-01-20)

- Multi-Point Watershed Delineation v7.0: Improved layer organization with proper folder structure for both merged and separate modes
- DEFE (SA) v2.1: Fixed CRS handling for accurate meter-based buffering regardless of input CRS
- Multi-Point Watershed Delineation v7.0: Now create organized folder structures in QGIS layer tree
- Added optional file output support while maintaining folder organization
- Layers appear in correct draw order (bottom to top) Note: DEFE (SA) v2.1 is a known bug for ordering outputs

### v1.3.0 (2026-01-20)

- Improved portability: Updated `Terrain Styler` and `Watercourse Buffer` to use relative style paths.
- Plugin is now fully self-contained for easier packaging and distribution.

### v1.2.0 (2026-01-19)

//Data lost for the prior script, thus had to rebuild 1.1.0 resulted in improved scripts

### v1.1.0 (2026-01-19)

- Added 6 new algorithms: DEFE, DEM Boundary, DRESSA Voronoi, Add XYZ, Warping, Watercourse Buffer
- New emoji groups: Terrain, Rainfall, Data, Land Cover, Layout
- Custom icons for all algorithms

### v1.0.0 (2026-01-19)

- Initial release
- Bundled 5 processing algorithms
- Ghost emoji branding 👻(I like this emoji, I do indeed)

## 📜 License

Overlord minion License — Welcome, fellow minion, may your travels be safe!

## 👤 Author

**Lazy by Design (Sheldon Willie)**
