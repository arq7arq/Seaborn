# Seaborn Cheat Sheet

This notebook is a beginner-friendly Seaborn cheat sheet. It shows how to load a dataset with Pandas and create scatter plots with Seaborn using `relplot`.

The examples are written in a Jupyter Notebook: `seaborn.ipynb`.

## Requirements

Install Pandas, Seaborn, and Jupyter before running the notebook:

```bash
pip install pandas seaborn notebook
```

Then start Jupyter:

```bash
jupyter notebook
```

Open `seaborn.ipynb` and run the cells from top to bottom.

## Import Libraries

```python
import pandas as pd
import seaborn as sns
```

| Library | Purpose |
| --- | --- |
| `pandas` | Loads and works with table-style data |
| `seaborn` | Creates statistical data visualizations |

## Load the Dataset

The notebook uses a CSV file named `housing.csv`.

```python
housing = pd.read_csv("./housing.csv")
housing.head()
```

`housing.head()` shows the first few rows of the dataset so you can quickly check that the file loaded correctly.

Make sure `housing.csv` is in the same folder as the notebook.

## Basic Scatter Plot

Create a scatter plot using longitude and latitude:

```python
g = sns.relplot(
    kind="scatter",
    data=housing,
    x="longitude",
    y="latitude"
)

g.set(title="Geographical location of housing in California")
```

This plots each housing record based on its geographic location.

## Scatter Plot with Color

Use `hue` to color points based on another column:

```python
g = sns.relplot(
    kind="scatter",
    data=housing,
    x="longitude",
    y="latitude",
    hue="median_house_value"
)

g.set(title="Geographical location of housing in California")
```

In this example, `hue="median_house_value"` colors the points by house value.

## Scatter Plot with Style

Use `style` to change the marker style based on a category:

```python
g = sns.relplot(
    kind="scatter",
    data=housing,
    x="longitude",
    y="latitude",
    style="ocean_proximity"
)

g.set(title="Geographical location of housing in California")
```

In this example, `style="ocean_proximity"` gives different marker styles to different ocean proximity categories.

## Scatter Plot with Color and Style

You can combine `hue` and `style` in the same plot:

```python
g = sns.relplot(
    kind="scatter",
    data=housing,
    x="longitude",
    y="latitude",
    style="ocean_proximity",
    hue="median_house_value"
)

g.set(title="Geographical location of housing in California")
```

This shows both:

- House value using color
- Ocean proximity using marker style

## `sns.relplot` Quick Reference

| Argument | Example | Meaning |
| --- | --- | --- |
| `kind` | `"scatter"` | Type of relational plot |
| `data` | `housing` | Dataset used for the plot |
| `x` | `"longitude"` | Column used for the x-axis |
| `y` | `"latitude"` | Column used for the y-axis |
| `hue` | `"median_house_value"` | Column used for point color |
| `style` | `"ocean_proximity"` | Column used for marker style |

## Main Concepts Practiced

- Importing Pandas and Seaborn
- Loading a CSV file with `pd.read_csv`
- Previewing data with `.head()`
- Creating scatter plots with `sns.relplot`
- Mapping columns to x-axis and y-axis values
- Using `hue` to show numeric or categorical differences with color
- Using `style` to show category differences with marker shapes
- Adding plot titles with `g.set(title=...)`

## Notes

- Seaborn works well with Pandas DataFrames.
- Column names must match the names in the dataset exactly.
- Use `hue` when color helps explain a pattern.
- Use `style` when you want to separate categories by marker shape.
- For geographic scatter plots, longitude usually goes on the x-axis and latitude on the y-axis.
