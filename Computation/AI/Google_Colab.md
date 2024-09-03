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
