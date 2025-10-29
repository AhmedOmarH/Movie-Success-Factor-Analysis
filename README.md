# Movie Success Factor Analysis

## Overview
This project analyzes the MovieLens dataset to identify key factors influencing a movie's financial success. The analysis explores the relationship between budget, revenue, genre, and return on investment (ROI) using Python and data science libraries.

## Dataset
The analysis utilized three main datasets from the MovieLens collection:
*   `movies_metadata.csv`: Containing core movie information (budget, revenue, genre, release date, popularity, vote average, etc.).
*   `credits.csv`: Containing cast and crew information.
*   `keywords.csv`: Containing plot keywords.

The initial `movies_metadata` dataset contained 45,466 entries. After merging with `credits` and `keywords` (based on matching movie IDs), filtering out entries with zero budget or revenue (which removed ~40,000 rows), and performing standard data cleaning (handling ID types, removing duplicates), the final dataset used for analysis consisted of **5,375 movies**.

## Methodology
1.  **Data Loading and Exploration:** Loaded the raw CSV files and performed initial checks on data types, shapes, and content.
2.  **Data Cleaning and Merging:**
    *   Corrected the data type of the `id` column in `movies_metadata` from object to integer, filtering out non-numeric IDs.
    *   Filtered `credits` and `keywords` to include only IDs present in the cleaned `movies_metadata`.
    *   Performed inner joins to create a single dataset containing metadata, credits, and keywords for movies where all information was available.
    *   Converted the `budget` column from string to numeric.
    *   Filtered the dataset to exclude movies with `budget` or `revenue` equal to 0 or NaN.
3.  **Feature Engineering:**
    *   Calculated `profit = revenue - budget`.
    *   Calculated `ROI = (revenue - budget) / budget`.
    *   Parsed the JSON-like `genres` column to extract the primary genre for each movie.
4.  **Exploratory Data Analysis (EDA):**
    *   Created visualizations (scatter plots, bar charts, histograms, correlation matrix) using Python libraries (pandas, matplotlib, seaborn).
    *   Analyzed the relationships between key variables.

## Key Findings
1.  **Budget vs. Revenue:** There is a strong positive correlation between a movie's budget and its revenue. Generally, higher-budget films tend to generate higher revenues. However, there is significant variance; many high-budget films underperform, and some low-budget films achieve substantial revenue.
2.  **Genre Performance:** Different genres exhibit varying levels of average financial performance.
    *   **Higher Revenue Genres:** Animation and Adventure movies consistently showed the highest average revenue in the dataset.
    *   **Lower Revenue Genres:** Drama, Crime, and Horror genres tended to have lower average revenue.
3.  **Return on Investment (ROI) Distribution:** The distribution of ROI is highly skewed. The most common outcome was a loss (negative ROI), with the peak around -50%. While many films lose money, a smaller number achieve very high returns, creating the long tail in the distribution.
4.  **Correlation Analysis:**
    *   `Budget` and `Revenue` showed a strong positive correlation.
    *   `Revenue` and `Profit` showed a very strong positive correlation.
    *   `Budget` and `ROI` showed a very weak correlation, indicating that spending more money does not necessarily translate to a higher *rate* of return.
    *   `Popularity` showed a moderate positive correlation with `Revenue`.

## Files
*   `movie_analysis_refactored.ipynb`: The main Jupyter notebook containing the analysis code and narrative.
*   `movie_analysis_refactored.html`: The exported HTML version of the notebook.

## Technologies Used
*   Python
*   Pandas
*   NumPy
*   Matplotlib
*   Seaborn
*   Jupyter Notebook

## How to Run
1.  Ensure you have Python 3.x installed.
2.  Install the required libraries: `pip install pandas numpy matplotlib seaborn jupyter`.
3.  Download the source dataset files (`movies_metadata.csv`, `credits.csv`, `keywords.csv`) and place them in the same directory as the notebook.
4.  Open the `movie_analysis_refactored.ipynb` file in Jupyter Notebook or JupyterLab.
5.  Run all cells sequentially.

Alternatively, you can open the `movie_analysis_refactored.html` file directly in your web browser to view the executed notebook and its outputs.
