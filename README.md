https://github.com/kiranimmadi2/AI-Agent/blob/98eafdb30e170441c93f9653a259c0127e5b2f91/web-ui.png

<br/>

This project builds upon the foundation of the [browser-use](https://github.com/browser-use/browser-use), which is designed to make websites accessible for AI agents.

We would like to officially thank Kiran Immadi for contributions to this project.

**WebUI:** is built on Gradio and supports most of `browser-use` functionalities. This UI is designed to be user-friendly and enables easy interaction with the browser agent.

**Expanded LLM Support:** We've integrated support for various Large Language Models (LLMs), including: Gemini, OpenAI, Azure OpenAI, Anthropic, DeepSeek, Ollama etc. And we plan to add support for even more models in the future.

**Custom Browser Support:** You can use your own browser with our tool, eliminating the need to re-login to sites or deal with other authentication challenges. This feature also supports high-definition screen recording.

**Persistent Browser Sessions:** You can choose to keep the browser window open between AI tasks, allowing you to see the complete history and state of AI interactions.

## Installation Options

### Option 1: Local Installation

Read the [quickstart guide](https://docs.browser-use.com/quickstart#prepare-the-environment) or follow the steps below to get started.

> Python 3.11 or higher is required.

First, we recommend using [uv](https://docs.astral.sh/uv/) to setup the Python environment.

```bash
uv venv --python 3.11
```

and activate it with:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
uv pip install -r requirements.txt
```

Then install playwright:

```bash
playwright install
```

### Option 2: Docker Installation

1. **Prerequisites:**
   - Docker and Docker Compose installed on your system
   - Git to clone the repository

2. **Setup:**
   ```bash
   # Clone the repository
   git clone https://github.com/kiranimmadi2/web-ui.git
   cd web-ui

   # Copy and configure environment variables
   cp .env.example .env
   # Edit .env with your preferred text editor and add your API keys
   ```

3. **Run with Docker:**
   ```bash
   # Build and start the container with default settings (browser closes after AI tasks)
   docker compose up --build

   # Or run with persistent browser (browser stays open between AI tasks)
   CHROME_PERSISTENT_SESSION=true docker compose up --build
   ```

4. **Access the Application:**
   - WebUI: `http://localhost:7788`
   - VNC Viewer (to see browser interactions): `http://localhost:6080/vnc.html`

   Default VNC password is "youvncpassword". You can change it by setting the `VNC_PASSWORD` environment variable in your `.env` file.

## Usage

### Local Setup
1.  Copy `.env.example` to `.env` and set your environment variables, including API keys for the LLM. `cp .env.example .env`
2.  **Run the WebUI:**
    ```bash
    python webui.py --ip 127.0.0.1 --port 7788
    ```
4. WebUI options:
   - `--ip`: The IP address to bind the WebUI to. Default is `127.0.0.1`.
   - `--port`: The port to bind the WebUI to. Default is `7788`.
   - `--theme`: The theme for the user interface. Default is `Ocean`.
   - `--dark-mode`: Enables dark mode for the user interface.
3.  **Access the WebUI:** Open your web browser and navigate to `http://127.0.0.1:7788`.
4.  **Using Your Own Browser(Optional):**
    - Set `CHROME_PATH` to the executable path of your browser and `CHROME_USER_DATA` to the user data directory of your browser.
5. **Keep Browser Open(Optional):**
    - Set `CHROME_PERSISTENT_SESSION=true` in the `.env` file.

### Docker Setup
1. **Environment Variables:**
   - All configuration is done through the `.env` file

2. **Browser Persistence Modes:**
   - **Default Mode (CHROME_PERSISTENT_SESSION=false):**
     - Browser opens and closes with each AI task
   - **Persistent Mode (CHROME_PERSISTENT_SESSION=true):**
     - Browser stays open between AI tasks

3. **Viewing Browser Interactions:**
   - Access the noVNC viewer at `http://localhost:6080/vnc.html`

4. **Container Management:**
   ```bash
   docker compose up -d
   docker compose logs -f
   docker compose down
   ```
