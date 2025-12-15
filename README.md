# 🧝‍♀️MARS

This repository contains the official implementation of the following paper:

🎉🎉[ *AAAI-26* ] **MARS: Multi-Agent Adaptive Reasoning with Socratic Guidancefor Automated Prompt Optimization**  

arXiv: https://arxiv.org/abs/2503.16874



We propose a Multi-Agent Approach Integrating Socratic Guidance (MARS). Specifically, our multi-agent architecture autonomously plans the optimization path to mitigate uncertainty and employs a "teacher-critic-student" Socratic guidance interaction pattern to iteratively optimize the prompts while providing interpretability. 

----------------------------------------------


## 📌 Environment Setup Guide

This project supports both `pip` and `conda` for environment setup. Choose the method that suits your setup.

### 🔹 Method 1: Using `requirements.txt` 

If you are using **pip**, follow these steps to install all dependencies:

```bash
# Install dependencies
pip install -r requirements.txt
```

### 🔹 Method 2: Using `environment.yml` --[Recommend!]

If you are using **conda**, follow these steps:

```bash
# Create a conda environment from environment.yml
conda env create -f environment.yml

# Activate the environment
conda activate MultiAgent
```



## 💡How to Run 

To run the model, please use the following command.

### 🔹 step 1: Configuring the OpenAI API key

Configure your API Key in the ***Config.py*** file and select the model you want to use as the base

```python
API_KEY = "---YOUR_API_KEY---"
BASE_URL = "---YOUR_BASE_URL---"
MODEL = "deepseek-chat" # anyone you want
```



### 🔹 step 2: Setting up the test dataset(optional)

Set the test dataset corresponding to the task you chose in ***config.py***.

```python
# For example
DATASET_PATH = './Dataset_format/BBH/geometric_shapes.csv'
```



### 🔹 step 3: Setting Prompts(optional)

Depending on the task you want to use, select the corresponding content from the ***Prompt/ALL_userproxy_task_input.md*** and ***Prompt/ALL_prompt_planner_template.md*** files to copy into ***Prompt/EDIT_1_userproxy_task_input.txt*** and ***Prompt/EDIT_2_prompt_planner_template.txt***.

Of course, if you want to optimize other tasks, you can also write the content in the ***Prompt/EDIT_1_userproxy_task_input.txt*** and ***Prompt/EDIT_2_prompt_planner_template.txt*** directly yourself.



### 🔹 step 4: Run the script

We have designed the program to support two question types. Exactly which one to use depends on the type of questions in the dataset.

If it is a choice question please run:

```bash
bash run.sh choice
```

If it is a short answer question, please run:

```bash
bash run.sh short_answer
```

The results of each run will be displayed in ***Output*** folder.

## 🗂️ Documentation

### Dataset 

The data used in this experiment are stored in two folders, ***Dataset*** and ***Dataset_format***. The Dataset folder stores the original dataset of the data used in this experiment, and the Dataset_format folder stores the processed data that can be used directly.

The data in Dataset_format is the result of processing the Dataset's corresponding task using the preprocess_XX.py file. The ***Preprocess/preprocess_XX.py*** file used to process the data is given here.



### Preprocess
The Preprocess folder holds the preprocessors used in the different tasks in this experiment, the results of running these programs have been placed in the ***Dataset_format*** folder.



### Work process

***run.sh***: script for automated execution of code optimization

***main_MARS***: The entry point of the program that implements the Agent calls.

***Agents***: the implementation methods of specific Agents.

***Config***: Stores various configuration parameters, file paths, and APIs for calling LLM.



### Results

The best prompt for all tasks after iteration is in the ***Optimized prompt*** folder.



## 📚 Citation

If you find this work useful in your research, please consider citing:

```bibtex
@article{zhang2025mars,
  title={Mars: A multi-agent framework incorporating socratic guidance for automated prompt optimization},
  author={Zhang, Jian and Wang, Zhangqi and Zhu, Haiping and Liu, Jun and Lin, Qika and Cambria, Erik},
  journal={arXiv preprint arXiv:2503.16874},
  year={2025}
}