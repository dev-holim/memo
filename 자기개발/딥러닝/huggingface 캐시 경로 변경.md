
```
rm -rf ~/.cache/huggingface/hub/*
rm -rf ~/.cache/huggingface/transformers/*
```

```
mkdir -p /dev/shm/huggingface/{hub,transformers,datasets}
```

```
import os
os.environ["HF_HOME"] = "/dev/shm/huggingface"
os.environ["TRANSFORMERS_CACHE"] = "/dev/shm/huggingface/transformers"
os.environ["HF_DATASETS_CACHE"] = "/dev/shm/huggingface/datasets"
```