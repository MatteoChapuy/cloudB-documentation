# [Release Notes](release-note.md)

Welcome to the CloudB Release Notes! In this document, we'll highlight the new features, fixes, and optimizations that
have been added to CloudB over the course of the year.

---

## March 2025

### Version 1.4.0 - 1.4.3

#### General Updates:
- Changed simulation module selection to be included in the settings menu option.
- Updated settings menu option component.
- Added the module name in the title with project and simulation for clarity.
- Created a new module "Map" and removed the map layout from the other simulation modules.
- Renamed the "Standard" module to "Classic Noise Impact" (CNI).
- Fixed the custom operating modes generation in CNI using Acventum tiers model.
- Removed custom operating modes generation for WDA using Acventum tiers model.
- Fixed backend Acventum tiers run method to actually use Acventum tier model.
- Changed simulation creation name to allow letters, numbers, spaces, hyphens (-), and underscores (_).
- Updated usage of dcc.Store to cache `simulation_id` and `project_id`. Now, information is cached in the Redis session server-side.
- Improved function simplicity and layout in the creation of sources and receivers accordion callback.
- Added a lock on the simulation layout when no simulation is selected.
- Updated simulation and project title in the header to include the acoustic model in use and simulation module.
- Locked simulation module in settings menu when no simulation is active.
- Fixed wind turbine perimeter calculation.
- Added the items (sources and receivers) IDs in the accordion.

#### Noise Impact Module Updates:
- Updated calculation history to include more information about the last calculation.
- Removed project and simulation ID storage in `dcc.Store` and moved it to server-side cache (Redis) for the Noise Impact module.
- Changed attenuation chart "Adetail" to display in stack mode instead of group mode.
- Updated backend endpoint to work with both model names: "Acventum global" and "Acventum tiers".
- Changed attenuation tab layout to generate chart radio item options on page creation.
- Changed compliance threshold limits for the Noise Impact module (both models). Now allows setting ambient noise in range 0-100 dB and noise impact in range 0-35 dB.
- Updated noise impact alerts to use the notification component.
- Renamed "Standard" module to "Noise Impact Module".
- Added calculation of electric power in Acventum tiers in default mode.
- Modified input data method to separate the return of input data dictionary and error messages.
- Added heuristic curtailment algorithm and integrated it with noise impact calculation (using both models).
- Activated the curtailment algorithm option in the Noise Impact module when using the Acventum tiers model.
- Removed the option to set noise compliance rules for each receiver. Now, rules apply to all receivers globally.
- Updated Acventum tiers model to take into account compliance threshold defined in input data.
- Fixed CSV and Excel export for Acventum global simulation with the new curtailment algorithm.
- Fixed CSV export for Acventum tiers and Noise Impact module.
- Fixed Excel export for Noise Impact and Acventum tiers models.
- Added formatting in the contribution tab for Excel exports.
- Fixed an error in noise impact views where sources with identical names were missing in the recap table when "by source" option was active.

#### Wind Direction Analysis (WDA) Updates:
- Changed calculation history for WDA module using Acventum global and Acventum tiers.
- Updated simulation info to include the use of the curtailment algorithm in calculations.
- Changed usage of `dcc.Store` for project ID and simulation ID in WDA module using Acventum global.
- Updated duplicate simulation module to allow users to change the name and acoustic model selected. Also improved modal UI.
- Updated open, create, rename, duplicate, and delete simulation modal to use new UI components.
- Updated import modeling points modal to use the new UI.
- Changed alerts in WDA module to use notification components (for both models).
- Integrated the new curtailment solver with WDA calculation in the backend.
- Fixed error on notification trigger when backend server is down and user attempts to run a calculation.

#### Eolyse Module Updates:
- Integrated tiers octave model in the Background Noise Sensitivity module.
- Fixed errors in the Map module.
- Fixed an issue in the Elevation module where calculations could not run without input data in the Noise Impact module.
- Fixed project simulation mistakes on module availability.
- Fixed an issue where new simulations in the Noise Impact module did not have a default wind direction value, causing an error in the wind direction multi-select.
- Fixed Eolyse - Acventum tiers - Noise Impact / Background Noise Sensitivity - Run calculation now returns an error if operating modes are not generated.
- Fixed Eolyse - Acventum global - Noise Impact - Run calculation without selecting wind direction now returns a user-friendly error.
- Removed check on source ID starting with "S" in Acventum tiers.
- Updated curtailment section text to make it clearer.
- Updated stored data to be compressed using zlib.
- Updated Acventum tiers backend to reduce the number of Maps Elevation API calls.

---

---

## October 2024

### Version 1.3.3

#### Acmonitor Connect :

##### Project app :
- **Project Date Sorting**: Projects can now be sorted by date within the project table.
- **Project owner Column**: A new “Project owner” column has been added to the project table, displaying  the project 
owner assigned to each project. 
- **Company-Wide Viewer Access**: All company employees are now automatically added as viewers in each project, 
ensuring full visibility across the organization. 
- **Device Table Ordering**: Devices in the project table are now automatically sorted by the device name in 
alphanumeric order.
- **Station Status Color**: The station markers on the map now reflect the current status color of each station, 
visually indicating operational conditions.


### Version 1.3.2

**Major update: Launch of the Norsonic Data Converter app within the Toolbox workspace.**

#### Norsonic Data Converter :

- The application is available now for internal use. 

---

## July 2024

### Version 1.3.1

#### Acmonitor Connect :

- **Measurement Point Name Field**: Added a new input field for naming measurement points. 
- **Special Characters in Project Names**: Enabled the use of special characters in project names. 
- **Project View for Admins**: Modified view rules so that admins of CloudB can now see all projects.
- **Data Display Indicator**: Added an indicator to show the percentage of data displayed.
- **Project Date Calculation**: Updated project dates to be based on the minimum and maximum dates of all associated stations.
- **Battery Charts**: Added battery status charts for each measurement point.
- **Device Images**: Integrated images for devices to enhance visual representation.

---

## May 2024

### Version 1.3.0

**Major update: Introduction of the Project Application in Acmonitor Connect.**

#### Acmonitor Connect :

- **Project Application**: Deployed the Alpha version. The application is available now for internal use. 

---

## March 2024

### Version 1.2.9

#### Eolyse Improvements:

- **Data Export Enhancements**: Enhanced the data download functionality to allow users to select specific wind classes
  for their reports, ranging by default from 3 m/s to 12 m/s. This customizable feature is now available for CSV and XLS
  exports across Eolyse applications: Standard, Wind Direction Analysis, Sensitivity, and Compliance Risk.

- **Naming Convention Optimization**: Users can now begin naming receiver and source points with numbers and utilize
  the "_" symbol. This update is designed to facilitate easier sorting and indexing of receiver names.

- **Interactive Chart Improvements**: In the Wind Direction Analysis application, when ratio mode is activated, users
  can now view ratios as percentages via mouse hover over the chart, enhancing data interaction and readability.

- **Fullscreen Mode Guidance**: Added a simple message in the Mesh application's full-screen mode, informing users they
  can exit full-screen mode using the Escape key, aiming to improve user navigation and experience.

- **Chronology Application Feature**: Introduced the ability for users to input the electrical power generated by each
  turbine in the Chronology application. This addition enables a new data chart where users can compare noise levels
  induced by electrical power, both globally and per wind turbine.

- **Chart Display Correction**: Fixed an issue in the Sensitivity to Residual Noise application where the electrical
  power chart's x-axis incorrectly displayed index values instead of the correct wind classes from 3 m/s to 12 m/s.

#### Acmonitor Connect :

- **Project Application**: Deployed the third sprint for user testing. Application is still not available for now. 

---

## February 2024

### Version 1.2.8

#### General Updates:

- Upgraded database architecture for enhanced performance.
- Refined SQL connection protocols to align with the new database structure.

#### Acmonitor Connect Enhancements:

- **Wind Farm Analysis**: Introduced a comprehensive wind rose, featuring both global views and segmented displays by
  wind speed classes.
- **Project Application**: Deployed the initial two sprints for user testing, laying the groundwork for future
  development in Acmonitor Connect.
- **Device Application**: Resolved numerical discrepancies in data display ratios.

#### Eolyse Improvements:

- **User Access**: Tailored wind turbine library access for 'inter' and 'client' roles, ensuring appropriate
  user-specific model filtering.
- **Map Layout**: Addressed and rectified the map background layout issue in the Mesh application.
- **Mesh Center Point**: Added functionality for users to specify a custom center point within the Mesh application,
  providing greater control over mesh generation.

---

## January 2024

### Version 1.2.7

#### Acmonitor Connect

##### Device data app

- **Sortable Devices by Status**: Easily manage your devices by sorting them according to their status. This new feature
  provides a quick and efficient way to organize and track the status of your devices.

##### Wind Farm Analysis app

- **Enhanced Data Display**: Acoustic data can now be displayed for periods exceeding 15 days.

---

## December 2023

### Version 1.2.6

#### Acmonitor Connect

##### Device data app

- **Enhanced Data Display**: Data can now be displayed for periods exceeding 15 days.
- **Search bar optimization**: Our search bar is now fast and executes instantly.
- **Device Details**: Now, select device button give the access of a table that display detailed information about
  device status and battery levels.
- **Battery information**: Now you have the ability to simply select the device you're interested in and check its
  current battery level.

---

## November 2023

### Version 1.2.4 to 1.2.5

#### Acmonitor Connect

##### Device data app

- **Enhanced Search Bar**: The search bar has been tuned and is fully operational, allowing you to effortlessly search
  for devices with precision.

##### Wind Farm Analysis app

- **Close Button for Filters**: Quickly revert to the unfiltered raw data with the new "Close" button next to the filter
  name. This simplifies your data exploration, making it more efficient.
- **Enhanced Search Bar**: The search bar has been tuned and is fully operational, allowing you to effortlessly search
  for devices with precision.
- **Streamlined Filter Management**: Filter parameters are now conveniently accessible through intuitive input fields,
  replacing dropdowns for a more user-friendly filtering experience.
- **Enhanced Data Visualization**: Filtered data is now highlighted in a distinct color within the analysis section.
- **Data Export Options**: Now, datasets can be downloaded in both CSV and Excel file formats.
- **Enhanced Time Range Visibility**: We've added a convenient feature to improve your analysis experience. Now, when
  you hover over the "Change time range" button, the start and end times of the analysis will be displayed.
- **Download Improved results analysis Files**: We've enhanced the file download feature. Now, when you download a
  results analysis,if you've applied a filter during the analysis, the filter name is also included in the file name for
  easy reference.
- **Streamlined Data Access**: We've added a convenient "Close" button for a smoother user experience. When you apply a
  filter to your data, you can now easily close the filter view and return to the raw analysis data with just one click.
- **Filter by Acoustic Level**: We've resolved a bug that was preventing users from filtering data by acoustic level.
  You can now effortlessly filter your data based on acoustic levels, giving you more control and insights into your
  wind farm analysis.

##### Upload data app

- **Header Correction**: We've resolved a bug that was affecting the date and time header when uploading files. The
  header is now called correctly.

---

## October 2023

### Version 1.2.0 to 1.2.3

**Major update: Introduction of the Wind Farm Analysis Application in Acmonitor Connect**

#### Acmonitor Connect

- **Wind Farm Analysis app**: A specialized application designed for analyzing measurements collected by the Acmonitor
  stations.
- **Enhanced Upload Section**: The upload functionality in Acmonitor Connect now supports weather and wind time series
  data, allowing for seamless cloud-based analysis.
- **Devices Data upgrade**: Improvements to the Devices Data application offer a more intuitive selection process for
  time series visualization.

#### Eolyse

- **Project name creation**: Users will now be prompted to avoid using special characters when creating project names,
  streamlining data handling.
- **Wind direction selection**: Issues related to Acventum backend's default wind direction data have been corrected,
  ensuring smoother operation.
- **Custom wind turbine and direct usage**: Previously, custom wind turbines added by users were not immediately
  available for use. This has been addressed; Eolyse now scans for available turbines each time a new calculation is
  initiated.

---

## September 2023

### Version 1.1.0

**Major update to enhance both general CloudB features and the Eolyse workspace.**

#### General CloudB Features

- **New URL**: Now operates under our company's domain name for a more cohesive brand experience.
- **UI Overhaul**: A simplified and intuitive user interface to improve user experience.
- **User Management Update**: Distinguish between internal users and clients, with the ability to specify account access
  permissions.
- **Cloud Architecture Update**: Transitioned to a new architecture with separate frontend and backend servers for
  optimized calculations on Google Cloud.
- **Enhanced Documentation**: Moved to GitHub Pages, offering more comprehensive guidance compared to the previous
  Monday documentation.

#### Eolyse

- **Wind Turbine Library**: Users can consult our extensive wind turbine library with improved data visualization and
  even add their own personalized wind turbine models.
- **API Maps Elevation**: Significant improvements in calculation time. Elevation data is now available worldwide.
- **Export Format**: New export format available in Delhom-branded Excel sheets for easy data extraction.
- **Simulation History**: Simplified tracking of past calculations across different applications.
- **Mesh Application**: Introduces the capability to calculate noise impact on a defined mesh grid.
- **Source and Receiver Building Updates**: Improved ease of definition for both sources and receivers.

---

## Jun 2023

### Version 1.0.6

#### General CloudB Features

- **User Management Service Upgrade** : we have upgraded our user management service by integrating a Redis server. This
  enhancement is expected to eliminate instances of unanticipated logouts. Users can now enjoy a more seamless and
  uninterrupted experience.
- **Cloud Run instance Upgrade** : to provide a robust infrastructure for handling concurrent requests, we have upgraded
  our Cloud Run Station from 512 MB RAM and 1 CPU to 8 GB RAM and 4 CPUs. This substantial upgrade allows us to increase
  the number of workers from 1 to 9, thereby significantly improving our capacity to manage simultaneous requests. You
  should notice a faster response time and improved system performance.

#### Eolyse:

We've addressed a crucial issue in the Eolyse workspace concerning the Chronologies app. Previously, users experienced
problems with wind turbine model calculations due to model confusion. This patch fixes that issue, allowing users to
perform their calculations without any model mix-up.

---

## April 2023

### Version 1.0.3 to 1.0.5

#### Eolyse

- **Patch** : Eolyse apps now replace default NaN elevation by 0 in the calculation. Minor patch to fix issues with
  dataset semicolon issue in app standard : added a round method in app standard data table display. Fixed CSV import
  separator issue with semicolon. Fixed CSV import source modeling dropdown filtering.
- **Simulation upgrade** : simulation can now be renamed, duplicated or deleted.

#### Acmonitor Connect

- **Updates** : plot line type changed from continuous to dot for non-equivalent acoustic data.

---

## March 2023

### Version 1.0.0 to 1.0.2

#### Eolyse

- **Patch** : Acventum and AcventumTimeSeries can now decode CSV files with ; separator. Projects can now be created
  normally on Eolyse