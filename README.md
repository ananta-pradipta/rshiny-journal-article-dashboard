# Journal Article Dashboard (R Shiny)

An interactive R Shiny dashboard that scrapes, cleans, and visualizes publication data from [The Journal of Physiological Sciences](https://jps.biomedcentral.com/articles) (BMC). Built as a final project for DS636 at NJIT.

## Overview

The application performs end-to-end data collection and analysis in a single workflow:

1. **Web scraping** of article metadata (title, authors, correspondence info, abstract, keywords, publish date) directly from the journal's website using `rvest`.
2. **Data cleaning and preprocessing**, including duplicate removal within author lists and keyword fields, handling of missing values, date parsing, and export to CSV.
3. **Interactive visualization** through a Shiny UI with a year-range slider and multiple chart views.

## Visualizations

The dashboard offers five views, selectable via radio buttons in the sidebar:

- **Articles Published by Year** , a stacked bar chart (by month) overlaid with a yearly total trend line (Plotly).
- **Top Keywords** , a bar chart of the 10 most frequent keywords paired with a word cloud.
- **Top Contributing Authors** , a horizontal bar chart of the 10 most prolific authors.
- **Monthly Trend Publication** , a line chart showing aggregate publication volume by calendar month across all selected years.
- **EDA** , raw `summary()` and `str()` output for quick exploratory inspection.

A data table with clickable article links is displayed below all chart views.

## Prerequisites

- R (>= 4.0 recommended)
- The following R packages:

```
rvest, httr, xml2, dplyr, ggplot2, stringr, tidyr, plotly, wordcloud, RColorBrewer, shiny
```

Install all dependencies at once:

```r
install.packages(c(
  "rvest", "httr", "xml2", "dplyr", "ggplot2",
  "stringr", "tidyr", "plotly", "wordcloud", "RColorBrewer", "shiny"
))
```

## Usage

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/rshiny-journal-article-dashboard.git
cd rshiny-journal-article-dashboard
```

2. Open the R script and run the app:

```r
source("Project_Ananta Dian Pradipta_Shiny.R")
```

Alternatively, open the file in RStudio and click **Run App**.

3. Use the year-range slider (2015 to 2024) to select the publication window. The app will scrape data live from the journal website, so an active internet connection is required. A progress bar indicates scraping status.

## Project Structure

```
rshiny-journal-article-dashboard/
  Project_Ananta Dian Pradipta_Shiny.R   # Complete Shiny app (UI + server + scraping logic)
  README.md                              # This file
```

## Notes

- Scraping is performed on each app launch (or whenever the year range changes), so initial load time depends on the number of years selected and the volume of articles in that range.
- The scraped dataset is automatically exported to a CSV file (`DS636_Project_Ananta Dian Pradipta.csv`) in the working directory after each fetch.
- The word cloud truncates keywords longer than 13 characters for display readability.

## License

This project is provided for educational purposes as part of NJIT DS636 coursework.

## Author

Ananta Dian Pradipta
