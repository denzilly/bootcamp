# Pandas Built-In Data Visualisation Tools


## Stylesheets

You can create a 'stylesheet' for your plots to follow to make everything look a little bit nicer

plt.style.use('stylename')

make a histogram

df1['a'].hist()

call stylesheet, it looks different

plt.style.use('bmh')
df1['A'].hist()


## Built-In Plot Types

  - df.plot.area
  - df.plot.barh
  - df.plot.density
  - df.plot.hist
  - df.plot.line
  - df.plot.scatter
  - df.plot.bar
  - df.plot.box
  - df.plot.hexbin
  - df.plot.kde
  - df.plot.pie


area
df2.plot.area(alpha=0.4)

bar

df2.plot.bar()
stacked
df2.plot.bar(stacked=True)

Histogram
df1['A'].plot.hist(bins=50)

line
df1.plot.line(x=df1.index,y='B',figsize=(12,3),lw=1)

scatter
df1.plot.scatter(x='A',y='B')
df1.plot.scatter(x='A',y='B',c='C',cmap='coolwarm')

scaled dot size
df1.plot.scatter(x='A',y='B',s=df1['C']\*200)


Boxplot
df2.plot.box() # Can also pass a by= argument for groupby

Hexagonal Bin plot
df = pd.DataFrame(np.random.randn(1000, 2), columns=['a', 'b'])
df.plot.hexbin(x='a',y='b',gridsize=25,cmap='Oranges')


kde
df2['a'].plot.kde()
df2.plot.density()
