# 🧠 Computer Use AI Agent 

## 📋 Overview
This project consists of a lightweight Python script that explores how AI agents are able perform complex tasks using computer inputs--like file access, app usage, or browser searching. The main framework was inspired by Paras Madan's code which can be found [here](https://medium.com/gopenai/computer-use-ai-agent-tutorial-full-code-browser-use-beb54cf1f525)

------

## ⚡️ Features -- What does the code do? 
#### The code for this project can be broken down into 5 steps: 
1. Request a Prompt from the User
2. Convert the Task into a Series of Actions
3. xecute the AI-Generated Plan Using `browser-use`
4. Implement Re-try Logic
5. Build in Data Privacy Safeguards (See below for an in-depth consideration)

--------

## 🌎 Environment Setup and Requirements
1. Clone the repo to your local computer and cd into the directory
``` 
git clone https://github.com/JessicaChildress/Computer_Use_Agent.git

cd Computer_Use_Agent
```
2. Create your conda virtual environment
```
conda create -n CompUseAgent
```
3. Install dependencies
``` 
pip install -r requirements.txt
```
4. Get your [Open AI API key](https://platform.openai.com/api-keys) and store it in a `config.yaml` file in the same directory

> [!IMPORTANT]  
> Be sure to add the file name to your `.gitignore` file so that it does not get pushed to your repo! 
-------

## ▶️ Usage 
```
python computer_use_agent.py
```

------

## ✅ The 2 Ways to Adhere to Data Privacy Best Practices:
### 1. Implement [WAIT] placeholders in a cloud-based LLM ⛅️
### 2. Fully automated Local LLM that can access user credentials 🔐

|        | Benefits | Drawbacks |
|:------ |:---------|:----------|  
| Cloud-Based Approach| * Simple setup on any machine | * Workflow is interrupted and requires manual user intervention at sensitive steps |
|        | * Can easily try different models and upgrade to the latest release | * Incurs usage costs based on the API calls and model pricing |
| Local LLM Approach | * Complete E2E automation without user intervention | * Requires significant local hardware resources | 
|   | * Full privacy protection for all user data | * Model quality may be lower than cloud alternatives due to compute restraints |
|   | * No ongoing costs can can run without internet after initial setup | * More complex setup and maintenance | 
|   | * Can integrate deeply with system security features | * Higher technical knowledge required for proper security configurations |   


For this simple architecture, I **used the cloud-based** approach, which consists of a three-part design: 
* Detect when a login might be required (performed during planning by the GPT-4o model)
* Pause the agent and wait for the user to manually enter their credentials
* Resume the process and continue with the remaining steps
