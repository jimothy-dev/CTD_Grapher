# CTD Profile Grapher

A Google Colab notebook for plotting multi-station CTD cast profiles from SeaBird `.cnv` files. Generates clean, publication-ready PDF figures with depth on the Y-axis and oceanographic variables on the X-axis — one graph per variable, all stations overlaid on each plot.

## Features

- Plots **6 variables** across individual graphs:
  - Temperature
  - Salinity
  - Density
  - Fluorescence
  - Transmissivity
  - Dissolved Oxygen
- All stations plotted together on each graph for easy comparison
- Depth on the Y-axis (increasing downward)
- Station names pulled automatically from Excel sheet names
- Custom location title for each graph
- Output saved as a single PDF to Google Drive

## Requirements

- Google Account (for Google Drive and Colab)
- Microsoft Excel (to prepare the `.cnv` data)
- SeaBird `.cnv` CTD files

## Workflow

### Step 1 — Prepare your data
1. Open your SeaBird `.cnv` files and import the data into Excel.
2. Place each station's data in its own sheet.
3. **Rename each sheet to the station name** — this is what will appear in the graph legend.
4. Save the workbook as a `.xlsx` file.

### Step 2 — Upload to Google Drive
- Save the `.xlsx` file somewhere accessible in your Google Drive.

### Step 3 — Run the Colab notebook
1. Open the notebook: [CTD Profile Grapher on Google Colab](https://colab.research.google.com/drive/1jivXdfRxe5QnhqM4HMkhIL0wbTsBSarX)
2. Follow the step-by-step instructions in the notebook.
3. When prompted, enter:
   - The **filename** of your `.xlsx` file (e.g. `CTD_Survey.xlsx`)
   - The **location name** to display as the graph title (e.g. `Puget Sound Survey 2025`)
4. The notebook will mount your Google Drive, read the file, and generate the plots.
5. A PDF containing all graphs will be saved to your Google Drive.

## Output

A single PDF with one graph per variable. Each graph shows all stations overlaid, making cross-station comparison straightforward.
