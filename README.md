# movie-data-cleaning-practice
# Movie Data Cleaning & Initial Analysis

## Overview

This repository contains the code and analysis for a practical data cleaning exercise performed on a movie dataset. The primary goal was to process raw movie data, ensure appropriate data types, handle common inconsistencies, and prepare the dataset for further in-depth analysis. This project served as a hands-on example to solidify data cleaning skills.

## Table of Contents

- [Project Goals](#project-goals)
- [Dataset Information](#dataset-information)
- [Cleaning Steps Performed](#cleaning-steps-performed)
- [Key Analyses & Insights](#key-analyses--insights)
- [Files in this Repository](#files-in-this-repository)
- [How to Run the Code](#how-to-run-the-code)
- [Requirements](#requirements)
## Project Goals

The main objectives of this practice project were:

1.  **Data Type Conversion:** Convert columns to suitable numerical data types for accurate analysis (e.g., `VOTES`, `RunTime`, `start_year`, `end_year` to integers).
2.  **Text Data Cleaning:** Address common inconsistencies in text-based columns like `GENRE`, `ONE-LINE`, and `STARS` (e.g., standardizing casing, handling multiple entries).
3.  **Duplicate Handling:** Identify and appropriately manage duplicate entries, understanding whether they represent redundant data or distinct items (like TV series episodes).
4.  **Data Preparation:** Prepare a clean, structured dataset ready for more advanced exploratory data analysis or machine learning tasks.

## Dataset Information

The dataset used in this project is assumed to be named `movies.csv` . It contains information about various movies and individual TV series episodes, with columns including:

* `MOVIES`: The title of the movie or series.
* `GENRE`: The genre(s) of the film/episode.
* `RATING`: The rating (e.g., on a scale of 1-10).
* `ONE-LINE`: A concise description or tagline.
* `STARS`: The main star(s) or actors involved.
* `VOTES`: The number of votes received.
* `RunTime`: The duration in minutes.
* `start_year`: The release or start year of the film/series.
* `end_year`: The end year of the series, or same as `start_year` for movies.

## Cleaning Steps Performed

The following key data cleaning and transformation steps were implemented:

* **`VOTES` Column:**
    * Removed commas from string values (e.g., "1,234" became "1234").
    * Converted the column to an **integer (`int32`)** data type.
* **`RunTime` Column:**
    * Converted from `float64` to an **integer (`int32`)** data type, effectively truncating any decimal points (e.g., "120.0" became "120"). No `NaN` values were present.
* **`start_year` & `end_year` Columns:**
    * Converted from `float64` to **integer (`int32`)** data types, as they did not contain `NaN` values and only had trailing decimals (e.g., "2020.0" became "2020").
* **Duplicate Entries in `MOVIES`:**
    * Identified 1553 duplicate movie titles, representing 221 unique duplicated titles.
    * Upon inspection (as seen with "13 Reasons Why" and "3Below: Tales of Arcadia"), these "duplicates" were determined to be **individual episodes or seasons of TV series** rather than redundant entries for single movies.
    * **Decision:** For the purpose of this practice, these individual episode/season entries were **retained** as distinct data points, acknowledging that the `MOVIES` column sometimes refers to a series title.
* **Text Column Standardization (`GENRE`, `ONE-LINE`, `STARS`):**
    * All entries were converted to **lowercase** for consistency in text analysis.
    * Leading and trailing whitespace was removed using `.str.strip()`.
    * For `GENRE` and `STARS`, initial cleaning focused on consistent casing and trimming; further complex parsing (e.g., splitting multi-genre strings into lists) was noted as a potential next step for more advanced analysis.
    * Punctuation removal was noted as a potential step for `ONE-LINE` depending on future text analysis goals.

## Key Analyses & Insights

After the data cleaning phase, the dataset is well-structured for various analyses. Initial exploratory steps included:

* **Data Type Verification:** Confirmed that all numerical columns are now correctly typed (`int32`, `float64`), enabling accurate calculations and sorting.
* **Sorting by Rating:** The entire dataset was sorted by the `RATING` column in **descending order (highest rating first)**, providing an immediate view of the top-rated films/episodes.
* **Data Export:** The cleaned and sorted DataFrame was successfully exported to an Excel file (`movies_sorted_by_rating.xlsx`) for easy viewing and sharing, with the DataFrame index column excluded.

## Files in this Repository
* `movie.csv`: The main movies dataset.
* `movie.ipynb`: The main Jupyter Notebook containing all the Python code for data loading, cleaning, and initial analysis.
* `movies_sorted_by_rating.xlsx`: The cleaned DataFrame, sorted by `RATING` (highest first), exported to an Excel file.
* `README.md`: This file, providing an overview of the project.
* `.gitignore`: A configuration file that tells Git which files and directories to ignore (e.g., temporary files, environment folders).

## How to Run the Code

To execute the analysis presented in this repository:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/zelvf/movie-data-cleaning-practice.git](https://github.com/zelvf/movie-data-cleaning-practice.git)
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd movie-data-cleaning-practice
    ```
3.  **Install dependencies:**
    Make sure you have `pandas` installed. If not, you can install it using pip:
    ```bash
    pip install pandas numpy
    ```
4.  **Place your dataset:** Ensure your original movie dataset (e.g., `movies.csv`) is in the same directory as the Jupyter Notebook.
5.  **Open the Jupyter Notebook:**
    ```bash
    jupyter notebook movies.ipynb
    ```
6.  Run all cells sequentially within the notebook to perform the data loading, cleaning, and analysis steps.

## Requirements

The code was developed using **Python 3.x** and relies on the following core libraries:

* `pandas` (for data manipulation and analysis)
* `numpy` (for numerical operations, used implicitly by pandas)
