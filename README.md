# Indian Railways Freight Corridor Analysis

This is the mini project given to us in class for analyzing Indian Railways
freight through graph theory and Python.

The project models a simplified railway network and explores freight routes,
network structure, and a flood-disruption scenario.

## Project question

How does closing the Bhopal-Itarsi section affect the shortest New Delhi-Chennai
freight corridor, and what does the network model suggest about protecting the
diversion route?

## Learning objectives

- Represent railway junctions as graph nodes and track sections as edges.
- Store distance, average speed, track type, and estimated travel time as edge
  attributes.
- Use NetworkX to inspect connectivity, degree, density, and betweenness
  centrality.
- Use Dijkstra's algorithm to compare shortest-distance and shortest-time
  routes.
- Model a closed track section and compare the resulting route with the normal
  route.
- Communicate the assumptions and limits of a small graph model.

## Project files

| File | Purpose |
| --- | --- |
| `indian_railways_freight_analysis.ipynb` | Explained, runnable analysis notebook |
| `indian_railways.csv` | Track-section data used by the notebook |
| `requirements.txt` | Python packages needed to run the project |
| `outputs/` | Generated analysis tables and figures |

The notebook creates or refreshes the `outputs/` folder when run. The generated
tables and figures are included in this repository so they can be reviewed
without running the notebook first.

## Setup and run

Use Python 3.10 or later. From the repository folder, create and activate a
virtual environment, install the dependencies, and start Jupyter:

**Windows PowerShell**

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
jupyter notebook
```

**macOS or Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook
```

Open `indian_railways_freight_analysis.ipynb` and run the cells from top to
bottom. Keep the CSV beside the notebook; the notebook reads it using a
project-relative path.

## Method and interpretation

Each row in the CSV is modeled as an undirected connection between two
junctions. The estimated section running time is
`Distance_km / Avg_Speed_kmh`. Dijkstra's algorithm is run with distance as its
edge weight and again with estimated running time as its edge weight. The flood
scenario copies the graph and removes the Bhopal-Itarsi edge so that the
original graph remains available for comparison.

The supplied dataset has 51 track sections connecting 44 junctions. In the
analysis, the normal New Delhi-Chennai shortest-distance route is 2,181 km with
an estimated 21.61 hours of section running time. With Bhopal-Itarsi removed,
the alternate route is 2,635 km and 27.14 hours: an increase of 454 km and
approximately 5.54 hours. The diversion uses the single-track
Katni-Prayagraj section, making it a reasonable capacity-improvement candidate
for this particular scenario.

These are outputs of a simplified educational model, not an operational
timetable or a verified engineering recommendation. The estimated time sums
section distance divided by average speed; it does not include scheduled
stops, congestion, signalling, crew changes, train-specific restrictions, or
live conditions. The supplied CSV is the analysis input; verify its original
source and reuse terms before redistributing it publicly.

## GitHub publishing checklist

- Keep the notebook, CSV, README, and requirements file together in the
  repository.
- Run the notebook from top to bottom and confirm that all cells complete.
- Do not commit the virtual environment (`.venv/`) or temporary notebook
  checkpoints.
