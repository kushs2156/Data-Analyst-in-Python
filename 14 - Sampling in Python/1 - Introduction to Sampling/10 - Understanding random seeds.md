1) Which statement about `x` and `y` is true?
```Python
import numpy as np
np.random.seed(123)
x = np.random.normal(size=5)
y = np.random.normal(size=5)
```
- The values of `x` are different from those of `y`.
2) Which statement about `x` and `y` is true?
```Python
import numpy as np
np.random.seed(123)
x = np.random.normal(size=5)
np.random.seed(123)
y = np.random.normal(size=5)
```
- `x` and `y` have identical values.
3) Which statement about `x` and `y` is true?
```Python
import numpy as np
np.random.seed(123)
x = np.random.normal(size=5)
np.random.seed(456)
y = np.random.normal(size=5)
```
- The values of `x` are different from those of `y`.