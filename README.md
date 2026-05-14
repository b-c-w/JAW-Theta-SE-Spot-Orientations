Theta Ellipsometer Spot Orientation Visualizer
An interactive, browser-based tool for visualizing the orientation and shape of the measurement spot on the J.A. Woollam Theta ellipsometer. The tool models the two-bar geometry of the motorized arms that positions the sample stage, and shows how the projected measurement spot is oriented and distorted across the sample stage.

Purpose
On the Theta ellipsometer, the angle of incidence and the in-plane orientation of the measurement spot depend on the configuration of the instrument's two articulated arms. Because the beam strikes the sample obliquely, the illuminated footprint is an ellipse whose size, eccentricity, and rotation vary with position on the stage. For mapping experiments, sample alignment, and interpretation of spatially resolved data, it is useful to know — at a glance — exactly how the spot will be oriented at any (x, y) location on the sample.

This tool computes and visualizes that geometry directly. Given the bar lengths and stage parameters, it renders:

the in-plane orientation angle β of the measurement spot at every point on a configurable grid,
the relationship between the arm angle α and the radial reach R,
a tabular dump of all relevant geometric quantities (R, θ, α₁, α₂, α, β, A, C, B, D) for each sampled point.
The result is an at-a-glance map of where the instrument can reach, how the spot will be oriented there, and which regions of the stage are kinematically inaccessible.

Features
β-field plot. The primary view draws a small tilted ellipse at every grid point inside the configured plot radius, oriented according to the local β angle computed from the two-bar geometry. Unreachable points are flagged in red. The ellipse semi-axes are user-configurable so the rendered footprint can be matched to the actual beam dimensions.

α(R) curve. A secondary plot sweeps the reach R from zero to the maximum radius and shows α as a function of R for the current bar parameters, making it easy to see the working range of the arms.

Data table. A scrollable table lists every sampled grid point with its polar coordinates (R, θ), both intermediate arm angles (α₁, α₂), the resulting α and β, and the four bar-length quantities A, C, B, D. Invalid (unreachable) points are marked.

Magnifier lens. Hovering over the β-field plot activates a 4× zoom lens that re-renders the ellipse field around the cursor, with a crosshair and a live readout showing the exact (x, y, β) at the cursor location. Useful for inspecting dense grids or behavior near the workspace boundary.

Live updates. All inputs (A, B, grid spacing, plot radius, ellipse semi-axes eA and eB) are wired to update all three views simultaneously.

Usage
Open index.html in any modern browser. No build step, no dependencies, no server required — the entire tool is a single self-contained HTML file using vanilla JavaScript and the HTML5 Canvas API.

Adjust the input fields at the top of the page to match the bar lengths and grid resolution of interest. The β-field plot, α(R) curve, and data table all redraw automatically. Hover over the β-field plot to activate the magnifier.

Inputs
A, B — the two bar-length parameters of the goniometer geometry, in millimeters.
Grid — spacing between sampled points on the stage, in millimeters.
Radius — maximum radial extent of the plotted region, in millimeters.
eA, eB — semi-axes of the ellipse drawn at each grid point to represent the projected beam footprint.
Notes
The geometric model assumes the idealized two-bar linkage of the Theta ellipsometer and does not account for mechanical backlash, arm flex, or stage tilt. The tool is intended as a planning and visualization aid, not as a calibration reference.

Development
This code was developed using Anthropic Claude Opus 4.7.
