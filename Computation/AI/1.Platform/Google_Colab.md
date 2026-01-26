# Google Colab

## Import custom module
1. Mount drive
```
from google.colab import drive
drive.mount('/content/gdrive')
```

2. Append path to the list of paths that Colab has access to

```
import sys

sys.path.append('/content/gdrive/My Drive')
```


3. Import the module
```
import valuator as val
```

If necessary, inspect files
```
#!ls /content/gdrive/My\ Drive/*.py

#!cat '/content/gdrive/My Drive/valuator.py'
```
## Subdependencies
The import statements declared in the .py file will work.
For those modules installed by default in the environment like `pandas`, there is no need for reinstalling.
For those modules not pre-installed like `numpy_financial`, use `!pip install name_of_module` in the notebook.
F
