# Just-Run
*"Your python version is too old for this package..."*

*"Your python version is too new for this package..."*

*"You should switch the python-version of your project and pray it won't crash..."*

**Shut up and just run it !**

---

You can call python scripts with different versions of the python interpreter, and get the returned data.

It enable multiple python environment to work togather, even though they have different versions!

## Install
```
pip install justrun
```
Every python environment that have to work with another, 
should installed a copy of **justrun**.

## Example - call by version number

caller.py *(Python 3.6)*
```python
# Windows 10
# python 3.6

import justrun as jr

# run worker.py through python 3.12 (that you already installed),
# - and get the processing result in this python 3.6 script.
result = jr.call_version(
    312,                        # in Linux/MacOS it should be "3.12" or 3.12
    r"path\to\worker.py",
    params=[var, another_var]
)
```

worker.py *(Python 3.12)*
```python
# Windows 10
# python 3.12

import justrun as jr

# get parameters from other python interpreter.
params = jr.get_params()

# do your work here with Python 3.12
# ...

# and send back the processing result to Python 3.6.
jr.return_data(your_processing_result)
```

## Another Example - call by python path

caller.py
```python
# Windows 10
# python 3.6

import justrun as jr

# run worker.py through specified python virtual environment (created with any version),
# - and get processing result in this python 3.6 script.
result = jr.call_pathon(
    r"path\to\your\python312\environment",    # such as r"c:\python-sandbox\312-myvenv"
    r"path\to\worker.py",
    params=[var, another_var]
)
```

This method allow you to run .py through specified python virtual environment, instead of main environment.

## limitations

Only supports passing Python native data types between scripts, such as: ***int***, ***str***, ***dict***, ***bytes***, ...
  
**Custom instance are not supported yet**.
