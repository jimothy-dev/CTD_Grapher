# CTD Profile Grapher
 
A Google Colab notebook for visualizing multi-station CTD cast profiles from Sea-Bird `.cnv` files. Supports both the **UW-Tacoma** and **UW-Friday Harbor** CTD instrument setups. The tool reads station data from a user-prepared `.xlsx` file in Google Drive, plots depth profiles for oceanographic variables with all stations overlaid on each graph, and saves the figures as a PDF back to Google Drive.
 
---

## Example Data
 
The following example files from Quartermaster Harbor, Puget Sound are included in this repository to demonstrate the expected input format and output. This data was collected by the class of TGEOS 445 (Spring 2026) at the University of Washington Tacoma.
 
| File | Description |
|---|---|
| `CTD_Data_QMH.xlsx` | Example input — one sheet per station, imported from `.cnv` |
| `CTD_Graphs_QMH.pdf` | Example output — all depth profile graphs |
| `ctdinformation.doc` | `.cnv` to Excel import instructions provided by University of Washington Tacoma |

> `ctdinformation.doc` was authored by the University of Washington Tacoma and is included here for reference only.
---
 
## Output

A single PDF saved to your Google Drive. Graphs vary by CTD setup:

**UW-Tacoma:**

| Graph | X-Axis |
|---|---|
| Temperature Profiles | Temperature (°C) |
| Salinity Profiles | Salinity (PSU) |
| Density Profiles | Density (kg/m³) |
| Dissolved Oxygen Profiles | Dissolved Oxygen (mL/L) |
| Fluorescence Profiles | Fluorescence (mg/m³) |
| Transmissivity Profiles | Transmissivity (%) |

**UW-Friday Harbor:**

| Graph | X-Axis |
|---|---|
| Temperature Profiles | Temperature (°C) |
| Salinity Profiles | Salinity (PSU) |
| Density Profiles | Density (kg/m³) |
| Dissolved Oxygen Profiles | Dissolved Oxygen (mL/L) |
| Fluorescence Profiles | Fluorescence (mg/m³) |
| Turbidity Profiles | Turbidity (NTU) |
| pH Profiles | pH |

All graphs: Y-axis is depth (m), inverted so the surface is at the top. All stations are plotted as smooth spline curves on a single graph with a legend identifying each station. Title format: `[Location Name]: [Variable] Profiles`

---

## Requirements
 
- Google Account (Google Drive + Google Colab)
- Microsoft Excel (to prepare the `.cnv` data)
- Sea-Bird `.cnv` CTD output files
---
 
## Workflow
 
### Step 1 — Prepare your Excel file

1. Open your Sea-Bird `.cnv` files and import the data into Excel.
2. Place each station's data in its own sheet — **do not modify the data or headers**.
3. **Rename each sheet to the station name.** Sheet names become the legend labels on the graphs.
4. Save the workbook as a `.xlsx` file.

> The notebook expects unmodified Sea-Bird `.cnv` imports. UW-Tacoma data starts at row 560; UW-Friday Harbor data starts at row 220. Do not add or remove rows above the data.

### Step 2 — Upload to Google Drive
 
Save the `.xlsx` file to the **root of your Google Drive** (i.e., `My Drive/`, not a subfolder).
 
### Step 3 — Run the notebook

1. Open the notebook: [CTD Profile Grapher on Google Colab](https://colab.research.google.com/drive/1adB0KzOIpqY6TdhmQE3F8XZP5Et4sybI?usp=sharing)
2. Open the **Table of Contents** in Colab.
3. **Run `CTD Data Grapher`** — installs required packages.
4. **Run `CTD Setup & Site Info`** — displays the setup selector and input fields:
   - **CTD Setup**: Select `UW-Tacoma` or `UW-Friday Harbor`
   - **Location**: Survey area name (appears in graph titles)
   - **Excel File**: Name of your `.xlsx` file — **do not include `.xlsx`**
   - **PDF File**: Desired name for the output PDF — **do not include `.pdf`**
5. **Run `Google Drive Access`** — Google will prompt you to authorize Drive access. The notebook reads your `.xlsx` and saves the output PDF to your Google Drive.

---

## Data Column Mapping

**UW-Tacoma** (data starts row 560):

| Variable | Column Index | Excel Column |
|---|---|---|
| Depth | 14 | O |
| Temperature | 2 | C |
| Salinity | 10 | K |
| Density | 12 | M |
| Dissolved Oxygen | 7 | H |
| Fluorescence | 5 | F |
| Transmissivity | 6 | G |

**UW-Friday Harbor** (data starts row 220):

| Variable | Column Index | Excel Column |
|---|---|---|
| Depth | 15 | P |
| Temperature | 2 | C |
| Salinity | 11 | L |
| Density | 13 | N |
| Dissolved Oxygen | 8 | I |
| Fluorescence | 5 | F |
| Turbidity | 6 | G |
| pH | 7 | H |

---

## Credits

Notebook authored by James Simpson. Example CTD data collected by TGEOS 445 (Spring 2026) students at the University of Washington Tacoma. `ctdinformation.doc` provided by the University of Washington Tacoma.

---
 
## Dependencies
 
Installed automatically by the notebook: `ipywidgets`, `openpyxl`, `pandas`, `matplotlib`, `scipy`, `numpy`
