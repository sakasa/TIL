# 改行なしで `print` する
```python
print("HOGE", end="")
```

# 関数の型ヒント
```python
def func(x: int, y: str) -> str:
    """
    Parameters
    ----------
    x : int
    y : str
    
    Returns
    -------
    z : str
    """
```
※ヒントなの実際の型が異なっていてもエラーにならない

# ディレクトリにパスを通す
参考：https://qiita.com/Kunikata/items/45e731753e97bda28aab
- ディレクトリ構成
```
/xxx/yyy
  |- /execute.py
  `- /module
      `- /module1.py
```
- execute.py
```python
import sys
sys.path.append('/xxx/yyy/module')

import module1.py
module1.method()
```

