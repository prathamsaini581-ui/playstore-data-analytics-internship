# Google Play Store Data Analytics — Internship Project

## Overview
This project analyzes the Google Play Store apps dataset along with user reviews to uncover insights about app performance, ratings, installs, sentiment, and category trends. It was built as part of the ElevanceSkills Data Analyst Internship, extending the training project with additional dashboard tasks.

## Dataset
- `googleplaystore.csv` — App-level data (category, rating, size, installs, price, etc.)
- `user_reviews.csv` — User reviews with sentiment polarity and subjectivity scores

## Tech Stack
- Python, Pandas, NumPy
- Plotly (Express + Graph Objects) for visualizations
- NLTK (VADER sentiment analysis)
- scikit-learn
- pytz (IST time-based visibility rules)

## How to Run
1. Clone this repository
2. Install dependencies:
   ```
   pip install pandas numpy plotly nltk scikit-learn pytz
   ```
3. Open `Analysis.ipynb` in Jupyter Notebook / JupyterLab
4. Run all cells from top to bottom (Kernel → Restart & Run All)
5. Generated dashboard HTML files will be saved in the same folder

## Internship Dashboard Tasks

### Task 1: Bubble Chart — App Size vs Rating (bubble size = Installs)
- Filters: rating > 3.5; category in Game, Beauty, Business, Comics, Communication, Dating, Entertainment, Social, Events; reviews > 500; app name doesn't contain "S"; sentiment subjectivity > 0.5; installs > 50,000.
- Game category highlighted in pink.
- Legend translations: Beauty (Hindi), Business (Tamil), Dating (German).
- Visible only between 5 PM–7 PM IST.

### Task 2: Choropleth Map — Global Installs by Category
- Filters: excludes categories starting with A, C, G, or S; shows top 5 categories by total installs; highlights categories exceeding 1M installs.
- **Assumption:** The dataset has no country/location column. A country-wise install split was simulated across 15 countries to build the map, since real geographic data doesn't exist in this dataset. This is clearly marked in the notebook.
- Visible only between 6 PM–8 PM IST.

### Task 3: Time Series Line Chart — Installs Trend by Category
- Filters: category starts with E, C, or B; app name doesn't start with x/y/z; reviews > 500; app name doesn't contain "S".
- Legend translations: Beauty (Hindi), Business (Tamil), Dating (German).
- Growth periods (>20% month-over-month) are shaded on the chart.
- **Assumption:** The dataset has no historical install-growth data. The "Last Updated" date was used as a proxy timeline (installs grouped by the month an app was last updated).
- Visible only between 6 PM–9 PM IST.

### Task 4: Stacked Area Chart — Cumulative Installs by Category
- Filters: rating ≥ 4.2; app name has no digits; category starts with T or P; reviews > 1000; size 20–80 MB.
- Legend translations: Travel & Local (French), Productivity (Spanish), Photography (Japanese).
- Months with >25% month-over-month growth are marked with bold highlighted markers.
- **Assumption:** Same "Last Updated" proxy timeline as Task 3, for the same reason.
- Visible only between 4 PM–6 PM IST.

### Task 5: Grouped Bar Chart — Top 10 Categories by Rating & Reviews
- Filters: rating ≥ 4.0; size ≥ 10 MB; app last updated in the month of January.
- Shows average rating and total review count for the top 10 categories by installs, on a dual y-axis.
- Visible only between 3 PM–5 PM IST.

### Task 6: Dual-Axis Chart — Free vs Paid Apps (Installs & Revenue)
- Filters: installs ≥ 10,000; Android version > 4.0; size > 15 MB; content rating = "Everyone"; app name ≤ 30 characters.
- Compares average installs and average revenue for Free vs Paid apps across the top 3 categories by installs.
- **Assumption 1:** "Revenue" isn't a column in the dataset — it's calculated as `Price × Installs` (a standard proxy).
- **Assumption 2:** The task's revenue filter (exclude revenue below $10,000) would exclude every Free app, since Free apps always have $0 revenue — this would make a "Free vs Paid" comparison impossible. The revenue filter was therefore applied to Paid apps only; Free apps pass this specific condition automatically.
- Visible only between 1 PM–2 PM IST.

## A Note on Time-Restricted Charts
Each chart above is only rendered and saved during its specified IST window, as required by the tasks. Outside those windows, running the notebook will print a message instead of generating the chart — this is expected behavior, not an error.



## Author
Pratham Saini — Data Analyst Intern, ElevanceSkills
