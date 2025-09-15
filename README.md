<div align="center">
  <img src="./assets/logo.png" width="40%">
</div>

<p align="center">
  <a href="https://www.arxiv.org/abs/2503.01940">Paper</a> |
  <a href="https://huggingface.co/NUMB1234/AskToAct-7B">Model</a> |
  <a href="#fine-tuning">Fine-Tuning</a> 
<!--   <a href="#evaluation">Evaluation</a>  -->
</p>


## Overview
**AskToAct** is a self-correcting clarification framework that directly addresses the challenge of **handling unspecified queries** in tool-use scenarios. It enables LLMs to: (1) identify when a query lacks critical information,   (2) interactively elicit missing intent through clarification, and   (3) recover from common errors during multi-turn interactions.


To support scalable research and development, we release:

- **A high-quality dataset** comprising clarification dialogues with built-in error correction, along with a dedicated test set of unspecified queries paired with ground-truth annotations.

- Full **training and evaluation scripts** to reproduce our results or benchmark new models.


## Fine-Tuning

### Setup

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

Please ensure that [examples/my_lora_sft.yaml](https://github.com/NUMB1234/AskToAct/blob/main/LLaMA-Factory/examples/my_lora_sft.yaml), [examples/my_lora_merge.yaml](https://github.com/NUMB1234/AskToAct/blob/main/LLaMA-Factory/examples/my_lora_merge.yaml), [examples/my_full_sft.yaml](https://github.com/NUMB1234/AskToAct/blob/main/LLaMA-Factory/examples/my_full_sft.yaml), and [data/dataset_info.json](https://github.com/NUMB1234/AskToAct/blob/main/LLaMA-Factory/data/dataset_info.json) are all properly configured before training.



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
