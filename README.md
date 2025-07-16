# lego_sets
Interactive LEGO Sets Dashboard in Power BI. Explore LEGO sets by theme, age group, and price. Built with DAX measures, filters, bookmarks, and a decomposition tree. Data sourced from Maven Analytics.

Berikut adalah contoh file README.md yang menarik dan profesional untuk proyek Power BI kamu:



# LEGO Sets Power BI Dashboard

A Power BI project built using the LEGO datasets from [Maven Analytics](https://app.mavenanalytics.io/datasets?search=lego). This dashboard provides an interactive exploration of LEGO sets, enabling users to filter and analyze by age range, price, theme group, and more.



## 📌 Project Overview

This dashboard was developed as a part of a data analytics case study with the following objectives:

### ✅ Objective 1: Load and Prepare the Data

- Connected to the `lego_sets.csv` file.
- Removed unnecessary fields: `minifigs`, `bricksetURL`, and `thumbnailURL`.
- Cleaned the data by filtering out rows with missing values for:
  - `price`
  - `age`
  - `pieces`
  - `imageURL`
- Reviewed and corrected data types.
- Created conditional columns:
  - `Age Range`: 
    - `Over 18`
    - `10 to 17`
    - `5 to 9`
    - `1 to 4`
  - `Price Range`: 
    - `$$$$$` for prices > $500  
    - `$$$$` for prices > $100  
    - `$$$` for prices > $50  
    - `$$` for prices > $25  
    - `$` otherwise
- Added DAX Measures for analysis (see details below).



### ✅ Objective 2: Design the Report Layout & Visuals

- Created card visuals to highlight:
  - Total LEGO Sets
  - Average Pieces
  - Average Price
- Added slicers for:
  - Theme Group
  - Theme
  - Age Range
- Built an interactive table displaying:
  - Set Name
  - Set ID
  - Theme
  - Age Range
  - Average Pieces
  - Average Price
  - Price Range
- Developed a detail section that updates based on selected set:
  - Name, Image, Price, Year, Pieces, and Age
  - Includes placeholders if multiple sets are selected
- Customized visual interactions to prevent table selection from affecting top-level metrics.



### ✅ Objective 3: Add Interactive Components

- Implemented a numeric range parameter `Max Price` (0–850, step 5) using:
  ```DAX
  
  Maxprice = GENERATESERIES(0, 850, 5)


 Used the parameter with a slicer to dynamically filter sets by price.
 Enabled tooltips on the table to display LEGO set images on hover.
 Created bookmarks and reset buttons to:

   Reset all filters on the page
   Customize button visuals for hover/press states
 Built a second report page using a Decomposition Tree to drill into:

   Total Sets by Category → Theme Group → Theme → Set Name
 Added navigation buttons for smooth page transitions.



## 📊 Key Measures

````markdown

```DAX
Avg Age       = AVERAGE(lego_sets[age])
Avg Piece     = AVERAGE(lego_sets[pieces])
Avg Price     = AVERAGE(lego_sets[price])
Total Group   = DISTINCTCOUNT(lego_sets[themeGroup])
Total Sets    = DISTINCTCOUNT(lego_sets[set_id])
Maxprice      = GENERATESERIES(0, 850, 5)

Max Price Filter = IF([Avg Price] <= Maxprice[Maxprice Value], 1, 0)

Selected Set     = IF(HASONEVALUE(lego_sets[name]), MAX(lego_sets[name]), "Select a Set")
Selected Price   = IF(HASONEVALUE(lego_sets[price]), MAX(lego_sets[price]), "-")
Selected Pieces  = IF(HASONEVALUE(lego_sets[pieces]), MAX(lego_sets[pieces]), "-")
Selected Age     = IF(HASONEVALUE(lego_sets[age]), MAX(lego_sets[age]), "-")
Selected Year    = IF(HASONEVALUE(lego_sets[year]), MAX(lego_sets[year]), "-")
````



## 📁 Files

 `lego_sets.csv`: Source data file
 `lego-dashboard.pbix`: Power BI dashboard file



## 🙌 Credits

Data for this project was provided by Maven Analytics, an excellent platform for data professionals to practice real-world projects and challenges.
👉 Explore more datasets at: [https://app.mavenanalytics.io/datasets](https://app.mavenanalytics.io/datasets)



## 🔗 About the Creator

This project was developed as part of a Power BI learning journey, focusing on transforming raw data into insights through meaningful interactivity and storytelling.

