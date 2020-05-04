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
