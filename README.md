# Just-Run
Enable multiple python environment work togather.

##Example
```python
# Windows 10
# python 3.6

import justrun as jr

# run work.py through python 3.12,
# - and get processing result in this python 3.6 script.
result = jr.call_version(
    312,
    r"path\to\work.py",
    params=[var, another_var]
)

```

