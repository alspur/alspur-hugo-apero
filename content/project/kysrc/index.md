---
author: Alex Spurrier
categories:
- R
date: "2019-03-19"
draft: false
excerpt: This package contains Kentucky public school data for 2012-2017 from the Kentucky School Report Card website. Data from the 2017-2018 school year are from the Open House page on the Kentucky Department of Education website.
layout: single
subtitle: An R package of Kentucky School Report Card data from 2012-2018
tags:
- Accountability
title: kysrc
---

[![Travis-CI Build Status](https://travis-ci.org/alspur/kysrc.svg?branch=master)](https://travis-ci.org/alspur/kysrc)

This package contains Kentucky public school data for 2012-2017 from the [Kentucky School Report Card website](https://applications.education.ky.gov/src/DataSets.aspx). Data from the 2017-2018 school year are from the [Open House page on the Kentucky Department of Education website](http://openhouse.education.ky.gov/Data).

### Installation

Install from Github with [devtools](https://github.com/hadley/devtools):

```r
library(devtools)
install_github("alspur/kysrc")
```

### What's inside

This package contains nine different kinds of datasets with data at three different levels: state, district, and school. To reference a table for a particular level, you will need to append the suffix `state`, `dist`, or `sch`, respectively. For example, `ach_grade_state` would provide summary data for the entire state of Kentucky, while `ach_grade_sch` would provide the same data for each public school in Kentucky.

The datasets included in this package are:

- `acctbly_...`: Accountability system scores and labels (until the 2015-2016 school year).
- `acctbly_essa_...`: Accountablity system scores and labels *after* ESSA reauthorization (first year = 2017-18).
- `ach_grade_...`: K-PREP test data by grade level (3-8, HS).
- `ach_level_...`: K-PREP test data by school level (Elementary School, Middle School, High School).
- `act_...`: ACT test data.
- `ap_...`: AP test data.
- `ccr_...`: College/Career Readiness data.
- `fin_summary_...`: Financial summary data (district & state only).
- `frpl_...`: Free/Reduced Price Lunch Eligibility data.
- `grad_...`: Four-year cohort graduation rate data.
- `iep_...`: Individualized Education Plan (IEP) counts and rates.
- `lep_...`: Limited English Proficiency (LEP) counts and rates.
- `profile_...`: Enrollment, Title 1 status, longitude, latitude, and NCES ID
- `race_...`: Racial demographic data.
- `rev_exp_...`: Revenue and expenditure data (district & state only).
- `seek_...`: SEEK funding data (district & state only).
- `tax_...`: Tax data (district & state only).
- `teach_...`: Teacher data.
- `discipline_...`: Discipline data.
- `legal_...`: Legal event data.
- `behavior_events...`: Behavior event data.
- `behavior_context...`: Behavior event data by context.
- `behavior_location...`: Behavior event data by location.
- `behavior_ses...`: Behavior event data by student socioeconomic status.
- `behavior_grade...`: Behavior event data by grade level.

Each dataset includes a unique identifier for the school/district/state, `sch_id`. This variable is helpful for joining data from multiple tables, as is `year`, which indicates the school year during which the data was generated.

There are currently 8,323,012 rows of data in this package and a total of 90,468,003 data points.