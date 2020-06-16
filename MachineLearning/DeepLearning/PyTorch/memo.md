## モデルの保存
```python
save_path = './dir/file.pth'
torch.save(model.state_dict(), save_path) # 学習済みモデルパラメータ, 保存先パス
```

## モデルの読み込み
```python
load_path = './dir/file.pth'
model = ModelClass(*args, **kwargs)
model.load_state_dict(torch.load(load_path))
```

### GPU上で保存されたパラメータをGPU上でロードする場合
```python
load_path = './dir/file.pth'
model = ModelClass(*args, **kwargs)
model.load_state_dict(torch.load(load_path, map_location={'cuda:0': 'cpu'}))
```

