README – IE–IATA Datathon Dashboard
1. Overview

This HTML dashboard was developed for the IE–IATA Datathon 2025. It provides an interactive environment to:

Visualize EU27 aviation fuel demand and CO₂ emissions under two predefined SAF scenarios (S0 and S1).

Explore gate-to-gate emissions over time using the g2g_emissions dataset uploaded as a CSV file.

Analyze relationships between flights, total CO₂ and CO₂ intensity per flight.

The dashboard runs entirely client-side in the browser and requires no backend.

2. SAF Scenario Module (EU27)

The upper section of the dashboard implements the two official EU27 SAF scenarios:

Scenario 0 – Business-as-Usual (market-driven SAF)
SAF blending increases from 1% in 2025 to 20% in 2050 (1%, 3%, 7%, 20% at anchor years).

Scenario 1 – ReFuelEU / High Ambition
SAF blending follows the regulatory trajectory: 2% in 2025, 6% in 2030, 20% in 2035, 70% in 2050.

The model uses fixed assumptions embedded in the JavaScript code:

Baseline fuel demand (2022): 38 Mt

Time horizon: 2025–2050

Annual fuel demand growth: 1.5%

CO₂ emission factor: 3.16 tCO₂ per tonne of fuel

SAF life-cycle reduction: 70% versus fossil jet fuel

For the selected scenario (S0 or S1), the dashboard computes and plots:

Total EU27 fuel demand over time (fixed Y-axis: 30–60 Mt).

Scenario-specific SAF share over time (fixed Y-axis: 0–100%).

CO₂ emissions and avoided CO₂ relative to a zero-SAF baseline (fixed Y-axis: 0–200 Mt).

3. Gate-to-Gate Emissions Module

The lower section (“Gate to Gate Emissions”) activates when the user uploads a CSV file through the “g2g_emissions CSV” input. The code expects at least the following columns:

YEAR

CO2_TONS

NB_FLIGHTS

After parsing the file in the browser using PapaParse, the dashboard aggregates data by year and generates:

Total CO₂ per year (line chart).

Number of flights per year (line chart).

CO₂ per flight per year (line chart, CO₂_TONS / NB_FLIGHTS).

CO₂ vs. number of flights (scatter plot, each point labelled by year).

Ranking of years by CO₂ per flight (bar chart, highest intensity first).

This provides a compact exploratory analysis of operational efficiency and its evolution across years.

4. Technologies Used

HTML5, CSS3 (static layout and styling, Aileron font, IE/IATA color palette).

JavaScript only on the client side:

Plotly.js for interactive charts.

PapaParse for CSV parsing in the browser.

Favicon: datathon_icon.png referenced in the <head> section.

No external server, database or Python backend is required.

5. How to Run

Place the HTML file and datathon_icon.png in the same folder.

Open the HTML file in a modern web browser (Chrome recommended).

Use the scenario dropdown to switch between Scenario 0 and Scenario 1.

Click on the g2g_emissions CSV input, select your CSV file, and wait for the plots to update.

All computations and visualizations are executed locally in the browser.