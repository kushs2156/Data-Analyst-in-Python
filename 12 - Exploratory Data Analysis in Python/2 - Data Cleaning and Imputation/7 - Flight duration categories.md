- Create a list of categories containing `"Short-haul"`, `"Medium"`, and `"Long-haul"`.
- Create `short_flights`, a string to capture values of `"0h"`, `"1h"`, `"2h"`, `"3h"`, or `"4h"` taking care to avoid values such as `"10h"`.
- Create `medium_flights` to capture any values between five and nine hours.
- Create `long_flights` to capture any values from 10 hours to 16 hours inclusive.
```Python
# Create a list of categories
flight_categories = ["Short-haul", "Medium", "Long-haul"]

# Create short-haul values
short_flights = "^0h|^1h|^2h|^3h|^4h"

# Create medium-haul values
medium_flights = "^5h|^6h|^7h|^8h|^9h"

# Create long-haul values
long_flights = "10h|11h|12h|13h|14h|15h|16h"
```
