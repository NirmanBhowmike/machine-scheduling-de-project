# Machine Scheduling DE Project

Zero-configuration browser application for a Doctor of Engineering course assignment.

## Live-demo features

- Three identical parallel machines with a built-in 12-job scenario
- Total tardiness objective
- Combined nervousness measure using start-time and sequence-position changes
- Approximate Pareto-efficient solution set
- User-weighted selection from efficient alternatives
- Manual job movement by controls or drag-and-drop
- Automatic and event-based step simulation
- Dynamic job releases
- Complete machine failures and reduced-capacity disruptions
- Moved/reassigned job highlighting
- Predefined repeatable scenario and random-event mode
- Optional CSV job loading

## Run

Open `index.html` directly in a modern browser. The same file is intended for GitHub Pages deployment and requires no server or external package.

## CSV format

```csv
id,processingTime,dueDate,releaseTime
J1,5,12,0
J2,4,10,0
```

## Baseline

This repository preserves the baseline implementation required by the original DE assignment before a later research-oriented enhancement is selected and implemented.
