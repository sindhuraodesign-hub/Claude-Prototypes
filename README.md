Polygonisation V2 — SME Input & Solution Exploration
SME Input
The key requirement from the SME was that users should be able to visualise cut/fill regions on the map, filter out noise, and then polygonise the selected regions.

Initial Solution Explored
The most obvious solution was to introduce Polygonisation within the Layer Properties card, alongside the existing histogram.

The ideation explored a workflow where users could:

Use the histogram to control which parts of the DEM are visualised as cut/fill regions.
Apply thresholds to reduce noise.
Visualise the resulting cut/fill regions directly on the map.
Define polygonisation parameters such as minimum polygon area, layer name, etc.
Generate multiple cut/fill polygon layers from a Subtract DEM based on the selected histogram ranges.
In essence, the goal was to allow users to use the histogram to control which parts of a Subtract DEM are polygonised, rather than immediately polygonising the entire output.

View prototypes here → [Prototype link]

Why the Solution Was Put on Hold
The solution raised a few larger product and architecture questions.

1. Polygonisation is only relevant to certain DEMs
Currently, the platform does not differentiate between continuous DEMs and Difference/Subtract DEMs.

However, this workflow is specifically useful for Difference DEMs because they contain cut/fill information. This meant that the Polygonisation tool would only be available for a DEM containing the relevant type of data.

This raised a broader question around whether the platform should explicitly differentiate between different types of DEMs.

The team was not aligned on introducing this distinction itself. While some felt that differentiating between continuous and Difference DEMs would make the product behaviour clearer, others felt that introducing separate DEM types was unnecessary.

Regardless of whether we formally introduced the distinction, the Polygonisation tool would still need to be conditionally available based on the type of data contained in the DEM.

This made the proposed solution more tightly coupled to a larger product decision that had not yet been resolved.

2. The future direction of Polygonisation is broader
The longer-term direction is for Polygonisation to potentially work with other raster types as well, with different inputs depending on the raster being processed.

This raised concerns about continuing to add more functionality into the Layer Properties side card. What started as a focused Polygonisation workflow could eventually make the card increasingly complex and difficult to scale.

3. It only solved part of the larger workflow
The proposed solution solved an important part of the workflow — visualising cut/fill regions, filtering noise, and then polygonising them.

However, it did not address the larger question of where the overall Subtract DEM workflow should live.

Today, users already receive cut/fill regions as a by-product of Subtract DEM, which gives them an existing way to access and polygonise those results.

Introducing another Polygonisation workflow within Layer Properties would therefore add a new path for achieving something that is already partially supported, while also introducing the complexity of handling different types of DEM data.

The broader direction being considered is to move Subtract DEM into the Workspace, so that the entire workflow — including visualisation, filtering, polygonisation, and its future extensions — can happen together on the map.

This felt like a more scalable direction than introducing a new capability into Layer Properties primarily to solve one part of the existing workflow.

4. Direction of Layer Properties
There was also a broader UX consideration.

We want to move away from the current pattern of double side cards and eventually redesign Layer Properties around a single, more streamlined side card.

Adding Polygonisation into the existing Layer Properties experience would increase the amount of functionality being placed there, while the longer-term direction is actually to simplify and rethink the Layer Properties structure.

Decision
The team decided not to proceed with the proposed Polygonisation V2 solution within Layer Properties.

The decision was not because the workflow itself was not valuable. Rather, the effort and complexity required to introduce it in the current architecture did not justify the benefit, especially given the direction of the product.

The more scalable direction is to solve the larger Subtract DEM workflow at the Workspace level, where visualisation, filtering, polygonisation, and future raster-processing capabilities can eventually come together as part of a broader map-based workflow.
