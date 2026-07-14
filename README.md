# LangGraph 101: Building Stateful AI Workflows

A hands-on notebook for learning [LangGraph](https://pypi.org/project/langgraph/), a Python framework for building stateful, graph-based AI workflows. You'll learn the core building blocks (states, nodes, edges, conditional edges) and use them to build two working applications: an authentication workflow and a question-answering agent, followed by a hands-on exercise building a simple looping counter graph.

## Overview

LangGraph lets you break complex tasks into smaller steps, organize them logically, and connect them into a graph that represents the flow of execution. Unlike frameworks limited to strictly linear (DAG) flows, LangGraph supports **cyclic graphs**, so a workflow can loop back on itself — retrying a step, refining an answer, or asking for input again — making it well suited for agents that need iteration, feedback loops, or retries.

## What You'll Learn

- What LangGraph is and why cyclic graphs matter for agentic workflows
- The four core components of LangGraph:
  - **States** – typed structures that carry data between steps
  - **Nodes** – functions that perform a unit of work
  - **Edges** – direct connections that define execution order
  - **Conditional edges** – decision points that route execution based on state
- How to build, compile, and run a graph with `StateGraph`
- How to integrate an LLM into a node to answer questions using retrieved context
- How to build a workflow with a loop and a stopping condition

## Contents

1. **What is LangGraph? / Why LangGraph?** — conceptual overview and comparison to linear-only frameworks
2. **Setup** — installing and importing the required libraries
3. **Components of LangGraph** — states, nodes, edges, and conditional edges explained with runnable examples
4. **Building an Authentication Workflow** — a full example graph that:
   - Collects a username/password via an input node
   - Validates credentials
   - Routes to a success or failure node using a conditional edge
   - Loops back to the input node on failure
5. **Building a QA Workflow** — a graph that:
   - Validates an incoming question
   - Determines whether relevant context is available
   - Uses an LLM node to answer the question when context is available, and gracefully declines otherwise
6. **Exercises** — build a simple counter graph from scratch:
   - Define a state with a counter and a random letter
   - Write an `add()` node that increments the counter
   - Write a `print_out()` node to log progress
   - Define a stop condition and wire up the full loop
   - Compile and run the graph
   (Solutions are included in collapsible sections for self-checking.)

## Requirements

- Python 3.9+
- Jupyter Notebook / JupyterLab
- `langgraph` (tested with `langgraph==0.2.57`)
- An LLM provider integration for the QA workflow section (any LangChain-compatible chat model works, e.g. `langchain-openai`'s `ChatOpenAI`)

Install the core dependency with:

```bash
pip install langgraph==0.2.57
```

## Running Locally

If you run this notebook outside of a hosted lab environment, you'll need to supply your own API key for whichever LLM provider you use in the QA workflow section (for example, `ChatOpenAI` from `langchain-openai`). Update the LLM initialization cell with your provider, model name, and credentials before running the QA workflow cells. Using your own API key will incur charges based on your provider's pricing.

## Usage

1. Open `LangGraph101-v1.ipynb` in Jupyter.
2. Run the setup cells to install and import dependencies.
3. Work through the authentication and QA workflow sections in order — each builds on concepts from the previous one.
4. Complete the exercises at the end to practice building a graph from scratch. Solutions are provided if you get stuck.

## License

See the notebook for authorship details. Please check with the original notebook authors regarding reuse and distribution terms.
