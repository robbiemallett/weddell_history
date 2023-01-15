# Tracing the history of five Weddell Sea ice floes

We visited five sea ice floes with KuKa in March/April 2022.

The purpose of the code in this repository is to plot the positions of the floes, and learn about how they reached that point. In particular, we would like to know *where* they came from, *what* weather they had experienced, *how* much snowfall they had seed, and *when* they experienced freeze-up.

Also in the repo is code to compare average snowfall amounts over sea ice, in the Arctic, the Antarctic, and in the Weddell Sea specifically. Doing this allows us to compare the snowfall that our five floes saw with what would "typically" be experienced in Antarctica at-large, and also within the Arctic.

## Characterising typical snowfall over sea ice in the Arctic and Antarctic.

In-situ and airborne data indicate that snow on Antarctic sea ice is deeper than in the Arctic. This is worth a quick investigation with ERA5 atmospheric reanalysis data, because it tells us (a) how true that is in the Weddell sea (b) how typical was the snowfall-experience of our five floes in 2022.

This part gets done in [Snow_reanalysis.ipynb](https://github.com/robbiemallett/weddell_history/blob/main/notebooks/Snow_reanalysis.ipynb)

### Method

The code to download the required data is at the bottom of the notebook. It uses the Python API that interfaces with the Copernicus data store. Very easy to set up if you haven't used it before.

I downloaded monthly average values for the "snowfall" and "sea_ice_cover" variables at 1° resolution for regions poleward of 50° latitude (NH.nc & SH.nc). I did this for the years 2000 - 2021.  These files are too big for storage in github, so you'll need to run the download code and get them yourself. Or ask me for them - they're in my Dropbox. 

I was interested in the **cumulative** snowfall that a sea ice floe experiences over the cold season. To get an indicative value, I defined two, hemisphere-dependent, six-month cold seasons. October - March for the Arctic, and April to September for the Antarctic. This is currently the weakest part of my analysis - I need to think a bit harder about the Antarctic definition since this year we saw Weddell Sea freeze up in February. 

For each month I made a spatial mask of sea ice where its concentration was >50%, and accumulated snowfall. I then summed along the time dimension so I had a cumulative value in each grid cell for the season. I then took the spatial average to get a single, cumulative snowfall value for the Arctic, the Antarctic, and the Weddell Sea specifically. I defined the Weddell as having a longitude between 15°W & 60°W. 

<img
  src="/figures/snowfall_lineplots.jpg"
  style="display: inline-block; margin: 0 auto;max-width: 100px">


<img
  src="/figures/snowfall_violins.jpg"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
The plots above show that Antarctic sea ice typically experiences three times as much snowfall as its Norethern counterpart. However, the Weddell Sea only has twice as much. This is fairly consitently the case - i.e. there haven't been any years where either the Weddell Sea or Antarctica as a whole has seen an "Arctic-like" quantity of snowfall. 

## Back-tracing the floe trajectories

We'd like to know where the five floes came from; to do that, we reconstruct their drifting trajectories across the Weddell Sea using [ice motion vectors from OSISAF](https://osisaf-hl.met.no/osi-405-c-desc
). A description of the methodology behind these vectors is [Lavergne, et al. (2010)](https://doi.org/10.1029/2009JC005958).

### Method

I downloaded the daily ice motion vectors from the OSISAF FTP between January 1st 2021 - May 1st 2022. This covers just over a year of vectors. The actual data in the files is the ice displacement over 48 hours, so for a day I've just halved this. At each timestep, I displace the final position of the floes by the negative of the ice motion vector in the nearest valid grid cell in the file for that day. I stop the algorithm if the nearest grid cell to the floe is land or land-ice: by not stopping for anything else, these trajectories are probably too long. But they're still a good guide to the range of locations from which the floes have come. 

<img
  src="/figures/floe_trajectories.jpg"
  style="display: inline-block; margin: 0 auto;max-width: 100px">
  
 
