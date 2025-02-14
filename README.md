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

# Steps to deploy finetuned fb-125m model on MLIS
* create registry and add huggingface token
* create packaged model
    * select custom model format, name model `finetuned-opt-125m`
    * enter image: `mendeza/vllm-openai:0.0.1` this is a custom VLLM container that support CPU only deployment
    * In advanced, add environment variable `HUGGING_FACE_HUB_TOKEN` and enter hugging face token in value
    * For resources, select `cpu tiny`
    * paste the following to the arguments text field: `--model mendeza/opt-125m-synthetic-finetuned --dtype bfloat16 --port 8080`
* create deployment
    * create deployment named: `finetuned-opt-125m`
    * select package model named `finetuned-opt-125m`
    * for scaling select fixed-1
    * for advanced, add two environment variables:
        * Name: `CPU`, value: `10`
        * Name: `Memory`, value: `10Gi`
