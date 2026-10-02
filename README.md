
# Sampling Methods Comparison

## Overview

This project compares three sampling methods using the Iris dataset:

- **Stratified Sampling**
- **Reservoir Sampling**
- **Full Random Sampling** (used as a baseline)

The experiment examines how the methods represent the dataset's species groups and how closely the numerical feature means of each sample match the full dataset.

## Dataset

The experiment uses the Iris dataset, containing 150 records and five columns:

- `sepal_length`
- `sepal_width`
- `petal_length`
- `petal_width`
- `species`

**Dataset source:**

https://raw.githubusercontent.com/mwaskom/seaborn-data/master/iris.csv

It contains 50 records for each of the three species: setosa, versicolor, and virginica.

## Methods

### 1. Stratified Sampling

The dataset is divided into groups based on `species`. The notebook takes 20% from each group, producing a sample of 30 records with 10 records per species.

### 2. Reservoir Sampling

A custom reservoir sampling function reads the CSV one row at a time and maintains a fixed-size sample of 30 records. This demonstrates how to sample from a stream without loading the entire dataset into memory.

### 3. Full Random Sampling

A random sample of 30 records is selected from the complete dataset. This provides a baseline for comparison.

## Evaluation

The notebook compares the methods using:

1. **Species distribution:** Compares the proportion of each species in the original dataset and each sample.
2. **Numerical feature means:** Compares the sample means for sepal length, sepal width, petal length, and petal width against the full-dataset means.
3. **Absolute error:** Calculates the absolute difference between each sample mean and the corresponding full-dataset mean.

## Results

For the recorded run, the average absolute errors were:

| Method | Average Absolute Error |
|---|---:|
| Stratified Sampling | 0.0372 |
| Reservoir Sampling | 0.0438 |
| Full Random Sampling | 0.0858 |

In this run, stratified sampling had the smallest average absolute error across the four numerical features. Reservoir sampling had the smallest error for petal length.

These results depend on the particular sample and random seed used. They do not prove that one method will always produce the smallest error.

## Tools and Libraries

- Python
- Google Colab
- pandas
- NumPy
- Python `random` and `csv` modules
- Matplotlib

## How to Run

1. Open `Sampling_Methods_Comparison.ipynb` in Google Colab or Jupyter Notebook.
2. Run the cells from top to bottom.
3. The notebook loads the Iris CSV from the URL above, creates the samples, and produces the comparisons and visualizations.

An internet connection is needed to load the dataset from the URL.

## Repository Contents

- `Sampling_Methods_Comparison.ipynb` — Notebook containing the code, outputs, comparisons, and conclusions.
- `README.md` — Project overview and instructions.

## Conclusion

This experiment illustrates the different purposes of the sampling methods. Stratified sampling controls representation across known groups, while reservoir sampling maintains a fixed-size random sample from a stream. Full random sampling serves as a baseline.

The numerical results are specific to this experiment and should be interpreted as a comparison of this run, rather than a general ranking of the methods.
