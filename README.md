# 🔧 Giving LLMs Superpowers with Tool Calling in LangChain

![LangChain](https://img.shields.io/badge/LangChain-0086CB?style=for-the-badge&logo=langchain) ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai) ![Python](https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python)

Hey there! Welcome to my exploration of what I think is one of the coolest features in LangChain: **Tool Calling**. I've always been fascinated by how AI assistants like ChatGPT can access real-time information or perform actions. It turns out, this is the core mechanism that makes it all possible.

This repository, documented in a single Jupyter Notebook, is my personal journey into understanding how to give a Large Language Model (LLM) access to my own custom Python functions. It's like giving the AI new superpowers on demand!

---

### 🤔 The "Why" Behind Tool Calling

By themselves, LLMs are amazing at processing and generating text. But they live in a bubble—they can't browse the web, check the weather, or perform a simple calculation without making a guess.

**Tool Calling** breaks them out of that bubble. It's the process of letting an LLM:
1.  **Recognize** when a user's query requires an external tool or function.
2.  **Figure out** which specific tool to use.
3.  **Determine** the correct inputs to pass to that tool.
4.  **Receive** the tool's output and use that information to formulate a final, accurate answer.

This is the foundational concept behind building powerful AI agents that can interact with APIs, databases, and other systems.

---

### ✨ Core Concepts I've Implemented

This project is a step-by-step demonstration of the entire tool-calling workflow:

1.  **Defining a Custom Tool**:
    -   I started by writing a simple Python function, for example, a function to multiply two numbers.
    -   Then, using LangChain's `@tool` decorator, I instantly converted this regular function into a "tool" that an LLM can understand. This decorator automatically infers the tool's name, description, and input schema from the function's signature and docstring.

2.  **Binding Tools to the LLM**:
    -   Next, I took my list of custom tools and "bound" them to an OpenAI chat model using the `.bind_tools()` method.
    -   This step essentially makes the LLM *aware* of the new capabilities it has. It can now choose to call these tools if needed.

3.  **Intelligent Invocation**:
    -   The magic happens when I invoke the model with a prompt like, "What is 5 times 30?".
    -   Instead of trying to guess the answer, the LLM recognizes that this is a multiplication task, and its response is not a simple text answer, but a structured `tool_calls` object. This object contains the name of the tool to call (`multiply`) and the arguments to pass to it (`{'a': 5, 'b': 30}`).

4.  **Building a Complete Chain**:
    -   Finally, I put everything together into a complete chain. The chain manages the whole process: sending the user's query to the LLM, parsing the `tool_calls` output, executing the correct Python function with the right arguments, and then feeding the result back into the LLM to generate the final, human-readable answer.

---

### 🛠️ Tech Stack

-   **Core AI Framework**: LangChain
-   **LLM Provider**: OpenAI
-   **Notebook Environment**: Jupyter
-   **Core Libraries**: `langchain-core`, `langchain-openai`, `python-dotenv`

---

### ⚙️ Setup and Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/jsonusuman351/tool-calling-in-lang-chain.git](https://github.com/jsonusuman351/tool-calling-in-lang-chain.git)
    cd tool-calling-in-lang-chain
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    # It is recommended to use Python 3.10 or higher
    python -m venv venv
    .\venv\Scripts\activate
    ```

3.  **Install the required packages:**
    Since I worked directly in a Jupyter Notebook, there isn't a `requirements.txt` file. You can install all the necessary libraries by running this command:
    ```bash
    pip install langchain langchain-core langchain-openai openai python-dotenv jupyter
    ```

4.  **Set Up Your OpenAI API Key:**
    -   To run the notebook, you'll need to provide your OpenAI API key. I recommend setting it as an environment variable on your system, but for a quick start, you can also place it directly in the notebook (just remember not to commit it to GitHub!).

---

### 🚀 How to Use This Project

The entire workflow is contained within a single, well-documented Jupyter Notebook.

1.  **Launch Jupyter:**
    Make sure your virtual environment is active, then run:
    ```bash
    jupyter notebook
    ```
2.  **Open the Notebook:**
    In the Jupyter interface that opens in your browser, click on `tool-calling-in-lang-chain.ipynb`.
3.  **Add Your API Key:**
    Ensure your OpenAI API key is accessible within the notebook.
4.  **Run the Cells:**
    You can run each cell in the notebook sequentially to see the entire process, from defining a simple tool to building a complete tool-calling chain.

---

### 🔬 A Tour of My Tool-Calling Experiment

I've organized this entire project into a single Jupyter Notebook to make it easy to follow my journey of giving superpowers to an LLM.

<details>
<summary>Click to view the code layout</summary>

```
tool-calling-in-lang-chain/
│
└── tool-calling-in-lang-chain.ipynb    # The complete end-to-end workflow is in this single notebook
```
</details>

---

---
