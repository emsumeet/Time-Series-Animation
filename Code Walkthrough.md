# Code Walkthrough
1. Data Cleaning

#### Read and filter raw dataset
```bash
df = pd.read_csv('./data/un-country-data.csv')
countries = df[df['ISO3_code'].notnull()]
columns = ['ISO3_code', 'Location', 'Time', 'TPopulation1Jan', 'TPopulation1July']
clean_df = countries[columns]
```
#### Scale population fields to millions
```bash
clean_df['TPopulation1Jan'] = clean_df['TPopulation1Jan'] / 1000
clean_df['TPopulation1July'] = clean_df['TPopulation1July'] / 1000
```
##### Save cleaned dataset
```bash
clean_df.to_csv('./data/cleaned-data.csv', index=False)
```

2. Static Visualization

#### Filter for year 1950 and top 10 populous countries
```bash
pop_data = pd.read_csv('./data/cleaned-data.csv')
pop_data_1950 = pop_data[pop_data['Time'] == 1950]
top_countries = pop_data_1950.nlargest(10, 'TPopulation1Jan').sort_values('TPopulation1Jan', ascending=True)
```

#### Create horizontal bar chart
```bash
plt.barh(top_countries['Location'], top_countries['TPopulation1Jan'])
plt.show()
```

3. Animated Visualization
```bash
def create_animation(df):
    frames = df['Time'].unique()
    fig, ax = plt.subplots(figsize=(12, 6))
    
    def animate(frame):
        ax.clear()
        top_countries = df[df['Time'] == frame].nlargest(10, 'TPopulation1Jan').sort_values('TPopulation1Jan', ascending=True)
        ax.barh(top_countries['Location'], top_countries['TPopulation1Jan'])
        setup_plot_style(ax)
        add_year_text(ax, frame)

    anmi = animation.FuncAnimation(fig, animate, frames=frames, interval=200)
    return anmi
```
