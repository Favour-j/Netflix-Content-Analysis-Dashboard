# 🎬 Netflix Insights & Discovery Dashboard

An end-to-end data analytics project exploring content trends on Netflix. This project involves cleaning raw Netflix data using Python and building a fully interactive Power BI dashboard with a Netflix-themed aesthetic.

---

## 📁 Project Files

- `netflix_movies_detailed_up_to_2025.csv` – Raw dataset used for analysis  
- `netflix_data.csv` – Cleaned dataset generated using Python  
- `NETFLIX ANALYSIS PYT.ipynb` – Python script for cleaning and preparing data  
- `Netflix content analysis.pbix` – Power BI dashboard file  
- `Netflix content analysis.pdf` – Exported PDF version of the dashboard for preview  

---

## 🧹 Data Cleaning (Python)

The dataset was cleaned using a Jupyter Notebook (`NETFLIX ANALYSIS PYT.ipynb`).  
Key steps include:
- Renamed columns to lowercase and standardized format
- Converted `date_added` to datetime format
- Extracted `year_added`, `month_added`, and `decade`
- Filled missing values in `country`, `rating`, and `director`
- Removed rows with invalid or placeholder values
- Extracted the primary genre from the genre list

Cleaned data was saved as `netflix_data.csv` for visualization in Power BI.

---

## 📊 Power BI Dashboard

The dashboard consists of **3 pages**:

### 1. **Overview**
- Total titles
- Distribution by genre and country
- Titles added by year

### 2. **Trends & Insights**
- Content type breakdown (Movie vs TV Show)
- Top countries by number of titles
- Title popularity trends

### 3. **Deep Dive**
- Interactive decomposition tree
- Slicers for genre, release year, and country
- Custom navigation buttons between pages

---

## 🎨 Theme & Design

- Dark theme with black background and red/white Netflix branding
- Slicers with sync enabled across pages (Genre, Country, Year)
- Custom Power BI theme JSON applied for consistency
- Navigation buttons allow seamless transition between dashboard pages

---

## 🧠 Tools Used

- **Python (pandas, numpy)** – Data wrangling & preparation
- **Power BI Desktop** – Dashboard creation & DAX
- **Jupyter Notebook** – Cleaning script
- **GitHub** – Version control and project hosting

---

## 📌 Sample DAX Measures

```DAX
Total Titles = COUNTROWS('Netflix')

Total Movies = CALCULATE(COUNTROWS('Netflix'), 'Netflix'[type] = "Movie")

Titles by Selected Genre = 
CALCULATE(COUNTROWS('Netflix'), 
   FILTER('Netflix', 
      'Netflix'[main_genre] IN VALUES('Netflix'[main_genre])
   )
)
