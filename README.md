#LLM EVALUATION MODEL
# LLM Comparison Tool

A Python tool for comparing the responses of Claude 3.5 Haiku with open-source language models using standard NLP evaluation metrics.

## Overview

This project provides a framework for quantitatively comparing the outputs of Anthropic's Claude API with open-source LLMs (such as DistilGPT-2). The tool generates responses to a set of prompts using both models and evaluates their similarity using several NLP metrics:

- BLEU score
- METEOR score
- ROUGE-1, ROUGE-2, and ROUGE-L scores
- Cosine similarity (TF-IDF based)

The results are saved to CSV files for further analysis.

## Features

- Connects to the Claude API for generating responses
- Loads and uses an open-source LLM (DistilGPT-2 by default)
- Evaluates model outputs using multiple standard NLP metrics
- Saves detailed comparison results to CSV
- Generates summary statistics of the evaluation

## Requirements

The tool requires Python 3.6+ and the following libraries:


anthropic
pandas
transformers
torch
nltk
rouge
scikit-learn
numpy


## Installation

1. Clone this repository:
bash
git clone https://github.com/yourusername/llm-comparison-tool.git
cd llm-comparison-tool


2. Install the required dependencies:
bash
pip install anthropic pandas transformers torch nltk rouge scikit-learn numpy


3. Set up your Anthropic API key (replace with your actual key in the code or use environment variables).

## Usage

1. Update the API key in the script:
python
client = anthropic.Anthropic(api_key="your-api-key-here")


2. Customize the prompts list to include the text prompts you want to evaluate:
python
prompts = [
    "What is artificial intelligence?",
    "Explain the difference between machine learning and deep learning.",
    # Add your own prompts here
]


3. Run the script:
bash
python llm_comparison.py


4. The script will generate two CSV files:
   - llm_comparison_with_metrics.csv: Contains all prompts, responses, and individual metrics
   - llm_metrics_summary.csv: Contains only the average values for each metric

## How It Works

1. For each prompt, the script:
   - Gets a response from Claude 3.5 Haiku
   - Gets a response from the open-source LLM
   - Calculates similarity metrics between the two responses
   
2. The metrics used are:
   - *BLEU*: Measures n-gram precision and is commonly used in translation evaluation
   - *METEOR*: Considers synonyms and stemming for more flexible matching
   - *ROUGE*: Measures recall of n-grams (how many n-grams in the reference appear in the candidate)
   - *Cosine Similarity*: Measures semantic similarity based on TF-IDF vectors

3. Average scores across all prompts are calculated to provide a summary view.

## Customization

- To use a different open-source model, change the model_name variable
- To modify the length of generated responses, adjust the max_tokens parameter for Claude and max_length for the open-source model
- Add or change the prompts to test different types of queries
