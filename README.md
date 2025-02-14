# Finetune and deploy LLMs on MLIS

# Requirements:
* Need PCAI environment to create a notebook server and notebooks
* Need PCAI environment that has MLIS deployed

# Environment install instructions
* `pip install vllm datasets 'accelerate>=0.26.0'`
* for torchtune, install: `pip install torchtune torchao bitsandbytes`

# Main demo: finetune and deploy llm 
* create notebook server: 2 vCPU and 20GB of Memory
* run cells in `ft.ipynb` to show finetuning
* go to MLIS, show deployed endpoint
* go to Tokens tab on the left, and copy the token in `finetuned-opt-125m`
* go back to `ft.ipynb` and run the cell to paste token interactively
* run cell in `ft.ipynb` to make API request of deployed finetuned model

# ToDo (add instructions to setup MLIS deployment)