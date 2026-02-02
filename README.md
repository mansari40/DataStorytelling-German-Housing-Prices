# Understanding German Housing Market Divergence (1964-2025)

A comprehensive data storytelling project analyzing long-term housing price developments across German cities, examining regional disparities, temporal trends, and macroeconomic relationships.

The HTML file can be found in the `docs` folder under file name `dsv.html` and can also be viewed online [here](https://mansari40.github.io/DataStorytelling-German-Housing-Prices/dsv.html).

## Project Overview

This research project investigates how housing prices have evolved across approximately 21 German cities over a 61-year period (1964-2025). The analysis reveals significant regional divergence, particularly after 2010, and examines the relationship between housing price dynamics and key macroeconomic indicators including gross domestic product, long-term interest rates, and unemployment rates.

The project employs rigorous data cleaning methodologies, temporal interpolation, and visual analytics to explore whether housing prices develop similarly across regions or whether regional differences have increased substantially over time. The central research questions include:

1. How have housing prices developed across German cities during the analysis period?
2. Have cities experienced convergent or divergent price trajectories?
3. Can macroeconomic factors explain observed variations in housing price growth?
4. How do property type segments (apartments, single-family houses, multi-family houses) influence market dynamics?

## Research Findings

The analysis identifies several key findings:

- Housing prices across German cities exhibited convergent trends until approximately 2010, suggesting alignment with national economic conditions.
- Post-2010 divergence has been pronounced, with selected metropolitan areas (Munich, Frankfurt, Hamburg) significantly outpacing the national average (GREIX), while smaller markets experienced stagnation or decline.
- Price growth acceleration occurred simultaneously across all property type segments post-2010, indicating macroeconomic forces dominate segment-specific factors.
- Regional price inequality has widened substantially, particularly in the apartment segment, with the ratio of most-to-least expensive cities increasing over the analysis period.
- Cities demonstrating below-median prices did not reliably converge toward higher-priced markets, contradicting simplistic mean-reversion hypotheses.
- Strong housing price increases correlate with periods of low interest rates and declining unemployment, yet housing price growth cannot be solely explained by aggregate economic growth.

## Dataset Description

### Primary Data Sources

**German Real Estate Index (GREIX)**
- Transaction-based housing prices for 21 German cities
- Coverage period: 1964-2025 (varying by city and property type)
- Three property type segments: Apartments, Single-family houses, Multi-family houses
- Data quality: Real (inflation-adjusted) and nominal prices

**Macroeconomic Indicators**
- Real GDP (World Bank, annual frequency)
- Long-term interest rates (European Central Bank)
- Unemployment rates (Federal Employment Agency/Destatis)

### Data Characteristics

- Time period: 1964-2025 (61 years)
- Geographic coverage: 21 German cities (excluding Berlin due to data completeness issues)
- Frequency: Annual observations
- Missing data treatment: Linear interpolation within cities; property-type median fill for residual gaps
- Inflation adjustment: CPI-adjusted to real terms

## Project Structure

```
DataStorytelling-German-Housing-Prices/
├── README.md                          # Project documentation
├── requirements.txt                   # Python dependencies
├── styles.css                         # Custom styling for web output
├── _config.yml                        # GitHub Pages configuration
├── _quarto.yml                        # Quarto project settings
├── dsv.qmd                            # Quarto markdown report source
│
├── Data/
│   ├── GREIX_all_cities_data.xlsx     # Main housing price dataset
│   ├── GDP 1960-2024.csv              # GDP indicators
│   └── Long term interest rate-Germany.csv  # Interest rate data
│
├── src/
│   ├── main/
│   │   └── main.ipynb                 # Jupyter notebook with full analysis
│   │
│   └── additional/
│       ├── GDP_vs_Housing.ipynb       # GDP analysis
│       ├── Housing_vs_Inflation.ipynb # Inflation analysis
│       ├── Housing_vs_InterestRates.ipynb  # Interest rate analysis
│       └── Housing_vs_Unemployment.ipynb   # Unemployment analysis
│
├── docs/                              # Generated static website
│   ├── index.html                     # Main report
│   ├── dsv.html                       # Alternate report format
│   └── site_libs/                     # Web assets
│
└── .git/                              # Version control
```

## Methodology

### Data Preparation

1. Data Import and Validation: Excel-based GREIX dataset loaded and structure verified
2. City Exclusion: Berlin excluded from primary analysis due to systematic incompleteness (>50% missing price observations)
3. Temporal Interpolation: Linear interpolation applied within each city to address missing values
4. Property-Type Imputation: Median price by property type applied to residual gaps
5. Temporal Aggregation: Annual average prices calculated by city, year, and property type

### Analytical Approaches

**Descriptive Analysis**
- Distribution analysis of housing prices across cities and time periods
- Summary statistics by property type and temporal segments

**Comparative Analysis**
- City-level price trajectory comparison relative to national average (GREIX)
- Identification of top and bottom performers across temporal windows (2004-2014, 2014-2024)
- Growth rate calculations and ranking analysis

**Dispersion Analysis**
- Quantile-based price dispersion bands (10th, 25th, 50th, 75th, 90th percentiles)
- Ratio analysis (most to least expensive city prices by year)
- Inequality trend measurement

**Convergence Testing**
- Mean-reversion analysis comparing above-median and below-median price cities
- Examination of 2-year-ahead price growth by initial price positioning

**Visualization Methods**
- Time series plots with focus/context design
- Faceted city-level panels with comparative context
- Interactive Plotly visualizations for multidimensional exploration
- Quantile band visualization for distributional analysis

## Technical Implementation

### Technologies

- **Python 3.x**: Primary analysis language
- **Jupyter Notebook**: Interactive exploratory analysis and documentation
- **Quarto**: Publication-quality report generation and website deployment
- **Pandas**: Data manipulation and aggregation
- **NumPy**: Numerical computations
- **Matplotlib**: Static visualization creation
- **Seaborn**: Statistical visualization
- **Plotly**: Interactive visualizations

### Reproducibility

The project can be rebuilt entirely using:

- Jupyter notebooks for exploratory analysis (src/main/main.ipynb)
- Quarto document for publication report (dsv.qmd)

To reproduce the analysis:

```bash
# Install dependencies
pip install -r requirements.txt

# Run Jupyter notebook
jupyter notebook src/main/main.ipynb

# Generate Quarto report
quarto render dsv.qmd

# Generate website
quarto render
```

## Output and Deliverables

### Interactive Jupyter Notebook
- Location: src/main/main.ipynb
- Contents: Full exploratory data analysis with inline visualizations
- Code folding enabled for readability

### Supplementary Analysis Notebooks
- GDP correlation analysis: src/additional/GDP_vs_Housing.ipynb
- Inflation relationship: src/additional/Housing_vs_Inflation.ipynb
- Interest rate effects: src/additional/Housing_vs_InterestRates.ipynb
- Unemployment dynamics: src/additional/Housing_vs_Unemployment.ipynb

### Published Web Report
- HTML publication: docs/index.html
- Hosted via GitHub Pages
- Features: Code folding, table of contents, interactive visualizations, responsive design

### Presentation
- Slide deck available at: https://www.canva.com/design/DAG8ogHZKSo/nK6EFs-p901AJ74QD0Qg2A/edit

## Key Visualizations

The analysis includes the following major visualizations:

1. **Price Distribution Analysis**: Histograms and density plots of housing prices across all cities and property types
2. **Time Series Trajectories**: Individual city price trends (1965-2025) with national average context
3. **City Performance Rankings**: Top and bottom performers relative to GREIX across distinct temporal periods
4. **Property Type Trends**: National-level price evolution by property segment
5. **City-Level Faceted Panels**: 21 individual city charts with context reference layer
6. **Segment-Specific Analysis**: Property type rankings and growth distributions
7. **Price Inequality Trends**: Max-to-min price ratios demonstrating widening inequality
8. **Quantile Dispersion Bands**: Distribution evolution across percentile ranges
9. **Mean Reversion Analysis**: Below-median vs above-median city growth trajectories
10. **Interactive Dashboards**: Plotly-based interactive visualizations with dropdown controls

## Data Quality Notes

- Berlin excluded from primary analysis due to systematic incompleteness exceeding 50% missing observations
- Treated separately for qualitative interpretation where applicable
- Temporal interpolation assumes smooth price evolution within cities
- Property-type median imputation preserves structural market differences
- No missing values remain after cleaning procedures

## Installation and Setup

### Requirements
- Python 3.8 or higher
- pip or conda package manager
- Quarto (optional, for report generation)

### Setup Instructions

```bash
# Clone repository
git clone https://github.com/mansari40/DataStorytelling-German-Housing-Prices.git
cd DataStorytelling-German-Housing-Prices

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install Quarto (optional)
# Visit https://quarto.org/docs/get-started/
```

## Usage

### Running Jupyter Analysis
```bash
jupyter notebook src/main/main.ipynb
```

### Generating Quarto Report
```bash
quarto render dsv.qmd --to html
```

### Building Website
```bash
quarto render
```

## Authors

- Mustafa Ansari
- Mitali Acharya
- Sai Arun

## Data Attribution

- German Real Estate Index (GREIX): https://greix.de
- GDP data: World Bank (https://data.worldbank.org)
- Interest rates: European Central Bank (https://data.ecb.europa.eu)
- Unemployment rates: Federal Employment Agency / Destatis

## Citation

If you use this project or findings in your research, please cite as:

Ansari, M., Acharya, M., & Arun, S. (2025). Understanding German Housing Market Divergence (1964-2025).

## License

This project is provided for educational and research purposes.

## Contact and Support

For questions or inquiries regarding this project, please contact the project authors or submit issues via the GitHub repository.

## Repository Information

- Repository: https://github.com/mansari40/DataStorytelling-German-Housing-Prices
- Branch: main

