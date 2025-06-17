<div align="center">
  <img src="./assets/logo.png" width="40%">
</div>

<p align="center">
  <a href="https://www.arxiv.org/abs/2503.01940">Paper</a> |
  <!-- <a href="">Model</a> | -->
    <!-- <a href="">Usage</a> | -->
  <a href="">Fine-Tuning</a> |
  <!-- <a href="">Evaluation</a> | -->
</p>


## Fine-Tuning

### Installation


```bash
conda create -n taskbench python=3.10
conda activate asktoact
cd LLaMA-Factory
pip install -e ".[torch,metrics]"
```

### Train the Model

After setting up the training environment, you can train the model using [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory). 

Run LoRA fine-tuning:
```
llamafactory-cli train examples/my_lora_sft.yaml
```
After fine-tuning, merge the LoRA adapter into the base model:
```
llamafactory-cli export examples/my_lora_merge.yaml
```

Run full-parameter fine-tuning:
```
llamafactory-cli train examples/my_full_sft.yaml
```

**Note:** Please ensure that `examples/my_lora_sft.yaml`, `examples/my_lora_merge.yaml`, `examples/my_full_sft.yaml`, and `data/dataset_info.json` are all properly configured before training.



## Citation

If you find this work useful in your method, you can cite the paper as below:
```
@misc{zhang2025asktoactenhancingllmstool,
      title={AskToAct: Enhancing LLMs Tool Use via Self-Correcting Clarification}, 
      author={Xuan Zhang and Yongliang Shen and Zhe Zheng and Linjuan Wu and Wenqi Zhang and Yuchen Yan and Qiuying Peng and Jun Wang and Weiming Lu},
      year={2025},
      eprint={2503.01940},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2503.01940}, 
}
```