---
title: Statewide school closures as a gif
date: 2020-03-30T19:25:34-05:00
slug: edweek-covid-data
---

We don't know what the total impact of the Covid-19 pandemic will look like. What we do know is that our economy, communities, families, and lives are disrupted in ways they haven't been for a century — including schools.

As I write this blog on March 30, school systems in 47 states have closed their doors to students, with the remaining three states of Iowa, Maine, and Nebraska opting to allow closure decisions to be made at the district level. Education Week produced [a helpful map and spreadsheet of closure-related information](https://www.edweek.org/ew/section/multimedia/map-coronavirus-and-school-closures.html), indicating when these decisions were made, how long schools are expected to be closed (for now), and information about the total number of schools and students in each state.

The past three weeks have been a blur of news about school closures, but this data from EdWeek really helped to clarify the timeline of events for me. I thought displaying this information visually might help people to get a better sense of when and where statewide closure decisions happened over the past few weeks, so I decided to make my first gif using R. 


## How I made it

The [`gganimate` package](https://gganimate.com) was pretty easy to work with, and other tools like [`lubridate`](https://lubridate.tidyverse.org) and [`urbnmapr`](https://urbaninstitute.github.io/urbnmapr/index.html) helped make data wrangling and mapping a breeze. One of my biggest Excel peevs reared its ugly head: dates that get converted to an inscrutable string of numbers.

![](https://raw.githubusercontent.com/alspur/edweek-covid-closures/master/icky_excel_dates.png)

It's easy to solve with a little math, but it still annoys me. Thankfully, [Sam Firke's `janitor` package](http://sfirke.github.io/janitor/) solves this problem with one function.

Once the date formatting issue was resolved, it was just a matter of creating a closure "status" variable for each day from March 15 to March 25, reshaping the data to make it "long," and cleaning up the special cases of the three states without a statewide closure decision.

When it came time to render the gif on my four-year-old [MacBook Adorable](https://www.caseyliss.com/2017/6/25/macbook-adorable), it took less than a minute. Not great, but not too shabby.

![](https://raw.githubusercontent.com/alspur/edweek-covid-closures/master/covid_state_closures.gif)

As always, my [code for this project is on GitHub](https://github.com/alspur/edweek-covid-closures).

## Closing thoughts

I'm satisfied with my first gif and it really was pretty easy with `gganimate`. My hope is that this gif helps a few people understand a small slice of what's happening to our students, educators, and schools right now.

Stay safe, stay home, and stay healthy. :heart: