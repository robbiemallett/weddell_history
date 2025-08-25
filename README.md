## Data and code for floe-related figures in Willatt et al. ([2025; GRL](https://doi.org/10.1029/2024GL112870))


This repository contains the necessary data and code to produce the inset map of Figure 1, as well as Figures S1 & S2 from the supporting information.

The code is found in /notebooks/

Data is in /data/, with the exception of the OSISAF ice motion vectors which need to be downloaded from the links below.

## Back-tracing the floe trajectories

We reconstructed drift trajectories across the Weddell Sea using [ice motion vectors from OSISAF](https://osisaf-hl.met.no/osi-405-c-desc
). A description of the methodology behind these vectors is [Lavergne, et al. (2010)](https://doi.org/10.1029/2009JC005958).

The trajectories are plotted alongside sea ice age data from Melsheimer et al. (2023; https://doi.org/10.5194/tc-17-105-2023).

<img
  src="/figures/F1.png"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
## What weather did the floes experience on their journeys?

Now we have the trajectories of the floes in time and space, we can reconstruct the weather that they experienced prior to our measurements. Of particular interest is the snowfall experienced by the floes before and after of the fall freeze-up. I defined the timing of the freeze-up as the last day on which surface air temperatures in ERA5 were at or above zero degrees. This occurred in February for all five floes. 

I then did a cumulative sum of the snowfall after that date.

<img
  src="/figures/S1.png"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
  In the figure above I've indicated the 0C threshold with the red dashed line, and my definition of the Fall freeze-up timing with the vertical blue dashed line. The blue solid line indicates the cumulative snofall since that date. 
