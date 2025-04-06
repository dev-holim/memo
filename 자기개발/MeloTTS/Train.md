
```bash
python3 preprocess_text.py --metadata data/KR-default/metadata.list
```


만들어진 config.json에 "data":{}에 아래 추가하기
```
"max_text_len": 999,
```

```bash
bash train.sh data/KR-default/config.json 2

torchrun --nproc_per_node=2 --master_port 10902 train.py --c data/KR-default/config.json --model KR-default --pretrain_G data/KR-default/G_0.pth --pretrain_D data/KR-default/D.pth --pretrain_dur data/KR-default/DUR.pth

torchrun --nproc_per_node=2 --master_port=10902 train.py --c data/KR-default/config.json --model KR-default --pretrain_G data/KR-default/G_0.pth --pretrain_D data/KR-default/D.pth --pretrain_dur data/KR-default/DUR.pth
```

```
python3 infer.py --text "테스트 상황을 만들어서 하고 있습니다. 알겠지?" -m data/KR-default/G_0.pth -o result
```