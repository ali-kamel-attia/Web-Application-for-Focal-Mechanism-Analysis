# Web-Application-for-Focal-Mechanism-Analysis
I provided an HTML script that implements a web application designed to determine focal mechanism solutions for local earthquakes within a regional seismographic network
The application includes:
   - Loading velocity models and SAC seismic waveform files.
   - Computing takeoff angles and other station parameters.
   - Picking P-wave polarities manually or automatically.
   - Solving for focal mechanisms (strike, dip, rake) using a grid search and polarity data.
   - Visualizing the results on a stereonet and beachball plot.
   - Allowing manual selection of nodal planes and poles on the stereonet.
   - Exporting results and plots.
The code is a single, self-contained HTML file with embedded CSS and JavaScript. We are to explain the code and its functionality. Let's break it down:
1.	The HTML structure defines a page with:
  - A header and subtitle.
  - A grid layout with two main columns.
  - Left column: Inputs for velocity model and SAC files, event coordinates, diagnostics, and a table of stations.
  - Right column: A stereonet canvas, controls for the beachball and P/T axes, and focal mechanism solution display.
2.	The CSS styles the page with a dark theme and a responsive layout.
3.	The JavaScript code is extensive and includes:
  - Utilities for math, file reading, and coordinate conversions.
  - A velocity model parser and interpolator.
  - A takeoff angle calculator using a Jansky method (ray tracing) and a fallback method.
  - SAC file parser (reading binary SAC files and extracting headers and data).
  - Data model for stations (rows) and events (EV).
  - Functions to compute and render the stereonet and beachball.
  - A focal mechanism solver that uses a grid search over strike, dip, and rake, then refines.
  - Functions for manual picking of nodal planes and poles on the stereonet.
  - A picker modal for interactive polarity picking on waveforms.
  - Event handlers for file inputs, buttons, and canvas interactions.
The application allows the user to:
  - Load SAC files and a velocity model
  - Set event coordinates (or read from SAC headers).
  - Compute takeoff angles and station parameters.
  - Pick polarities manually in the picker modal or automatically.
  - Solve for the focal mechanism using the polarities.
  - Manually define the focal mechanism by clicking on the stereonet (two points for the first plane and one for the second).
  - Export the results and the stereonet as PNG.
The code is well-structured but quite long (over 1500 lines of JavaScript). It uses modern JavaScript features and the Canvas API for drawing. Note that the code includes a custom SAC parser that attempts to read both little-endian and big-endian SAC files and merge multiple SAC files for the same station. The focal mechanism solver (FocalMechanismSolver) uses a grid search over strike, dip, and rake, then refines the solution. It scores each candidate by comparing the predicted polarity (from the moment tensor) with the observed polarity. The stereonet is a lower-hemisphere equal-area projection. The beachball is drawn by evaluating the sign of the radiation pattern on a grid and filling accordingly. The code then computes the strike, dip, and rake for the two planes and chooses the one that fits the polarities best. The picker modal displays the waveform and allows the user to set the P arrival time and polarity.
This is a sophisticated web application for seismological analysis, specifically for focal mechanism determination from P-wave first motions. This is a web-based seismology tool for focal mechanism analysis called FMSAC Web. It's a comprehensive application that allows seismologists to determine earthquake focal mechanisms (the orientation of fault planes and slip direction) from seismic wave data.

Key Features:
1. Data Input & Processing
•	Load SAC (Seismic Analysis Code) waveform files
•	Parse velocity models for accurate travel time calculations
•	Read station metadata (coordinates, network codes)
2. Polarity Picking
•	Interactive waveform viewer for manual P-wave polarity picking
•	Automatic polarity detection suggestions
•	Filtering options (high-pass, low-pass) for better signal visualization
•	Bulk auto-picking capability
3. Takeoff Angle Calculations
•	Uses Jansky's method for accurate ray tracing through velocity models
•	Fallback geometric calculations when ray tracing fails
•	Computes station azimuths, back-azimuths, and distances
4. Focal Mechanism Solving
•	Automated grid search over strike, dip, and rake parameters
•	Manual nodal plane selection by clicking on the stereonet
•	Polarity-based scoring to find best-fitting solutions
•	Refinement around best solutions
5. Visualization
•	Upper-hemisphere stereonet display
•	Beachball diagrams showing focal mechanism solutions
•	Station polarities plotted as colored symbols (red = compression, blue = dilation)
•	P and T axis markers
6. Advanced Features
•	Manual mode: Define fault planes by picking three points on the stereonet
•	Real-time solution updates as picks change
•	Export results as tables, images (PNG), and focal mechanism solutions
•	Responsive design with dark theme
Workflow:
1.	Load velocity model and SAC files
2.	Set earthquake location (EVLA, EVLO, EVDP)
3.	Pick P-wave polarities manually or automatically
4.	Compute takeoff angles and station parameters
5.	Solve for focal mechanism (automatically or manually)
6.	Visualize results on a stereonet with a beachball
7.	Export final solutions
This tool essentially replicates functionality that would traditionally require multiple specialized seismology software packages, all in a single web interface.


