
# 911 Emergency Calls Analysis | Python & Data Visualization

An exploratory data analysis project focused on identifying patterns in emergency 911 calls, understanding incident categories, and examining how emergency demand varies by time and location.

Using Python, Pandas, NumPy, Matplotlib, and Seaborn, this project transforms emergency call records into visual insights that can support public safety analysis and operational planning.

## Project Overview

Emergency call data can reveal useful patterns about the frequency, type, timing, and geographic distribution of incidents.

This project explores 911 call records to answer questions such as:

- Which emergency categories generate the most calls?
- Which ZIP codes and townships have the highest call volumes?
- How does call frequency vary by hour of the day?
- Which days of the week experience higher call volumes?
- How do emergency calls vary across months?
- What recurring patterns can be observed through heatmaps and time-series visualizations?

## Objectives

- Perform exploratory data analysis (EDA) on emergency call records.
- Clean and prepare data for analysis.
- Extract meaningful information from timestamps.
- Analyze call volumes by incident category, time, and location.
- Create visualizations to identify recurring patterns.
- Demonstrate how Python-based analytics can support operational decision-making.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Data analysis and programming |
| Pandas | Data manipulation and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Charts and plotting |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Interactive analysis and documentation |

## Dataset Description

The project uses a 911 emergency calls dataset containing incident descriptions, timestamps, geographic coordinates, and location information.

### Main attributes

| Column | Description |
|---|---|
| `lat` | Latitude of the incident |
| `lng` | Longitude of the incident |
| `desc` | Description of the emergency call |
| `zip` | ZIP code associated with the call |
| `title` | Emergency category and incident title |
| `timeStamp` | Date and time of the call |
| `twp` | Township associated with the call |
| `addr` | Address associated with the call |
| `e` | Dataset indicator column |

The analysis also derives additional features, including:

- `Reason`: Broad emergency category such as EMS, Fire, or Traffic.
- `Hour`: Hour of the call.
- `Month`: Month of the call.
- `Day of Week`: Day on which the call occurred.
- `Date`: Calendar date extracted from the timestamp.

## Project Workflow

### 1. Data Loading and Inspection

- Imported the dataset using Pandas.
- Examined the dataset structure, data types, and sample records.
- Assessed missing values and data quality.

### 2. Data Preprocessing

- Converted timestamp strings into datetime objects.
- Extracted hour, month, day of week, and calendar date.
- Created a `Reason` feature from emergency titles.
- Prepared the data for grouped analysis and visualization.

### 3. Emergency Category Analysis

Analyzed the distribution of calls across major emergency categories:

- EMS
- Traffic
- Fire

Used count plots to compare incident frequencies and identify the most common category.

### 4. Geographic Analysis

Investigated call distribution by ZIP code and township to identify locations with relatively high call volumes.

### 5. Time-Based Analysis

Grouped emergency calls by:

- Hour of the day
- Day of the week
- Month
- Calendar date

Used these groupings to examine changes in emergency demand over time.

### 6. Data Visualization

Created visualizations using Matplotlib and Seaborn, including:

- Count plots for emergency categories.
- Line plots for monthly and daily call volumes.
- Time-series charts for daily activity.
- Heatmaps for calls by day and hour.
- Heatmaps for calls by day and month.
- Cluster maps to explore similarities in temporal call patterns.

## Key Findings

The commonly distributed version of this dataset contains 99,492 emergency call records. Its broad emergency categories have the following distribution:

| Emergency category | Number of calls |
|---|---:|
| EMS | 48,877 |
| Traffic | 35,695 |
| Fire | 14,920 |
| **Total** | **99,492** |

These counts show that EMS is the largest category in this dataset, followed by Traffic and Fire.

Other useful analytical outputs include the most frequent ZIP codes and townships, hourly call patterns, and differences in call volumes across weekdays and months.

*Note: Verify that these figures match the CSV file in this repository before treating them as final results.*

## Business and Operational Applications

The analytical techniques demonstrated in this project can help support:

- **Emergency resource planning:** Understand patterns in call demand.
- **Operational scheduling:** Investigate periods with higher call volumes.
- **Geographic planning:** Identify locations with relatively high recorded incident activity.
- **Data-driven decision-making:** Convert historical records into interpretable visual insights.
- **Public safety research:** Explore recurring patterns in emergency service requests.

The analysis is descriptive and does not establish causation or determine the actual level of emergency service coverage required.

## Getting Started

### Prerequisites

Install Python 3 and pip.

### 1. Clone the repository

```bash
git clone https://github.com/sm292/911_Calls.git
cd 911_Calls
```

### 2. Create a virtual environment (optional)

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

macOS or Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Launch Jupyter Notebook

Open the notebook included in the repository and run its cells sequentially.

```bash
jupyter notebook
```

Make sure the dataset CSV is available at the path referenced in the notebook.

## Future Improvements

- Develop an interactive dashboard using Streamlit or Power BI.
- Add more detailed geographic visualizations.
- Compare emergency categories across different time periods.
- Improve missing-value handling and data validation.
- Add automated summary reports and key performance indicators.
- Explore forecasting techniques for historical call volumes, with appropriate validation.
- Add a reproducible analysis script and dependency file.

## Skills Demonstrated

Python | Pandas | NumPy | Data Cleaning | Exploratory Data Analysis | Data Visualization | Datetime Feature Engineering | Statistical Analysis | Heatmaps | Time-Series Exploration | Business Analytics

## Disclaimer

This project is intended for educational and analytical purposes. Historical call frequency alone does not establish incident severity, emergency response quality, or the need for specific resource allocations.

## Author

**Sumit Mondal**

- GitHub: https://github.com/sm292
- Project Repository: https://github.com/sm292/911_Calls

---

If you find this project useful, feel free to star the repository or share feedback.
