# 乱数シード値の固定
参考：https://qiita.com/sugulu/items/c0e8a5e6b177bfe05e99
```python
import os
import random
import numpy as np
import torch

SEED_VALUE = 1234  # これはなんでも良い
os.environ['PYTHONHASHSEED'] = str(SEED_VALUE)
random.seed(SEED_VALUE)
np.random.seed(SEED_VALUE)
torch.manual_seed(SEED_VALUE)  # PyTorchを使う場合

# PyTorchでGPUを使用する場合
torch.backends.cudnn.deterministic = True
torch.backends.cudnn.benchmark = False
```
- scikit-learnの場合は各アルゴリズムで乱数シードを受けつる部分もある
```python
from sklearn.linear_model import LogisticRegression

SEED_VALUE = 1234  # これはなんでも良い
clf = LogisticRegression(random_state=SEED_VALUE)
```
