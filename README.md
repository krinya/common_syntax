# Commands that I use very often

It is focused on Pandas because I work a lot with it.
This can be helpful for both beginners and experienced users to improve their data manipulation skills. Below, I'll provide explanations for each command you've listed to help you with your article:

### Show all columns in pandas
```python
pd.set_option('display.max_columns', None)
```
This command sets the display option to show all columns in a Pandas DataFrame, regardless of their number. It is particularly useful when working with datasets that have a large number of columns, as it ensures you can view all columns without truncation.

### Show all rows in pandas
```python
pd.set_option("max_rows", None)
```
Similar to the previous command, this sets the display option to show all rows in a Pandas DataFrame, allowing you to view the entire dataset without any truncation.

### Group by and create new variables in the existing data
```python
data['new_column_name'] = data.groupby('grouping_column')['calculating_on_this_column'].transform('nunique')
```
This line of code groups the DataFrame data by the values in the 'grouping_column' and then calculates the number of unique values in the 'calculating_on_this_column' for each group. The transform method applies this calculation to each row in the original DataFrame, and the result is assigned to a new column named 'new_column_name'.

### Group by and create new variables
```python
df.groupby(['grouping_col1', 'grouping_col2']).agg(
    new_name1=('variable1', 'sum'),
    new_name2=('variable2', 'sum')
).reset_index()
```
This code groups the DataFrame df by two columns ('grouping_col1' and 'grouping_col2') and then aggregates the values in 'variable1' and 'variable2' using the 'sum' function. It creates a new DataFrame with the aggregated values, where the columns are renamed to 'new_name1' and 'new_name2', respectively.

### Group by and apply multiple functions
```python
data_grouped = data.groupby(grouping_columns).agg(
    mean_price=(variable_column, 'mean'),
    median_price=(variable_column, 'median'),
    quantile=(variable_column, lambda x: np.percentile(x, q=95))
).reset_index()
```
This code groups the DataFrame data by the columns specified in grouping_columns. It then applies three different aggregation functions to the 'variable_column': mean, median, and the 95th percentile using a custom lambda function. The aggregated results are stored in the 'mean_price', 'median_price', and 'quantile' columns, respectively.

### How to use apply in group by
The provided code demonstrates how to use the apply method in combination with a custom function to perform complex group by operations. It applies several custom functions (count_new, mean_new, and auc_group) to the groups created by the specified columns ('group1' and 'group2'). The results are then concatenated into a new DataFrame using the aggfunc function.

### How to append pandas Dataframes
```python
pd.concat([df1, df2.rename(columns={'b': 'a'})], ignore_index=True)
```
The code uses pd.concat to concatenate two DataFrames, df1 and df2. The rename method is used to change the column name 'b' in df2 to 'a' to align the columns properly before concatenation. The ignore_index=True parameter ensures that the resulting DataFrame has a new index without preserving the original indices.

### How to merge a dictionary to a DataFrame
```python
df['colname'].apply(lambda x: a_dict.get(x, "NA"))
```
This code uses the apply method on the 'colname' column of the DataFrame df to apply a lambda function to each element. The lambda function looks up the value of each element in the dictionary a_dict and returns the corresponding value. If a value is not found in the dictionary, it returns "NA" as a default.

### Sort pandas DataFrame
```python
df.sort_values(by=['colname'], ascending=False)
```
This command sorts the DataFrame df based on the values in the 'colname' column in descending order (due to ascending=False). It rearranges the rows of the DataFrame, so the largest values in the 'colname' column appear at the top.

### Rename column(s)
```python
df = df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'})
```
This code renames columns in the DataFrame df. It changes the names of 'oldName1' and 'oldName2' columns to 'newName1' and 'newName2', respectively.

### Join pandas DataFrames
```python
combined_df = pd.merge(
    frame_1, frame_2,
    how='left',
    left_on=['county_ID'], right_on=['countyid'])
```
This code performs a left join on frame_1 and frame_2 DataFrames, merging them based on the common columns 'county_ID' in frame_1 and 'countyid' in frame_2. The resulting DataFrame is stored in combined_df.

With these explanations, you can create a comprehensive article/blog post about the most frequently used commands and syntax in Python Pandas, along with examples to illustrate their practical usage. Happy writing!

