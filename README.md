# 2022-inflation-inequality-data

Methodology for data cleaning and analysis for Philadelphia Inquirer's "TK INFLATION HEADLINE STORY", published June 11th, 2022.

## Project goal

This project seeks to explain **inflation inequality** and the effects of inflation on people in different income groups. Although high-income households bear a larger inflationary burden compared with low-income households in absolute dollar amounts, taking income into account shows inflation hits lower-income households harder: Inflation costs take up a larger proportion of the income of lower-income households.

## Staff involved

Contact Jasen Lo ([email](jlo@inquirer.com), [Twitter](https://twitter.com/jasenlo123)) or Francois Barrilleaux ([Twitter](https://twitter.com/FrenchwaEB)) with concerns and questions. 

## Data sources

This project uses two U.S. Bureau of Labor Statistics (BLS) data sets:
- [Consumer Price Index (CPI), Northeast Region – May 2022](https://www.bls.gov/regions/mid-atlantic/news-release/consumerpriceindex_northeast.htm)
    - The CPI report is published monthly and provides the inflation rate for expenditure categories for specific regions. This is the source for how prices are rising for different types of goods and services.
    - This story uses the Northeast Region, which includes Philadelphia. The Northeast Region is comprised of Connecticut, Maine, Massachusetts, New Hampshire, New Jersey, New York, Pennsylvania, Rhode Island, and Vermont.
- [Table 3104. Northeastern region by income before taxes: Average annual expenditures and characteristics, Consumer Expenditure Surveys (CES), 2019-2020](https://www.bls.gov/cex/tables/cross-tab/mean/cu-region-by-income-northeast-2020.pdf)
    - The CES report is published annually and provides data on expenditures and incomes for households of different income groups. This is the source for the breakdown of how different income groups spend their money across various categories.

## Project setup instructions

After cloning the git repo:

1. `pipenv shell` and `pipenv install` to create virutal environment and install dependencies.
2. `jupyter notebook` to view `etl_analysis.ipynb`. The resulting data should reflect the latest BLS CPI figures, which are released monthly on the 11th.

*Note that `Java 8+` is required to run [`tabula-py`](https://tabula-py.readthedocs.io/en/latest/getting_started.html#requirements), one of the dependencies of the project.*

## Data notes
1. This story uses data from two income groups:
      - The low-income households are those that earn between $15,000 and $30,000.
      - High-income households earn between $100,000 and $149,999.

2. The `housing` category in the story refers to `shelter` expenditures, which describe rent or mortage payments and accounts for how high-income households usually hold property and low-income households usually rent. We exclude some data in the BLS `housing` expenditures category, which includes utilities and other housing-related expenditures. 

2. The `transportation` category in the story includes the costs of buying fuel, paying for public transportation, and purchasing new and used vehicles. `Gas` costs fall into the fuels subcategory of transportation and are distinct from the natural gas costs used in household contexts like heat and cooking, which are counted as utilities within housing expenditures.

3. The expenditure categories in the CPI and CES data have different names. Calculating the inflation costs required matching categories that may not perfectly align, and in some cases meant using subcategories to be as aligned as possible. Here’s how we lined up the categories:

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

