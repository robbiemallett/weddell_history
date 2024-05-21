# Tracing the history of five Weddell Sea ice floes

We visited five sea ice floes with KuKa in March/April 2022.

The purpose of the code in this repository is to plot the positions of the floes, and learn about how they reached that point. In particular, we would like to know *where* they came from, *what* weather they had experienced, *how* much snowfall they had seed, and *when* they experienced freeze-up.

## Back-tracing the floe trajectories

We'd like to know where the five floes came from; to do that, we reconstruct their drifting trajectories across the Weddell Sea using [ice motion vectors from OSISAF](https://osisaf-hl.met.no/osi-405-c-desc
). A description of the methodology behind these vectors is [Lavergne, et al. (2010)](https://doi.org/10.1029/2009JC005958).

### Method

I downloaded the daily ice motion vectors from the OSISAF FTP between January 1st 2021 - May 1st 2022. This covers just over a year of vectors. The actual data in the files is the ice displacement over 48 hours, so for a day I've just halved this. At each timestep, I displace the final position of the floes by the negative of the ice motion vector in the nearest valid grid cell in the file for that day. I stop the algorithm if the nearest grid cell to the floe is land or land-ice: by not stopping for anything else, these trajectories are probably too long. But they're still a good guide to the range of locations from which the floes have come. 

<img
  src="/figures/floe_trajectories.jpg"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
The green area in the above plot indicates the sea ice distribution on the day on which the final floe was visited (24th March). Blue areas indicate areas perennially covered by ice shelves. Red dots indicdate the five ice floes on the days on which they were visited.

The floes come from quite diverse origins, particularly Floe 1. That's noticeable because it had a clearly softer and thinner remnant snow layer on it, and was the only floe where we were able to easily access the snow-ice interface. 

## What weather did the floes experience on their journeys?

Now we have the trajectories of the floes in time and space, we can reconstruct the weather that they experienced prior to our measurements. Of particular interest is the snowfall experienced by the floes before and after of the fall freeze-up. I defined the timing of the freeze-up as the last day on which surface air temperatures in ERA5 were at or above zero degrees. This occurred in February for all five floes. 

I then did a cumulative sum of the snowfall after that date.

<img
  src="/figures/floe_weather.jpg"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
  In the figure above I've indicated the 0C threshold with the red dashed line, and my definition of the Fall freeze-up timing with the vertical blue dashed line. The blue solid line indicates the cumulative snofall since that date. 
  
 We can plot this cumulative snowfall against the typical accumulated snow on a regional scale:
 
 
<img
  src="/figures/snowfall_violins_with_floes.jpg"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
The plot above indicates that post-feeeze-up snowfall that the floes typically received is basically what an Arctic floe would receive in a whole winter. So we can perhaps imagine the situation as that of an Arctic snowpack superimposed on top of the remnant snow from the summer.
