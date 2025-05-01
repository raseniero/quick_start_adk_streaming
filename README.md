# ADK Streaming Quickstart

This project demonstrates a simple web application using the Google Agent Development Kit (ADK) to stream responses from a Gemini agent backed by Google Search.

## Folder Structure

```
.
├── .env                  # API keys and configuration (ignored by git)
├── .gitignore            # Specifies intentionally untracked files that Git should ignore
├── README.md             # This file
├── app/                  # Main application folder
│   ├── __init__.py       # Makes 'app' a Python package
│   ├── main.py           # FastAPI application entrypoint
│   ├── google_search_agent/ # Contains the agent logic
│   │   ├── __init__.py   # Makes 'google_search_agent' a Python package
│   │   └── agent.py      # Defines the search agent
│   └── static/           # Static files (HTML, CSS, JS)
│       └── index.html    # Frontend HTML
└── .venv/                # Python virtual environment (ignored by git)
```
*(Note: A potentially redundant `.env` file might exist in `app/google_search_agent/`)*

## Setup

1.  **Clone the repository (if applicable)**
    ```bash
    # git clone <repository-url>
    # cd adk_streaming_quickstart
    ```

2.  **Create and Activate Virtual Environment:**
    It's recommended to use a virtual environment to manage dependencies.
    ```bash
    # Create the virtual environment
    python3 -m venv .venv

    # Activate the virtual environment
    # On macOS/Linux:
    source .venv/bin/activate
    # On Windows:
    # .venv\Scripts\activate
    ```

3.  **Install Dependencies:**
    *(Create a requirements.txt file with dependencies like `fastapi`, `uvicorn[standard]`, `google-generativeai`, `python-dotenv`, `websockets`, `google-cloud-aiplatform` (if using Vertex) and run:)*
    ```bash
    pip install -r requirements.txt
    ```

4.  **Configure Environment Variables:**
    Create a file named `.env` in the root directory of the project (`/Users/jairo/Projects/adk_streaming_quickstart/.env`). Add the following content, replacing the placeholder with your actual Google API Key:
    ```dotenv
    # .env
    GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY_HERE"
    GOOGLE_GENAI_USE_VERTEXAI="False" # Use "True" for Vertex AI, "False" for AI Studio/MakerSuite
    ```
    *   Get your API key from [Google AI Studio](https://aistudio.google.com/app/apikey).
    *   The `.env` file is included in `.gitignore` and should not be committed to version control.

## Running the Application

1.  **Navigate to the app directory:**
    ```bash
    cd app
    export SSL_CERT_FILE=$(python3 -m certifi)
    adk web
    ```

2.  **Start the FastAPI server:**
    ```bash
    uvicorn main:app --reload
    ```
    The `--reload` flag automatically restarts the server when code changes are detected.

3.  **Access the application:**
    Open your web browser and go to [http://127.0.0.1:8000](http://127.0.0.1:8000).

