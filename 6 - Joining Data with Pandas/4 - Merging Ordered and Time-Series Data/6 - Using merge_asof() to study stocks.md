- Use `merge_asof()` to merge `jpm` (left table) and `wells` together on the `date_time` column, where the rows with the **_nearest_** times are matched, and with `suffixes=('', '_wells')`. Save to `jpm_wells`.
- Use `merge_asof()` to merge `jpm_wells` (left table) and `bac` together on the `date_time` column, where the rows with the closest times are matched, and with `suffixes=('_jpm', '_bac')`. Save to `jpm_wells_bac`.
- Plot the close prices of `close_jpm`, `close_wells`, and `close_bac` from `price_diffs`.
```Python
# Use merge_asof() to merge jpm and wells
jpm_wells = pd.merge_asof(jpm, wells, on='date_time', 
					direction='nearest', suffixes=['', '_wells'])

# Use merge_asof() to merge jpm_wells and bac
jpm_wells_bac = pd.merge_asof(jpm_wells, bac, on='date_time', 
					direction='nearest', suffixes=['_jpm', '_bac'])

# Compute price diff
price_diffs = jpm_wells_bac.diff()

# Plot the price diff of the close of jpm, wells and bac only
price_diffs.plot(y=['close_jpm', 'close_wells', 'close_bac'])
plt.show()
```
![[download 28.svg]]
