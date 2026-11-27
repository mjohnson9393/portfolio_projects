# Understanding the Autism Spectrum Through Data

![Dashboard](autismcasestudychart.pdf)

A case study using public data to show that autism presents along a spectrum, who is represented in screening data, and how identification has changed over time. Built with Python (pandas) and Tableau.

**Files:** [`autism_analysis.ipynb`](autism_analysis.ipynb) (Python notebook) • `autism_clean.csv` • `autism_prevalence.csv` • dashboard PDF and image

## Ask
1. How are AQ-10 screening scores (0-10) distributed across respondents, and what percentage fall in each range (0-3, 4-6, 7-10)?
2. How do average AQ-10 scores differ by gender and age group (17-29, 30-44, 45+)?
3. How has the CDC's identified autism prevalence among 8-year-olds changed from 2000 to 2022?

## Prepare
- [Autism Screening Adult dataset](https://archive.ics.uci.edu/dataset/426) (UCI Machine Learning Repository): 704 respondents, 21 columns
- [CDC ADDM Network prevalence data](https://www.cdc.gov/autism/data-research/): combined prevalence per 1,000 children by surveillance year, 2000-2022 (entered manually into a CSV)

## Process
- Checked for missing values: `age` was missing 2 values, and `ethnicity` and `relation` were each missing 95 (unused in this analysis)
- Found an impossible age value (383) and removed it along with the 2 missing ages, leaving 701 rows for the age and gender analysis
- Relabeled gender values and created age groups and score ranges for analysis and visualization

## Analyze
- **Scores fall along a range.** Respondents scored at every point from 0 to 10, peaking at 4. About 33% scored 0-3, 40% scored 4-6, and 27% scored 7-10, with no clear split into two groups.
- **Group differences are small.** Average scores ranged from 4.52 to 5.61. Women scored slightly higher in the 17-29 and 30-44 groups, and men aged 45+ had the highest average (5.61).
- **Identified prevalence has risen sharply.** It went from 6.7 per 1,000 8-year-olds in 2000 to 32.2 per 1,000 in 2022, about 4.8 times higher.

## Share
An interactive Tableau dashboard combines all three charts (see image above).

## Act
For people unfamiliar with autism, the data supports a few points: traits appear along a continuum rather than in two groups, average screening scores look similar across age and gender groups, and the rise in identified prevalence is tied to awareness and diagnosis as well as how common autism is.

## Limitations
- AQ-10 scores are screening results, not diagnoses, and respondents chose to take the screening, so they may not represent the general population.
- The 45+ group is small (59 people), so its average is less reliable.
- CDC figures show *identified* prevalence, which reflects diagnostic practices and awareness. The number of reporting sites also changed over time (6 in 2000, 16 in 2022), so years aren't perfectly comparable.
- The Tableau dashboard uses the 701 cleaned rows, while the score range percentages above use all 704 respondents.

## Tools
Python (pandas, Google Colab) • Tableau • GitHub
