# AgentECI

This is the official implementation for the paper "Agent Neuro-Symbolique pour l’Identification de Relations Causales"

# Usage
```bash
git clone https://github.com/nlp-uoregon/meci-dataset.git data/MECI
```

## Dataprep
Replace your_account/your_repo with your huggingface repository path of choice 
```bash
read -s -r -p "Enter your Hugging Face token: " HF_TOKEN
export HF_TOKEN

python3 -m data.MECI_dataprep \
  --root_dir data/MECI/meci-v0.1-public \
  --exclude 1_10ecbplus.xml \
  --seed 42 \
  --test_size 0.1 \
  --repo_id your_account/your_repo   

python3 -m data.dataprep_llm_format --dataset account/your_repo
```

## Launch the test (Check/Modify the config first)
Replace your_account/your_repo with your huggingface repository path of choice
```bash
read -s -r -p "Enter your Open Router API key: " OPENROUTER_API_KEY
export OPENROUTER_API_KEY
read -s -r -p "Enter your Langsmith API key: " LANGCHAIN_API_KEY
export LANGCHAIN_API_KEY

python3 main.py --repo_id your_account/your_repo 
```