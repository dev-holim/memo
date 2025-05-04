```python
train_ft["smoker"] = train["smoker"].map(lambda x : int(x == "yes"))
```