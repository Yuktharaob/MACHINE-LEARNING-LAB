# MACHINE-LEARNING-LAB



## _LAB 01_


Develop a program to create Histograms for all numerical features and analyze the distribution of each 
feature. Generate Box plots for all Numerical Features and identify any Outliers. Use California Housing 
dataset. 

### *COMPONENTS OF PROGRAM*
 
1. [Modules used to solve the given question](#)
2. [Importing california dataset](#) 
3. [Convert to a Pandas DataFrame and include the target column](#)
4. [Display basic information about the dataset](#)
5. [Print the first 10 rows of the dataset with house prices](#)
6. [Generate Histograms for all numerical features](#)
7. [Generate Box Plots to identify outliers](#)

### 1. Modules used to solve the given question-

```python
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt 
import seaborn as sns 
from sklearn.datasets import fetch_california_housing
``` 

* numpy: A library for numerical computing, providing support for large multi-dimensional arrays and matrices, and offering a variety of mathematical functions.

* pandas: A library for data manipulation and analysis, offering data structures like Series and DataFrame for handling structured data.

* matplotlib.pyplot: A plotting library for creating static, interactive, and animated visualizations in Python.

* seaborn: A statistical data visualization library built on top of matplotlib, providing a high-level interface for drawing attractive and informative statistical graphics.

* sklearn.datasets: A module in scikit-learn for loading standard datasets, including real-world datasets for machine learning practice.

### 2. Importing california dataset

```python 
california = fetch_california_housing()
```
This line of code will load the California Housing dataset into the california variable using the fetch_california_housing function from the sklearn.datasets module. This dataset includes various features related to housing in California.

### 3. Convert to a Pandas DataFrame and include the target column

```python
data = pd.DataFrame(california.data, columns=california.feature_names)
```
*Creates a DataFrame*: This line converts the data from the California Housing dataset into a DataFrame.

*Data and Columns*: california.data contains the feature data, and california.feature_names provides the names of these features, which become the column headers of the DataFrame.

```python 
data["MedHouseValue"] = california.target 
```
*Adds a Target Column*: This line adds a new column named "MedHouseValue" to the DataFrame.

*Median House Value*: california.target contains the target variable data, which represents the median house value for each entry in the dataset.

### 4. Display basic information about the dataset

```python 
print("Dataset Information:\n") 
print(data.info())
```

### 5. Print the first 10 rows of the dataset with house prices

```python 
print("\nFirst 10 Rows of the Dataset:\n") 
print(data.head(10)) 
``` 
### 6. Generate Histograms for all numerical features

```python 
plt.figure(figsize=(12, 8)) 
```
 **o** *Create a New Figure*: This line creates a new figure with a specified size of 12 inches by 8 inches. It sets up the canvas for plotting.

```python
data.hist(bins=30, figsize=(12, 8), edgecolor='black', color='skyblue') 
```
**o** *Create Histograms*: This line generates histograms for all numerical features in the DataFrame data.

&nbsp;&nbsp;&nbsp;&nbsp; bins=30: Specifies the number of bins (intervals) for the histogram.

&nbsp;&nbsp;&nbsp;&nbsp; figsize=(12, 8): Sets the size of each subplot to 12 inches by 8 inches.

&nbsp;&nbsp;&nbsp;&nbsp; edgecolor='black': Adds a black edge color to the bars.

&nbsp;&nbsp;&nbsp;&nbsp; color='skyblue': Fills the bars with a sky blue color.

```python
plt.suptitle("Histograms of All Numerical Features", fontsize=16) 
```
**o** *Set Super Title*: This line sets the overall title for the figure, indicating that the histograms represent all numerical features. The font size is set to 16.

```python
plt.show() 
```

**o** *Display the Plot*: This line displays the figure with all the histograms.

### 7. Generate Box Plots to identify outliers

```python 
plt.figure(figsize=(12, 8)) 
for i, col in enumerate(data.columns): 
    plt.subplot(3, 3, i+1) 
    sns.boxplot(y=data[col], color='lightcoral') 
    plt.title(col) 
    plt.ylabel('') 
    plt.tight_layout() 
plt.suptitle("Box Plots of All Numerical Features", fontsize=16) 
plt.show()
```

* Create a New Figure: This line creates a new figure with a specified size of 12 inches by 8 inches, setting up the canvas for plotting.
* Loop Through Columns: This line begins a loop over each column in the DataFrame, assigning the loop index to i and the column name to col.
* Create Subplots: This line creates a 3x3 grid of subplots and selects the (i+1)th subplot. It allows multiple plots to be displayed in the same figure.
* Generate Box Plot: This line creates a box plot for the column col using the Seaborn library. The box plot is colored light coral.
* Set Title: This line sets the title for the subplot to the column name.
