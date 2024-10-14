pip install squarify
import pandas as pd
import squarify
import matplotlib.pyplot as plt

# Load your data into a DataFrame
file_path = 'path_to_your/HW2.xlsx'  # Update with your file path
covid_data = pd.read_excel(file_path, sheet_name='COVID')

# Normalize data per million
covid_data['Cases per Million'] = covid_data['Total Cases'] / (covid_data['Population'] / 1_000_000)
covid_data['Mortality Rate'] = covid_data['Total Deaths'] / covid_data['Total Cases']

# Function to plot treemaps
def plot_treemap(values, labels, title):
    plt.figure(figsize=(10, 7))
    squarify.plot(sizes=values, label=labels, alpha=0.7)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Plot treemaps
plot_treemap(covid_data['Total Cases'], covid_data['Country'], 'Treemap of Total Cases')
plot_treemap(covid_data['Cases per Million'], covid_data['Country'], 'Treemap of Total Cases per Million')
plot_treemap(covid_data['Mortality Rate'], covid_data['Country'], 'Treemap of Mortality Rate')
