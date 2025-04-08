# python script
 vgsales-analysis
# vgsales_analysis.py

import pandas as pd

# Load the dataset
df = pd.read_csv("vgsales.csv")

# Drop rows with missing 'Year' or 'Publisher'
df.dropna(subset=["Year", "Publisher"], inplace=True)

# Group by Genre and calculate total global sales
genre_sales = df.groupby("Genre")["Global_Sales"].sum().sort_values(ascending=False)

# Display top 5 genres by global sales
print("Top 5 Game Genres by Global Sales:")
print(genre_sales.head())
