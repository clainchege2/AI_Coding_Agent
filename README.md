# AI_Coding_Agent


This repository contains the code and documentation for the AI Agent Workshop, where we explore the capabilities of different Large Language Models (LLMs) through APIs like OpenAI, Groq, and OpenRouter.

## Table of Contents
- [Introduction](#introduction)
- [Setup](#setup)
- [Usage](#usage)
- [Functions](#functions)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

## Introduction
The goal of this workshop is to build an AI agent capable of breaking down complex queries into manageable subtasks, reasoning through them, and executing code when necessary. The agent leverages various LLMs to perform these tasks.

## Setup
To get started, you need to have the following prerequisites installed:
- Python 3.10 or higher
- `openai` and `groq` libraries

You can install the required libraries using pip:
```bash
pip install openai groq
You will also need API keys for OpenAI, Groq, and OpenRouter. These keys should be set as environment variables:
bash
Copy
export NGROK_AI_TOKEN=your_groq_api_key
export OPENROUTER_API_KEY=your_openrouter_api_key
export OPENAI_API_KEY=your_openai_api_key
Usage
To use the AI agent, you can run the following Python script:
Python
Copy
from openai import OpenAI
from groq import Groq

# Initialize clients
groq_client = Groq(api_key=os.getenv('NGROK_AI_TOKEN'))
openrouter_client = OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key=os.getenv("OPENROUTER_API_KEY")
)
openai_client = OpenAI(
    base_url="https://api.openai.com/v1",
    api_key=os.getenv("OPENAI_API_KEY")
)

# Define your query
query = "The surgeon, who is the boy's father, says, 'I can't operate on this boy, he's my son!' Who is the surgeon to the boy?"

# Get response from Groq
result = get_llm_response("groq", query)
print(result)

# Use the autonomous agent to solve the query
final_answer = autonomous_agent(query)
print("FINAL ANSWER: ", final_answer)
Functions
The following functions are defined in the script:
get_llm_response(client, prompt, openai_model="o1-preview", json_mode=False): Fetches responses from specified LLMs.
evaluate_responses(prompt, reasoning_prompt=False, openai_model="o1-preview"): Compares responses from different LLMs.
planner(user_query): Breaks down the user's query into subtasks.
reasoner(user_query, subtasks, current_subtask, memory): Provides reasoning for the current subtask.
actioner(user_query, subtasks, current_subtask, reasoning, memory): Determines the next action (generate code or reasoning).
evaluator(user_query, subtasks, current_subtask, action_info, execution_result, memory): Evaluates the result of the current subtask.
generate_and_execute_code(prompt, user_query, memory): Generates and executes Python code.
executor(action, parameters, user_query, memory): Executes the task based on the action type.
final_answer_extractor(user_query, subtasks, memory): Extracts the final answer from the memory.
autonomous_agent(user_query): Coordinates the entire process to answer the user's query.
Examples
Surgeon Puzzle
Python
Copy
query = "The surgeon, who is the boy's father, says, 'I can't operate on this boy, he's my son!' Who is the surgeon to the boy?"
result = get_llm_response("groq", query)
print(result)
Bear Puzzle
Python
Copy
query = "The Bear Puzzle: A hunter leaves his tent. He travels 5 steps due south, 5 steps due east, and 5 steps due north. He arrives back at his tent, and sees a brown bear inside it. What color was the bear?"
result = get_llm_response("groq", query)
print(result)
Contributing
Contributions are welcome! Please open an issue or submit a pull request with your changes.
License
This project is licensed under the MIT License - see the LICENSE file for details.
Copy

### Additional Notes:
- Make sure to include a `LICENSE` file in your repository if you mention it in the README.
- You can add more sections or details as needed, such as a section for dependencies, tests, or deployment instructions.

This README provides a comprehensive overview of your project, making it easier for others to understand and contribute to your work.
