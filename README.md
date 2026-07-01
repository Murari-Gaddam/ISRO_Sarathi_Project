#  SARATHI - Subgoal-based Autonomous Rover Assistance through Trajectory and Hierarchical Intelligence

## ISRO Hackathon Problem Statement 8

**Detection and Characterization of Subsurface Ice in Lunar South Polar
Regions Using Chandrayaan-2 DFSAR and OHRC Data**

## Project Overview

SARATHI proposes an **orbiter-centric autonomous navigation
framework** for lunar rover missions in permanently shadowed regions
(PSRs). Computationally intensive tasks are executed on the orbiter,
while the rover acts as a lightweight execution platform.

## Objectives

1.  Detect and estimate subsurface ice.
2.  Generate a traversability cost map.
3.  Select an optimal landing site.
4.  Compute an energy-aware global rover path.
5.  Divide the mission into hierarchical checkpoints.
6.  Execute autonomous navigation with continuous hazard monitoring.

------------------------------------------------------------------------

# System Pipeline

## Stage 1 -- Ice Detection

-   DFSAR CPR and DoP analysis.
-   High CPR (\>1) and low DoP (\<0.13) indicate probable ice.
-   Estimate ice concentration and penetration depth.
-   Generate ice probability and ice volume maps.

## Stage 2 -- Landing Site Determination

Inputs: - Ice probability - Terrain slope - Boulder density -
Illumination - Elevation

Weighted landing cost:

**J = w₁S + w₂D + w₃E − w₄I**

Where: - S = Terrain safety - D = Distance to target - E = Energy
required - I = Ice probability

Lowest-cost safe region is selected.

## Stage 3 -- Orbiter Global Planning

Inputs: - Landing site - Traversability cost map - Mission goal - Rover
battery model

Pipeline: 1. Global map fusion 2. Mission goal definition 3. Cost
evaluation 4. Global RRT\* planning 5. Hierarchical checkpoint
generation 6. Command transmission

Outputs: - Global path - Ordered checkpoints - Energy profile - Mission
commands

## Stage 4 -- Orbiter-Centric Navigation

Orbiter: - Visual/LiDAR SLAM - Localization - 3D mapping - Obstacle
detection - Local motion planning

Rover: - Capture camera & LiDAR data - Execute received commands - Wheel
control - Health monitoring - Emergency stop - Telemetry feedback

------------------------------------------------------------------------

# Key Differentiators

## Hierarchical Checkpoint Navigation

Mission divided into sequential checkpoints to simplify replanning.

## Orbiter-Centric Planning

Heavy computation moved from rover to orbiter.

## Energy-Aware Mission Planning

Battery model integrated into global planning.

## Adaptive PSR Navigation

Visual SLAM in illuminated terrain. LiDAR-based navigation inside PSRs.

------------------------------------------------------------------------

# Technology Stack

## Remote Sensing

-   Chandrayaan-2 DFSAR
-   Chandrayaan-2 OHRC
-   DEM

## Terrain Analysis

-   QGIS
-   GDAL
-   Rasterio
-   NumPy

## Planning

-   Traversability Cost Maps
-   Multi-objective Optimization
-   RRT\*
-   Hierarchical Checkpoints

## Navigation

-   Visual SLAM
-   LiDAR SLAM
-   Obstacle Detection
-   Wheel Odometry

## Development

-   Python
-   OpenCV
-   SciPy
-   Matplotlib

------------------------------------------------------------------------

# Expected Outcomes

-   Accurate ice probability mapping
-   Safe landing site selection
-   Energy-efficient global path
-   Autonomous checkpoint navigation
-   Reduced rover compute and power consumption
-   Improved mission robustness inside PSRs
