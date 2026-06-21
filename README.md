# CTD Profile Grapher
 
A Google Colab notebook for visualizing multi-station CTD cast profiles from Sea-Bird SBE19plus `.cnv` files. The tool reads station data from a user-prepared `.xlsx` file in Google Drive, plots depth profiles for six oceanographic variables with all stations overlaid on each graph, and saves the figures as a PDF back to Google Drive.
 
---
 
## Example Data
 
The following example files from Quartermaster Harbor, Puget Sound are included in this repository to demonstrate the expected input format and output. This data was collected by the class of TGEOS 445 (Spring 2026) at the University of Washington Tacoma.
 
| File | Description |
|---|---|
| `CTD_Data_QMH.xlsx` | Example input — one sheet per station, imported from `.cnv` |
| `CTD_Graphs_QMH.pdf` | Example output — all six depth profile graphs |
 
---
 
## Output
 
A single PDF is saved to your Google Drive containing **six depth profile graphs**, one per variable:
 
| Graph | X-Axis |
|---|---|
| Depth vs. Temperature | Temperature (°C) |
| Depth vs. Salinity | Salinity (PSU) |
| Depth vs. Density | Density (kg/m³) |
| Depth vs. Dissolved Oxygen | Dissolved Oxygen (mL/L) |
| Depth vs. Fluorescence | Fluorescence (mg/m³) |
| Depth vs. Transmissivity | Transmissivity (%) |
 
- **Y-axis**: Depth (m), inverted so the surface is at the top
- **X-axis label**: Positioned at the top of the graph
- All stations are plotted as smooth spline curves on a single graph, with a legend identifying each station
- Graph title format: `[Location Name]: Depth vs [Variable]`
---
 
## Requirements
 
- Google Account (Google Drive + Google Colab)
- Microsoft Excel (to prepare the `.cnv` data)
- SeaBird `.cnv` CTD output files
---
 
## Workflow
 
### Step 1 — Prepare your Excel file
 
1. Open your SeaBird `.cnv` files and import the data into Excel.
2. Place each station's data in its own sheet — **do not modify the data or headers**.
3. **Rename each sheet to the station name.** Sheet names become the legend labels on the graphs.
4. Save the workbook as a `.xlsx` file.
> The notebook expects CTD data to begin at **row 560** (index 559) - standard for Seabird CTD used at UWT. Do not add or remove rows above the data.
 
### Step 2 — Upload to Google Drive
 
Save the `.xlsx` file to the **root of your Google Drive** (i.e., `My Drive/`, not a subfolder).
 
### Step 3 — Run the notebook
 
1. Open the notebook: [CTD Profile Grapher on Google Colab](https://colab.research.google.com/drive/1jivXdfRxe5QnhqM4HMkhIL0wbTsBSarX)
2. Open the **Table of Contents** in Colab.
3. **Run `CTD Data Grapher`** — installs required packages (`ipywidgets`, `openpyxl`).
4. **Run `Test Site`** — displays three input fields:
   - **Location**: The name of the survey area (appears in graph titles, e.g. `Quartermaster Harbor`)
   - **Excel File**: The name of your `.xlsx` file — **do not include `.xlsx`**
   - **PDF File**: The desired name for the output PDF — **do not include `.pdf`**
5. **Run `Google Drive Access`** — Google will prompt you to authorize Drive access. The notebook will then read your `.xlsx` and save the output PDF directly to your Google Drive.
---
 
## Data Column Mapping
 
The notebook reads the following columns from the raw `.cnv` import (zero-indexed):
 
| Variable | Column Index | Excel Column |
|---|---|---|
| Depth | 14 | O |
| Temperature | 2 | C |
| Salinity | 10 | K |
| Density | 12 | M |
| Dissolved Oxygen | 7 | H |
| Fluorescence | 5 | F |
| Transmissivity | 6 | G |
 
> If your `.cnv` import places data in different columns, update the `col` dictionary in the notebook accordingly.
 
---
 
## Dependencies
 
Installed automatically by the notebook:
 
- `ipywidgets`
- `openpyxl`
- `pandas`
- `matplotlib`
- `scipy`
- `numpy`
