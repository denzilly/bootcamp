# Pandas Section

create a df
pd.DataFrame(vals,index,vals,index)

selecting and indexing

df['index']

drop a col or row
df.drop('index', axis=n)

select a row
df.loc['index']

or based on position
df.iloc[index]

subset of rows and cols (submatrix)
df.loc[['A','B'],['W','Y']]

conditional selection

df><


ex- select all rows where val w>0
df[df['W']>0]

select col Y from all rows where val w>0
df[df['W']>0]['Y']


More indexing


reset indices to 0...n
df.reset_index()


Change indices
1. newind = ' a b c d '.split()
2. add new col with inices df['newind'] = newind
3. change ind to new ind col df.set_index('newind')



Multi-index and index hierarchy

set index levels:
outside = ['a', 'a', 'a', 'b', 'b', 'b']
inside = [1,2,3,1,2,3]

note: zip creates tuples containing ((a,1),(a,2), etc)


hier_index = list(zip(outside,inside))
hier_index = pd.MultiIndex.from_tuples(hier_index)


df = pd.Dataframe(np.random.randn(6,2),index=hier_index,columns=["A","B"])

df.loc['a'] will return all a

df.loc['a'].loc[1] will return first row of a

you can give the indices names

df.index.names = ['Group','Num']



## Dealing with Missing Data


drops all rows with NaN
df.dropna()

drops all columns with NaN
df.dropna(axis=1)

set the threshhold of NaN allowance
df.dropna(thresh=2)

replace nans with something
df.fillna(value='fill value')


## Grouping

groupby allows you to group rows of data together and call aggregate functions

sample df:
data = {'Company':['GOOG','GOOG','MSFT','MSFT','FB','FB'],
       'Person':['Sam','Charlie','Amy','Vanessa','Carl','Sarah'],
       'Sales':[200,120,340,124,243,350]}
df = pd.DataFrame(data)

df.groupby('Company')

you can save the groupby as a variable:

by_comp = df.groupby('company')

and then call methods on it
by_comp.mean()

will find means aggregated by Company similar to df.groupby('company').mean()
other methods: min(), max(), describe(), transpose(), count(), std()



# Merging, Joining, and Concatenating

concatenate dataframes with same col-indices (gluing, basically)
pd.concat([df1,df2,df3])


merging dataframes

pd.merge(left,right,how='inner',on='key')





Joining

To combine dataframes with different indices

keeps indices from df1
df1.join(df2)

df1.join(df2, how='outer')
keeps both, fills in NaN


# Operations

list unique values in a row or col
df['col2'].unique()

count unique values in a row or col
df['col2'].nunique()

both  .value_counts()

can apply head(n) t o show first n values from the list

# Selecting DataFrame
select from df where col1 > 2 and col 2 === 444
newdf = df[(df['col1']>2) & (df['col2']==444)]


# Applying Functions

eg.
def times2(x):
  return x*2

df['col1'].apply(times2)

# Permanently deleting columns

del df['col1']


# Getting column and index names

df.columns

df.index  

Sorting and ordering

df.sort_values(by='col2')


Find Null or check for Nulls

df.isnull()

Drop nans
df.dropna()

Fill nans with something else

df.fillna('FILL')


# Data Input and Output


CSV

in
df = pd.read_csv('example')

out
df.to_csv('example', index=false)


Excel
in
pd.read_excel('Excel_sample.xlsx', sheetname='sheet1')
out
df.to_excel('excel.xlsx', sheet_name='Sheet1')


HTML
(reads tables off of a webpage and return a list of DataFrame objects)

Input
df = pd.read_html('url')

## Cross Section and other

pandas.xs(key=key,axis=int,level=index)

use this to get a cross section of data with multiple index levels

pd.idxmin() find the index at minimum value of selected indicator
