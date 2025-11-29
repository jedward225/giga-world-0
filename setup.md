
```bash
git clone git@github.com:jedward225/giga-world-0.git
cd giga-world-0/
uv venv --python 3.11.10
source .venv/bin/activate
uv pip install giga-train giga-datasets natten -i https://pypi.tuna.tsinghua.edu.cn/simple
git clone https://github.com/open-gigaai/giga-models.git
cd giga-models
uv pip install -e .
cd ..
mkdir models
python scripts/download.py --model-name video_pretrain --save-dir models/
uv pip install huggingface_hub
huggingface-cli login
huggingface-cli download open-gigaai/GigaWorld-0-Video-Pretrain-2b --local-dir /home/jjliu/giga-world-0/models/transformer

python scripts/inference.py --data-path /home/jjliu/giga-world-0/assets/it2v.json --save-dir /home/jjliu/giga-world-0/outputs/ --transformer-model-path   /home/jjliu/giga-world-0/models/transformer/transformer --text-encoder-model-path /home/jjliu/giga-world-0/models/text_encoder --vae-model-path /home/jjliu/giga-world-0/models/vae --gpu_ids 0
```