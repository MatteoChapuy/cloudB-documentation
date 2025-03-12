# Eolyse - User Documentation

## Introduction

Eolyse is an acoustic analysis platform specializing in assessing the noise impact of wind farms. Integrated into CloudB, this tool enables engineers to analyze, model, and optimize wind farm electricity production while ensuring compliance with noise regulations.

## Application Structure

Eolyse follows a hierarchical structure to organize acoustic analyses:

- **Projects**: Each project corresponds to a distinct acoustic study.
- **Simulations**: A project can contain multiple simulations to explore different scenarios.
- **Calculation Modules**: Each simulation includes multiple calculation modules for geospatial and acoustic analyses. Each module retains only one calculation result in memory.

## How to Create a Project and Simulation?

1. Access the **Eolyse workspace** and click on **"Eolyse Projects"**.
2. Click the **"+"** button in the top right, enter a name, and click **"Create"**.
3. Your new project will open automatically.
4. Click **"Simulation"**, then **"Create Simulation"**.
5. Enter a name and select an acoustic propagation model.

> **Note:** A project can contain multiple acoustic simulations with different propagation models.

## Acoustic Propagation Models

Eolyse is based on **Acventum**, an acoustic propagation model developed by Delhom Acoustique. Two variants are available:

- **Acventum Global**: The historical propagation model that calculates global sound pressure level attenuation.
- **Acventum Tiers**: A more advanced model based on **ISO9613-2**, computing attenuation per **1/3 octave bands**.

### Comparison of Propagation Models

| Features | Acventum Global | Acventum Tiers |
|----------|----------------|---------------|
| Geometric divergence attenuation | ✅ | ✅ |
| Atmospheric absorption attenuation | ✅ | ✅ |
| Ground effect attenuation | Basic (ISO9613-2 alternative method) | Advanced (ISO9613-2 main method, adjustable ground factor) |
| Topography-induced screening effect | Maekawa Method | ISO9613-2 (max 25 dB) & R&D improvements |
| Automatic terrain path & screen detection | Optional | ✅ |
| Wind effect on propagation | ✅ | ✅ |
| Calculation for distinct day & night periods | ✅ | ✅ |
| Calculation for 10 wind speed classes (3m/s - 12m/s) | ✅ | ✅ |
| Output format | Global SPL | Global & Spectral SPL (50Hz - 10kHz) |
| Available calculation modules | Noise Impact, Wind Direction, Background Sensitivity, Time-Series, Noise Map | Same except **Noise Map** |
| Compatibility with curtailment algorithm | ✅ | ✅ |

## Simulation Modeling

Modeling is a key step in Eolyse, defining noise sources (wind turbines) and acoustic receivers for propagation calculations.

### Simulation Management

- **Create a simulation**: From the project page, click **"Simulation" → "Create Simulation"**, enter a name, and select a propagation model.
- **Duplicate a simulation**: Copy an existing simulation (sources, receivers, or both). The propagation model can be changed. **Results are not duplicated.**
- **Rename a simulation**: Available in the **"Simulation"** options menu.
- **Delete a simulation**: **Irreversible** deletion of all points and results.

### Adding Sources and Receivers

Two methods are available:

1. **Manual addition**: Add points one by one via a form.
2. **CSV Import**: Upload a list of points using a **CSV template** (downloadable in the interface).

#### Manually Creating a Source (Wind Turbine)

Each wind turbine (source) requires:

1. **Name** (unique in the simulation).
2. **GPS Coordinates** (WGS84 format, e.g., `43.604381, 1.443369`).
3. **Wind Turbine Model** (selected from the internal database containing acoustic/electrical characteristics).
4. **Color Group (optional)** (visible on maps and visualizations).

> Once added, sources appear on the interactive map and can be modified or deleted.

#### Manually Creating a Receiver

Acoustic receivers require:

1. **Name** (unique in the simulation).
2. **GPS Coordinates** (WGS84 format).
3. **Color Group (optional)**.

> Once added, receivers appear on the map and can be used for noise impact calculations.

#### Importing Points via CSV

Instead of adding each point manually, users can import a **CSV file**:

1. Download the **CSV template** (`Download Import Template`).
2. Fill in point names and GPS coordinates.
3. Upload the file via **"Upload"**.
4. The system will validate the file and import the points.

### Exporting Modeled Points

To export points:

1. Go to the **simulation management menu**.
2. Click **"Export Points"**.
3. A CSV file will be generated containing all sources, receivers, and associated data.

## Calculation Modules

### **Map Module**

- Displays sources & receivers on an **interactive map**.
- Supports **regulatory buffer zones**:
  - **French measurement perimeter** (acoustic measurement protocol).
  - **500m buffer zone** (France’s minimum distance between wind turbines and dwellings).

### **Elevation Profile Module**

- Displays topographic elevation between a noise source and a receiver.
- Identifies **terrain obstacles** affecting noise propagation.
- Uses **Google Maps API** with **20m precision**.

### **Noise Impact Module**

- Evaluates wind farm noise impact based on **meteorological conditions, topography, and background noise**.
- Determines **regulatory compliance**.
- Provides **graphical & tabular outputs**.

### **Wind Direction Analysis Module**

- Computes noise impact for **16 wind sectors** (every **22.5°**).
- Generates **polar noise distribution analysis**.
- Useful for identifying **critical wind directions** affecting noise.

### **Background Noise Sensitivity Module**

- Assesses noise impact under **+/-5 dB(A) variations** in background noise.
- Helps optimize **curtailment strategies** for year-round compliance.

### **Time-Series Analysis Module**

- Uses **meteorological time-series data** to analyze dynamic noise evolution.
- Supports **two methodologies**:
  1. **Direct Method**: Uses measured **residual noise** to estimate induced noise.
  2. **Inverse Method**: Uses measured **ambient noise** to infer residual & induced noise.
- Outputs **temporal noise impact trends**.

### **Noise Mapping Module**

- Generates a **color-mapped noise contour** using a **grid of receiver points**.
- Allows configuration of:
  - **Grid size & resolution**.
  - **Propagation conditions (topography, wind, temperature, humidity)**.
- Provides **interactive map visualization**.

