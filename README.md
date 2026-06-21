# NHL Seasons Data Analysis Project

This project was made for my Data Analyst course. The goal was to scrape historical NHL season data, clean the dataset and perform a exploratory data analysis, including descriptive statistics, data visualization, and a baseline sports betting odds estimation model.

## Project Files

* **`NHL_scrape.ipynb`**: Jupyter Notebook containing the web scraping script used to collect the data.
* **`NHL_analysis.ipynb`**: Jupyter Notebook containing the data cleaning, analysis, visualizations, and odds modeling.
* **`NHL_seasons_combined.csv`**: The primary analysis dataset. It contains NHL regular season statistics from **1990 to 2025** (excluding the 2004–2005 season, which was canceled due to the NHL lockout). You can run the analysis notebook with this file alone.

## How to run

1. Clone the repository and open the project directory.
2. Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

3. Start Jupyter and open `NHL_analysis.ipynb`:

```bash
jupyter notebook
```

4. Run the notebook from the cell that loads `NHL_seasons_combined.csv`. The combined CSV in the repository is the primary dataset for analysis.

Optional: run `NHL_scrape.ipynb` first if you want to regenerate season CSVs from Hockey-Reference. That notebook requires Google Chrome and a compatible ChromeDriver.

## Libraries & Tools Used

The following Python libraries were used for web scraping, file management, data manipulation and visualization:

* **Web Scraping & Automation**: `selenium`, `time`
* **File & Directory Management**: `pathlib`
* **Data Manipulation**: `pandas`, `numpy`
* **Data Visualization**: `matplotlib`, `seaborn`

## Data Source

All data was scraped from [Hockey-Reference](https://hockey-reference.com). 

### Data Dictionary

The dataset includes the following variables:

| Variable | Description |
| **Rk** | Rank |
| **AvAge** | Average age of the team weighted by time on ice |
| **GP** | Games Played |
| **W** | Wins |
| **L** | Losses |
| **OL** | Overtime/Shootout Losses (tracked from the 2000 season onward) |
| **PTS** | Points |
| **PTS%** | Points percentage (total points divided by maximum possible points) |
| **GF** | Goals For |
| **GA** | Goals Against |
| **SOW** | Shootout Wins |
| **SOL** | Shootout Losses |
| **SRS** | Simple Rating System (factors in average goal differential and strength of schedule; 0 is league average) |
| **SOS** | Strength of Schedule (schedule difficulty rating; 0 is league average) |
| **GF/G** | Goals For Per Game |
| **GA/G** | Goals Against Per Game |
| **PP** | Power Play Goals |
| **PPO** | Power Play Opportunities |
| **PP%** | Power Play Percentage |
| **PPA** | Power Play Goals Against |
| **PPOA** | Power Play Opportunities Against |
| **PK%** | Penalty Killing Percentage |
| **SH** | Short-Handed Goals |
| **SHA** | Short-Handed Goals Against |
| **PIM/G** | Penalties in Minutes Per Game |
| **oPIM/G** | Opponent Penalties in Minutes Per Game |
| **S** | Shots on Goal |
| **S%** | Shooting Percentage |
| **SA** | Shots Against |
| **SV%** | Save Percentage |
| **SO** | Shutouts |

---

## Analysis & Questions Answered

### 1. League & Team Demographics
* How many teams have participated in league games over the years?
* What is the total number of seasons in the dataset?
* How many teams have participated in every single season?
* How did the average age of players changed over the years?

### 2. Historical Performance
* Which teams have the highest win percentage in NHL history?
* In which seasons did the regular season winner achieve the highest winrate?
* Which teams won the regular season most frequently?
* Which teams have never won a regular season?
* Which teams have the most play-off appearences?

### 3. Overtime Metrics
* What is the total number of overtime losses accumulated by each team?
* Which teams lost in overtime most frequently?
* What percentage of teams have lost in overtime at least once?
* Which seasons had the most overtimes played?

### 4. Statistical Distributions & Scoring Trends
* **Goals Ratio & Victory Percentage Analysis**: Calculation of Mean, Standard Deviation, and Quantiles (2nd, 3rd, 4th).
* **Histograms**: Plotting goal ratios using Rice's Rule vs. Square Root Rule for bin selection, histogram for victory percentages.
* **Correlations & Scatterplots**: 
  * Win Percentage vs. Goal Ratio
  * Shots vs. Goals For
* How have Goals Per Game changed across the years?

### 5. Betting Odds Estimation
* **Performance Tier Assignment**: Teams are classified into 4 performance categories:
  * **Tier A**: Top 5% of teams.
  * **Tier B**: Teams performing better than 70% of the league (excluding Tier A).
  * **Tier C**: Teams performing better than 20% of the league (excluding Tiers A & B).
  * **Tier D**: The remaining bottom teams.
* **Odds Calculation**: Determination of the global baseline probability of any team winning (rounded to two decimals) and calculation of custom odds per performance tier.

---

## Discussion

1. **Simplifications & Omissions**: What elements of the analysis were simplified or completely omitted?
2. **Odds Inconsistencies**: Are there any structural flaws or contradictions in the estimated betting odds?
3. **Improving Estimates**: How can the mathematical framework for the odds estimation be improved?
4. **Data Enrichment**: How can the initial dataset be expanded to make future risk estimates more accurate and less risky?
5. **Risk Simulation**: How can we simulate the outcomes of this analysis to mathematically verify that they would not lead to financial losses in a real betting scenario?
