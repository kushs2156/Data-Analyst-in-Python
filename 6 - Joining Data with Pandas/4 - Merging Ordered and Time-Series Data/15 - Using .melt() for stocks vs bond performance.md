- Use `.melt()` on `ten_yr` to unpivot everything except the `metric` column, setting `var_name='date'` and `value_name='close'`. Save the result to `bond_perc`.
- Using the `.query()` method, select only those rows where `metric` equals 'close', and save to `bond_perc_close`.
- Use `merge_ordered()` to merge `dji` (left table) and `bond_perc_close` on `date` with an inner join, and set `suffixes` equal to `('_dow', '_bond')`. Save the result to `dow_bond`.
- Using `dow_bond`, plot only the Dow and bond values.
```Python
# Use melt on ten_yr, unpivot everything besides the metric column
bond_perc = ten_yr.melt(id_vars='metric', var_name='date', 
							value_name='close')

# Use query on bond_perc to select only the rows where metric=close
bond_perc_close = bond_perc.query('metric == "close"')

# Merge (ordered) dji and bond_perc_close on date with an inner join
dow_bond = pd.merge_ordered(dji, bond_perc_close, how='inner', 
							on='date', suffixes=['_dow', '_bond'])

# Plot only the close_dow and close_bond columns
dow_bond.plot(kind='bar', x='date', y=['close_dow', 'close_bond']
				,rot=90)
plt.show()
```
![[download 32.svg]]
