---
title: Making an editable map for PowerPoint with R
date: 2019-11-04T15:12:56-05:00
slug: make-a-simple-map
---

Recently, I needed to make a map that would color-code states and overlay some points to represent data for specific metro areas. My initial reaction to graphic creation is to always start with R and use `ggplot2`, but the final product also needed to be editable as a PowerPoint graphic. 

This was the perfect opportunity to try a few R packages that were new to me: the [`urbnmapr`](https://github.com/UrbanInstitute/urbnmapr) package from the Urban Institute for map-making and the [`officer`](https://davidgohel.github.io/officer/) and [`rvg`](https://rdrr.io/cran/rvg/) packages to export data from R into Microsoft Office document formats (including `.pptx`).

Using a [great tutorial](https://medium.com/@urban_institute/how-to-create-state-and-county-maps-easily-in-r-577d29300bb2) on how to use `urbnmapr`, I was able to produce the map I wanted pretty quickly. All it took was a simple `left_join()` to merge my state data with the `urbnmapr` data, then all I had to do was use `geom_polygon` and `geom_point` to map my two layers of data.

I recreated a version of the map I made using two tables of data: 

- A list of states, coded as states I've called home, visited, or never been
- A list of coordinates indicating where I've done postsecondary work

It took me about 15 minutes to pull this together - most of it was spent actually creating the data:

![](https://raw.githubusercontent.com/alspur/simple-map-for-ppt/master/place_ps_map.png)

Most of the time, I’m exporting the plot as a static `.png` file, but thanks to the `officer` and `rvg` packages, I was able to export my `ggplot` object to a slide in a `.pptx` deck:

```
library(officer)
library(rvg)

read_pptx() %>%
  add_slide(layout = "Title and Content", master = "Office Theme") %>%
# this is where you call your ggplot object (here it's `place_ps_map`)
  ph_with_vg(code = print(place_ps_map), type = "body") %>% 
# this is where you provide the filename/location for your new ppt slide
  print(target = "place_ps_map.pptx")
```
That's it! From that point, I was able to open the PowerPoint deck and play around with every part of my map. I "ungrouped" all of the elements, then re-grouped the legend and map elements as separate groups to make re-positioning really easy.

![](https://raw.githubusercontent.com/alspur/simple-map-for-ppt/master/ungroup.png)

If you want to check out the code and data I used, it's available on [Github](https://github.com/alspur/simple-map-for-ppt).
