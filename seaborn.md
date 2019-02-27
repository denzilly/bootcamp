# Seaborn

## Distribution Plots

Load data set
tips = sns.load_dataset('tips')

## Distplot

univariate distribution

sns.distplot(tips['total_bill'])



## jointplot

Match up two distplots for bivariate dataf. "Kind" is parameter type

eg scatter
sns.jointplot(x='total_bill',y='tip',data=tips,kind='scatter')

or hex
sns.jointplot(x='total_bill',y='tip',data=tips,kind='hex')


## pairplot

plot pairwise relationships along an entire dataframe

sns.pairplot(tips)

with colors

sns.pairplot(tips, hue='sex', palette='coolwarm')


#rugplot

dash mark for every point on a univariate Distribution

sns.rugplot(tips['total_bill'])


## kdeplot

kernel density estimation plots - replace every single observation with a Gaussian distribution centered around that values

To get the kde plot we can sum these basis functions.

Plot the sum of the basis function
sum_of_kde = np.sum(kernel_list,axis=0)

 Plot figure
fig = plt.plot(x_axis,sum_of_kde,color='indianred')

 Add the initial rugplot
sns.rugplot(dataset,c = 'indianred')

 Get rid of y-tick marks
plt.yticks([])

 Set title
plt.suptitle("Sum of the Basis Functions")

sns.kdeplot(tips['total_bill'])
sns.rugplot(tips['total_bill'])


## Barplot and Countplot

bar chart
sns.barplot(x='sex', y='total_bill',data=data)

just counts
sns.count(x='sex', ,data=data)


## Boxplot and violinplot

sns.boxplot(x='day', y='total bill', data=tips, palette='rainbow')
sns.boxplot(x="day", y="total_bill", hue="smoker",data=tips, palette="coolwarm")

sns.violinplot(x="day", y="total_bill", data=tips,palette='rainbow')


## Stripplot and Swarmplot
sns.stripplot(x="day", y="total_bill", data=tips)




# Matrix plots

Data should already be in matrix form, basically sns makes a heatmap of your matrix

sns.heatmap(data.corr(), cmap='coolwarm',annot=true)

or a pivottable

flights.pivot_table(values='passengers',index='month',columns='year')

# Clustermap
basically an unordered matrix plot in which categories are clustered by a certain qualifier, like similarity in count

sns.clustermap(data)


# Grids

Allow you to to map plot types to rows and columns in a grid, so that you can compare them

create grid

g = sns.PairGrid(data)

map scatters to grid
g.map(plt.scatter)

map to certain areas of the Grids
g.map_diag(plt.hist)
g.map_upper(plt.scatter)
g.map_lower(sns.kdeplot)

pairplot
sns.pairplot(data)
is a simpler version of grid--


## Facet Grid

Create grids of plots based off of a feature

g = sns.FacetGrid(tips, col="time", row="smoker")
g = g.map(plt.hist, "total_bill")
g = g.map(plt.scatter, "total_bill", "tip").add_legend()


# Regression plots

sns.lmplot(x="total_bill", y='tip',data=tips)

sns.lmplot(x='total_bill', y='tip', data=tips, hue='sex', palette='coolwarm')

sns.lmplot(x='total_bill',y='tip',data=tips,col='day',hue='sex',palette='coolwarm',
          aspect=0.6,size=8)


# Multiple graphs side-by-side

use FacetGrid
g = FacetGrid(data=data,col='sex')
g.map(plt.hist,'age')
