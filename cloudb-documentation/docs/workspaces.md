# [Workspaces](workspaces.md)

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

---

# Acmonitor Connect

## Introduction to Acmonitor Connect

Acmonitor Connect is a dedicated workspace focused on acoustic measurements and their subsequent analysis. Initially developed as an IoT (Internet of Things) platform, it displayed real-time acoustic measurements from connected devices. The workspace has since evolved to facilitate advanced analysis calculations, not just on data from IoT devices received through MQTT, but also on datasets uploaded by the user.

## Device Data

In this application, users can request and view real-time measurements from connected acoustic monitoring systems. This functionality is essential for those who need immediate and live data to make informed decisions on-the-spot.
The Device Data application allows users to request real-time measurements from connected acoustic monitoring systems.   

Below is a step-by-step guide on how to use this feature:

1. **Select a Device**: Click the orange "Select device" button located at the top left corner of the page to choose the device you want to query.

2. **Choose a Time-zone**: As all data are stored in UTC, users must select their time-zone to convert the request date and time. Currently, only UTC, UTC+1, and UTC+2 are available options for conversion.

3. **Select Date and Time Range**: Choose the start date and time as well as the end date and time, factoring in your chosen time-zone.

4. **Pick an Acoustic Parameter**: Our monitoring stations can measure multiple parameters. Users need to select the specific parameter they are interested in viewing. Note that the availability of certain parameters depends on the station's configuration, but LAeq is always an available option.

5. **Run the Request**: Upon completing the previous steps, run the request. If data can be located, a time-series graph should appear on the screen.

6. **Download Data**: Users have the option to download the displayed data by clicking on the "Download" button. The data will be downloaded as a CSV file.

7. **View Battery Data**: Navigate to another tab within the application to check the battery status of the selected monitoring station.

8. **Erase and Restart**: To initiate a new data request, the existing graph must be erased. Navigate back to the main screen and start a new query following steps 1 to 7.

By following these steps, users can effectively query, view, and download real-time acoustic data from connected monitoring systems.

## Project

Project is a versatile application designed to streamline project management and data visualization. It facilitates 
the creation and management of acoustic projects, offering tools to input and edit essential project details such 
as names, descriptions, geographical data, and images. Users can also manage measurement devices crucial for data 
collection, view detailed device data, and download this data in a user-friendly CSV format. The app integrates map 
views for a spatial understanding of projects and devices, enhancing the interactive experience by displaying project 
details and device statuses directly on the map. With robust user management capabilities, "Project" ensures secure 
and role-specific access, allowing project owners to control data visibility and modification permissions effectively.

### Project Management:

   - **Creating and Managing Projects**: Users can initiate new projects by specifying names (including special 
   characters), descriptions, locations, and uploading images. Projects can be edited or deleted as per ongoing 
   requirements. Project dates are now automatically calculated based on the minimum and maximum dates of all 
   associated stations.
   - **Project Date Sorting**: Projects can now be sorted by date within the project table.
   - **Project owner Column**: The project table now includes a “Project owner” column, displaying the project owner 
   assigned to each project.

### Device Management:

   - **Adding and Modifying Devices**: Devices used for measurements can be added to projects with specific location 
   details and operational ranges. Users can now name measurement points, upload and view images for each device, 
   and see the State of Health (SOH) and battery levels. Users can also modify or delete devices as needed.
   - **Device Table Ordering**: Devices in the project table are now automatically sorted by the device name in 
   alphanumeric order.

### Data Interaction:

   - **Visualization**: Users can select individual devices to access a detailed data visualization panel, which 
   provides insights within chosen time ranges.
   - **Data Download**: For deeper analysis or record-keeping, data can be downloaded directly from the app in CSV 
   format.

### Map Integration:

   - **Interactive Map Display**: Both projects and devices are plotted on an interactive map, with hover-over details 
   revealing names. This feature aids in quickly locating and distinguishing projects and their associated devices.
   - **Station Status Color**: The color of each station on the map now reflects its current status, offering a visual 
   indicator of operational conditions.

### User Management and Access Control:

   - **User Roles and Permissions**: The app supports diverse user roles, including Administrator, Owners and Viewers. 
   Administrator and Owners have comprehensive control over projects and devices, capable of making any modifications. 
   Viewers have access to view all device data and project details, ensuring transparency without compromising control.
   - **Company-Wide Viewer Access**: All company employees are now automatically added as viewers in each project, 
   ensuring visibility across projects.

### Getting Started with "Project" App:
#### Creating a New Project:
   1. Click on the "Create project" button.
   2. Fill in the project name and description. 
   3. Specify the geographical location of the project using coordinates.
   4. Upload an image for your project (only one image can be added).
   5. Click "Create" to create the project.
#### Editing a Project:
   1. In the project table, click on the "Modify" button for the project that you wish to edit.
   2. Modify the necessary details.
   3. Save the changes.
#### Deleting a Project:
   1. In the project table, click on the "Delete" button for the project that you wish to delete.
   2. Confirm the deletion.
#### Add Devices:
   1. In the project table, click on the project name of the project that you wish to visualize.
   2. Go to the "Devices" section.
   3. Click on the "Add / Modify Device" button.
   4. Enter device details such as name, measurement point name, geographical location, date range, and upload an image.
   5. Click "Validate" to add the device.
#### Modifying Device Details:
   1. Click on the "Add / Modify Device" button.
   2. Choose the device that you want to edit.
   3. Update the necessary details.
   4. Click "Validate" to modify the device.
#### Delete a Device:
   1. In the device table, click on the "Delete" button for the device that you wish to delete.
   2. Confirm the deletion.
#### Visualizing Data:
   1. In the device table, click on the device name that you wish to visualize.
   2. Select the indicator that you want to visualize.
   3. Select the time range. 
   4. Click "Display data" button.
   5. Use various visualization tools provided to gain insights from the data.
#### Downloading Data:
   1. Click on the "Download as CSV" button.
   2. The data will be downloaded in CSV format for further analysis.
#### Interactive Map Usage:
   1. In the project table, click on the project name of the project that you wish to visualize.
   2. Use the map to view the locations of project and devices.
   3. Hover over points on the map to see names.
#### Adding a User:
   1. In the project table, click on the project name of the project that you wish to visualize.
   2. As an administrator or owner, go to the "Users" section.
   3. Click on the "Add / Modify User" button.
   4. Enter user details such as email address and assigning appropriate roles (Owner or Viewer).
   5. Click "Validate" to add the user.
#### Modify User's Role:
   1. Click on the "Add / Modify User" button.
   2. Choose the email of the user whose role you want to edit.
   3. Update the role.
   4. Click "Validate" to update the user's role.
#### Deleting a User:
   1. In the user's table, click on the "Delete" button for the user that you wish to delete.
   2. Confirm the deletion.


## Wind Farm Analysis

The Wind Farm Analysis application is designed to offer comprehensive analysis based on acoustic and meteorological measurements. It allows users to conduct in-depth studies on wind farm noise impacts, utilizing either real-time data or historical datasets. The application is divided into two primary views:

### Dataset view

This view offers data visualizations based on the datasets selected for analysis.

Data Sources: A dataset is composed of two sources: the acoustic source and the meteorological source.
- Acoustic Source: Provided by Acmonitor stations, which gather acoustic data and store them in our cloud as IoT devices. These are directly accessible within the platform.
- Meteorological Source: Provided by the user in the form of a CSV file through the Upload Data section. The file should contain time series data on wind velocity, wind direction, temperature, humidity, and wind farm operating modes.

Creating a New Analysis: By clicking the "Analysis" button, users can select their two data sources for analysis. Data sources can later be updated using the "Data Source" button.

Filters: The "Filter" button allows users to refine the dataset based on specific criteria such as time period, acoustic levels, wind velocity, wind direction, and rain.

### Analysis View
Calculations: This view initiates the calculations based on the French standard analysis described in the acoustic measurement protocol of June 2023.

Results: Users can access visualizations and compliance results related to the measurements.

## Upload Data

The Upload Data application is a utility tool designed to enable users to upload their acoustic and meteorological datasets. These datasets can then be used for analysis in the 'Wind Farm Analysis' application, providing a seamless and integrated experience. The Upload Data application has recently been updated with several new features:

- Data Archiving: Users can archive their upload data by downloading template files. This makes it easier to maintain and manage multiple datasets.

- Wind Data Standardization: During the upload process, users have the option to indicate whether their wind data is already standardized. If Yes: No additional action is needed. If No: Users can provide the height of the measurement point, and the code will automatically standardize the data for the user.

- Cloud Storage: All uploaded datasets are securely stored on the cloud and are accessible to the user.

- Data Management: Users can manage their stored datasets directly within the Upload Data application. This includes the ability to remove datasets if they are no longer needed.

# Toolbox

## Norsonic Data Converter
The Norsonic Data Converter streamlines the process of converting and managing acoustic measurement files for engineers.
After extracting XLSX files using the NorXFer software (by Norsonic), this application allows users to convert and concatenate the data into a CSV format compatible with the dBtrait software (by ACOEM).

### Key Features

**Data Upload**:

The app supports Norsonic data files in the format NORXXX_XXXXXXXX_XXXX_PROFILE.xlsx. Files can be uploaded by dragging and dropping or through browsing, with a maximum size of 5MB.

**Frequency Bands Selection**: 

Users can choose the minimum and maximum frequency bands for analysis, giving flexibility in the data range used for conversion.

**File Result Format**: 

Users can select between generating separate files or a concatenated file for the final output.

**Data Conversion**: 

Once the required parameters are set, clicking “Convert” processes the uploaded data and generates the necessary output files.

**File Management**: 

The app provides a table displaying uploaded files with options to delete or clear them before and after processing.