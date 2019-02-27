# Plotly and Cufflinks

Plotly allows you to create interactive plots that you can use in dashboards or websites (saved as html files or static images)

sns.lmplot


Using Cufflinks and iplot()

  -  scatter
  -  bar
  -  box
  -  spread
  -  ratio
  -  heatmap
  -  surface
  -  histogram
  -  bubble


### Scatter

df.iplot(kind='scatter', x='A', y='B', mode='markers', size=10)


### Bar plots

df2.iplot(kind='bar', x='Category', y='Values')

df.count().iplot(kind='bar')


### Box plots

df.iplot(kind='box')

### 3d surface

df3 = pd.DataFrame({'x':[1,2,3,4,5],'y':[10,20,30,20,10],'z':[5,4,3,2,1]})
df3.iplot(kind='surface',colorscale='rdylbu')

### Spread (premium)

df[['A','B']].iplot(kind='spread')

### histogram

df['A'].iplot(kind='hist',bins=25)

bubble histogram

df.iplot(kind='bubble',x='A',y='B',size='C')
