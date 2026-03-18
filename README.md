# AgentECI

This is the official implementation for the paper "Agent Neuro-Symbolique pour l’Identification de Relations Causales"

# Usage
```bash
conda env create -f environment.yml
conda activate agenteci
```

## Dataprep
Replace YOUR_ACCOUNT/YOUR_REPO with your huggingface repository path of choice 
```bash
read -s -r -p "Enter your Hugging Face token: " HF_TOKEN
export HF_TOKEN

git clone https://github.com/nlp-uoregon/meci-dataset.git

python3 -m data.MECI_dataprep \
  --root_dir data/MECI/meci-v0.1-public \
  --exclude 1_10ecbplus.xml \
  --seed 42 \
  --test_size 0.1 \
  --repo_id YOUR_ACCOUNT/YOUR_REPO

python3 -m data.dataprep_llm_format --dataset YOUR_ACCOUNT/YOUR_REPO
```

## Launch the test (Check/Modify the config first)
Replace YOUR_ACCOUNT/YOUR_REPO with your huggingface repository path of choice
```bash
read -s -r -p "Enter your Open Router API key: " OPENROUTER_API_KEY
export OPENROUTER_API_KEY
read -s -r -p "Enter your Langsmith API key: " LANGCHAIN_API_KEY
export LANGCHAIN_API_KEY

python3 main.py --repo_id YOUR_ACCOUNT/YOUR_REPO
```
