# Math Routing Agent

This project is a full-stack application designed to solve math problems. It features a sophisticated backend built with FastAPI and LangGraph, a user-friendly frontend, and a comprehensive suite for benchmarking performance. The agent can retrieve information from a knowledge base, perform web searches, and refine its answers based on user feedback.

## Features

* **Advanced Backend**: The core of the application is a powerful backend that uses an agentic workflow to process and route user queries for solving math problems.
* **Knowledge Base Integration**: The agent can retrieve information from a knowledge base to provide accurate and context-aware answers.
* **Web Search Capability**: If the knowledge base does not contain the necessary information, the agent can perform web searches to find a solution.
* **Feedback and Refinement**: The system includes a feedback mechanism that allows users to provide input on the initial answers. This feedback is used to refine the answers and continuously improve the knowledge base.
* **Comprehensive Benchmarking**: The project includes a full suite for evaluating the performance of the math agent, with support for various question types and metrics.
* **User-Friendly Frontend**: A clean and intuitive frontend application allows users to easily interact with the math agent.

* **`Benchmark Evaluation/`**: Contains all the scripts and data required for benchmarking the performance of the math agent.
* **`Core_Backend/`**: The main backend of the application, built with FastAPI and LangGraph.
* **`Frontend/`**: The frontend application for user interaction.

## Getting Started

### Prerequisites

Make sure you have Python 3.7+ and Node.js installed on your system.

### Installation

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/your-username/math-routing-agent.git](https://github.com/your-username/math-routing-agent.git)
    cd math-routing-agent
    ```

2.  **Install backend dependencies:**

    ```bash
    pip install -r Core_Backend/requirements.txt
    ```

3.  **Install frontend dependencies:**

    ```bash
    cd Frontend
    npm install
    ```

### Running the Application

1.  **Start the backend server:**

    ```bash
    cd Core_Backend
    uvicorn main_backend:app --reload
    ```

    The backend server will be running on `http://127.0.0.1:8000`.
    
    Note: Make sure to create a .env file to store your API Keys. (LLM key, Tavily Key)

2.  **Start the frontend application:**

    ```bash
    cd Frontend
    npm run dev
    ```

## API Endpoints

The backend provides the following API endpoints:

### `POST /ask`

* **Description**: Submits a math question to the agent for a solution.
* **Request Body**:
    ```json
    {
      "question": "Your math question here"
    }
    ```
* **Response**:
    ```json
    {
      "answer": "The agent's step-by-step solution"
    }
    ```

### `POST /refine`

* **Description**: Provides feedback on an initial answer to get a refined solution.
* **Request Body**:
    ```json
    {
      "question": "The original question",
      "initial_answer": "The agent's first answer",
      "feedback": "Your feedback on the answer"
    }
    ```
* **Response**:
    ```json
    {
      "refined_answer": "The new, refined answer"
    }
    ```

## Benchmarking

The `Benchmark Evaluation/` directory contains all the necessary tools to evaluate the performance of the math agent.

* **`inference.py`**: Runs the inference process to get the agent's responses for a given dataset.
```
python inference.py --model agentic --mode CoT --data data/dataset.json --num_procs 1 --max_questions 10
```
* **`compute_metrics.py`**: Computes and saves the performance metrics of the agent.
```
python compute_metrics.py --model agentic --mode CoT --data data/dataset.json --response_path responses/Agentic_CoT_responses/responses.json

```

For detailed instructions on running the benchmarks, please refer to the documentation within the `Benchmark Evaluation/` directory.

## Frontend

The frontend is a React application built with Vite. It provides a user-friendly interface for interacting with the backend. The source code is located in the `Frontend/` directory.
