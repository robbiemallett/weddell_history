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
  style="display: inline-block; margin: 0 auto;max-width: 200px">
