# 2022-inflation-inequity-data

Methodology for data cleaning and analysis for Philadelphia Inquirer's "TK INFLATION HEADLINE STORY", published June 11th, 2022.

## Project goal

This project seeks to explain **inflation inequality** and the effects on inflation on people in different income groups. The conclusion is that although high-income households bear a larger inflationary burden compared to low-income households in absolute dollar amounts. Taking into account the income of these households, however, show that inflation hits lower-income households harder since additional inflation expenditures take up a larger proportion of the income of lower-income households.

### Staff involved

Kindly contact Jasen Lo ([email](jlo@inquirer.com), [Twitter](https://twitter.com/jasenlo123)) or Francois Barrilleaux ([Twitter](https://twitter.com/FrenchwaEB)) with concerns and questions. 

### Data sources

This project uses two United States Bureau of Labor Statistics (BLS) datasets:
- [Consumer Price Index (CPI), Northeast Region – May 2022](https://www.bls.gov/regions/mid-atlantic/news-release/consumerpriceindex_northeast.htm)
    - The BLS CPI report is published monthly and provides inflation rate figures for expenditure categories for specific regions. 
    - This story uses the Northeast Region since Philadelphia lies within the region. The Northeast region is comprised of Connecticut, Maine, Massachusetts, New Hampshire, New Jersey, New York, Pennsylvania, Rhode Island, and Vermont.
- [Table 3104. Northeastern region by income before taxes: Average annual expenditures and characteristics, Consumer Expenditure Surveys (CES), 2019-2020](https://www.bls.gov/cex/tables/cross-tab/mean/cu-region-by-income-northeast-2020.pdf)
    - The BLS CES report is published annually and provides average expenditure and income figures for households of different income groups, as well as estimated expenditures of each income group for various categories.
    - This story uses the data from two income groups.
      - Low-income group is the population of households that earns between $15,000 − $30,000.
      - High-income group is the population of households that earns between $100,000− $149,999.   

### Project setup instructions

After cloning the git repo:

1. `pipenv shell` and `pipenv install` to create virutal environment and install dependencies.
2. `jupyter notebook` to view `etl_analysis.ipynb`. The resulting data should reflect the latest BLS CPI figures, which are released monthly on the 11th.

*Note that `Java 8+` is required to run [`tabula-py`](https://tabula-py.readthedocs.io/en/latest/getting_started.html#requirements), one of the dependencies of the project.*

## Data notes

1. Note that when `housing` expenditures are discussed in the story, this technically refers to `shelter` expenditures, which describe rent or mortage payments and accounts for how high income households usually hold property and low income households usually rent. This distinction is required because `housing` expenditures are inclusive of utilities and other housing-related expenditures. 

2. Note that `transportation` expenditure are inclusive of fuel costs, public transportation costs and the price of new and used vehicles. `Gas` costs, which fall into the fuels category, are distint from the natural gas costs used in household contexts like heat and cooking, which are accounted for as utilities in housing expenditures.

3. The expenditure categories in the Consumer Price Index and Consumer Expenditure Surveys have different names. The calculation of the additional expenditure due to inflation figure for both income groups required breaking down some categories into subcategories to calcualte the additional expenditure due to inflation for each category. Key that was used for the various category names:

| Consumer Price Index      | Consumer Expenditure Survey |
| ----------- | ----------- |
| Food at home      | Food at home       |
| Food away from home	   | Food away from home	        |
| Alcoholic beverages     | Alcoholic beverages       |
| Shelter	   | Shelter	        |
| Household furnishings and operations      | Household operations + Housekeeping supplies +  Household furnishings and equipment       |
| Fuels and utilities	   | Utilities, fuels, and public services	        |
| Apparel      | Apparel and services       |
| Motor fuel   | Gasoline, other fuels, and motor oil	        |
| Medical care	   | Healthcare	        |
| Recreation	   | Entertainment	        |
| Education and communication	   | Education	        |
| Other goods and services	   | Personal care products and services + Reading + Tobacco products and smoking supplies + Miscellaneous + Cash contributions + Personal insurance and pensions	        |

