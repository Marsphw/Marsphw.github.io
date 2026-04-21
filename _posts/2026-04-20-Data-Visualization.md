---
title: Data Visualization
date: 2026-04-20
categories: [Data Science]
tags: [Data Visualization, Python]
description: Data Visualization is a critical skill for data scientists. Here are some tools and techniques to help you visualize your data.
math: true
---

# Data Visualization

## Histograms

A **histogram** is a type of bar graph that represents the distribution of numerical data by showing the frequency of data points within a certain range of values (called **bins**). To build a histogram you need to follow the steps below. Suppose you have a dataset $\{x_i\}_{i = 1}^n$.

- **Determine the Number of Bins**: Choose the number of bins $k$. Several approaches exist, but for the moment let us suppose that we choose $k$ manually without any rule. 
- **Calculate the range of data**: Compute the range your dataset by subtracting the minimum value from the maximum value.
- **Determine the bin width**: Divide the range by the number of bins $k$ to find the bin width $= \frac{\text{range}}{k}$.
- **Create bin intervals**: Starting from the minimum data value, create bin intervals up to the maximum value, each with the calculated bin width. Your $i$-th interval $\Delta_i$ will be defined by 

$$
\Delta_i = \left[\min(x_i) + \frac{\text{range}}{k}(i - 1), \min(x_i) + \frac{\text{range}}{k}i\right)
$$

- **Count the number of data points in each interval $\Delta_i$ (bin)**: Count how many fall into each bin based on the established intervals. 
- **Draw the histogram**: Draw the histogram with bins on the horizontal axis and the counts of data points on the vertical axis. The height of each bin corresponds to the the number of data points it contains. 

## Boxplots

A **boxplot**, also known as a **box-and-whisker plot**, is a graphical representation of statistical data. In general, it serves the purpose of giving a condensed view of the distribution of the data by using graphically five numbers extracted from the data: (1) minimum (excluding outliers), (2) first quartile (Q1), (3) median (Q2), (4) third quartile (Q3), and (5) maximum (excluding outliers). The elements of a boxplot and a short discussion are reported below. 

<figure id = "boxplot">
  <img src="/assets/images/2026-04-20-Data-Visualization/boxplots.png" alt="BoxPlot">
  <figcaption>Fig1: The structure of a boxplot. The main elements that you will find in a boxplot are outliers, whiskers, the quartiles $Q1$, $Q2$, and $Q3$, the IQR, and the median. The axis indicates the values of the data (indicated with $x$), and its values are only indicatives. </figcaption>
</figure>

- **Box**: The main element of a boxplot is the central box that spans from $Q1$ to $Q3$ and represents how wide the central 50\% of the data are, providing insights into the distribution's dispersion and skewness thanks to the median line.
- **Whiskers**: Whiskers are typically represented as horizontal lines of the box until the single points. 
- **Minimum**: The smallest data point **excluding** any outliers is represented by the end of the left whisker (when vertically oriented as the lower) on [fig1](#boxplot) the small vertical lines that end the whiskers lines and are at roughly around;
- **Maximum**: The largest data point **excluding** outliers is represented by the end of the right whisker (or the top one if oriented vertically). 
- **Interquartile Range (IQR)**: It is defined as $Q3 - Q1$. This range covers the middle 50\% of the data and is a measure of statistical dispersion. It is the width (or height) of the box.  

There are mainly two ways of deciding how long whiskers should be: Tukey's and the standard deviation method. 
- **Tukey's method**: Whiskers extend to the last data point within 1.5 times the IQR from the quartiles.
- **Standard deviation method**: Whiskers extend to a specified number of standard deviations from the mean. 

The simplicity of boxplots also introduces certain limitations regarding the granularity of data they can display. Specifically, boxplots do not capture the finer details of a distribution's shape, such as its modality. Additionally, while boxplots show medians and spread, they do not show the mode or mean explicitly (unless added additionally). 

## $Q-Q$ Plots

$Q-Q$ stands for the Quantiles-Quantiles. The basic idea is to compare experimental quantiles (coming from data) to theoretical ones (coming from the expected distribution) and plot one versus the other. If the data are distributed according to the expected distribution, all points will be on the diagonal line in the plot; otherwise they will be far from the diagonal. 

## Pair Plots

A pair plot displays all the pairwise relationships between variables in a dataset, along with the distribution of each variable. This is typically done in a grid where each row and each column represent one variable. Each cell in the grid contains a scatter plot of the corresponding pair of variables, while the diagonal cells often contain the univariate distribution of the variables, such as histograms or kernel density plots. 

<figure id = "pair-plots">
  <img src="/assets/images/2026-04-20-Data-Visualization/pair_plot_iris.png" alt="Pair Plots">
  <figcaption>Fig2: A pair plot for the Iris dataset. For example, we can see that the petal\_width and petal\_length are highly correlated. On the contrary, sepal\_length and petal\_width are not correlated, as the points do not show any clear relationship.</figcaption>
</figure>

In [fig2](#pair-plots), we can see how such a plot looks like. Diagonal cells show the distribution of each variable, and off-diagonal cells show scatter plots of each pair of variables. 

Generally speaking, if you see a straight line (or almost a straight line) in a scatter plot, it indicates a linear relationship (correlation) between the variables. Different clusters in the scatter plots can indicate different groups or categories within the data. 

Pair plots are typically used for Exploratory Data Analysis (EDA). They are extremely useful for getting a quick overview of the relationships between multiple variables in our dataset. 