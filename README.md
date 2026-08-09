# Polygonisation V2

## Context

Based on SME input, the goal for Polygonisation V2 was to allow users to:

* Visualise **cut/fill regions** on the map.
* Filter out noise using thresholds.
* Polygonise the selected regions.
* Generate multiple cut/fill polygon layers from a Subtract DEM.

The proposed workflow used the existing **histogram in Layer Properties** to control which parts of the DEM were visualised and subsequently polygonised.

## Solution Explored

The initial direction was to introduce Polygonisation directly within the **Layer Properties** card, alongside the histogram.

The workflow explored:

1. Use the histogram to select the cut/fill ranges to visualise.
2. Apply thresholds to reduce noise.
3. Preview the resulting regions directly on the map.
4. Configure polygonisation parameters such as minimum polygon area and layer name.
5. Generate polygon layers from the selected regions.

**[View prototypes here →](#)**

## Challenges Identified

### 1. DEM types and data differentiation

The platform currently does not differentiate between **continuous DEMs** and **Difference/Subtract DEMs**.

However, this Polygonisation workflow is specifically useful when the DEM contains cut/fill data. This means the tool would need to be available only when the underlying DEM contains the relevant data.

This raised a larger product question: **should the platform explicitly differentiate between different types of DEMs?**

The team was not fully aligned on this. Some felt that having distinct DEM types would make the behaviour clearer, while others felt that introducing this distinction was unnecessary.

Regardless of whether the distinction was formally introduced, the Polygonisation tool would still need to be conditionally available based on the data contained in the DEM.

### 2. Future scope of Polygonisation

The longer-term direction for Polygonisation is broader than just cut/fill data. It could eventually be applied to other raster types, with different inputs and parameters depending on the raster.

Adding the feature directly into Layer Properties therefore risked making the side card increasingly complex and coupling a broader raster-processing workflow to the Layer Properties experience.

### 3. Solving only part of the workflow

The proposed solution addressed an important gap: **visualising, filtering, and then polygonising cut/fill regions**.

However, it only solved part of the larger Subtract DEM workflow.

Today, Subtract DEM already generates cut/fill regions as a by-product, giving users an existing way to work with these outputs.

Introducing another Polygonisation workflow inside Layer Properties would therefore add a new path while also introducing additional complexity around DEM types and conditional functionality.

A broader direction being considered was to **move Subtract DEM into the Workspace**, allowing the entire workflow to happen on the map — including visualisation, filtering, Polygonisation, and its future extensions.

### 4. Layer Properties direction

There was also a broader UX consideration.

The current experience can involve **multiple side cards**, while the longer-term direction is to move towards a **single, streamlined Layer Properties side card**.

Adding more processing functionality to Layer Properties would move against this direction and make the card harder to scale.

## Decision

The team decided **not to proceed with the proposed Polygonisation V2 workflow within Layer Properties**.

The decision was not because the workflow itself lacked value. Rather, the **effort and complexity required to introduce it within the current structure did not justify the benefit**, particularly given the broader product direction.

Instead, the focus should move towards solving the **larger Subtract DEM workflow at the Workspace level**.

This provides a more scalable foundation for bringing together:

* Subtract DEM
* Cut/fill visualisation
* Noise filtering
* Polygonisation
* Future raster-processing capabilities

This direction also avoids introducing a new workflow into Layer Properties that would later need to be reworked as the broader raster-processing experience evolves.
