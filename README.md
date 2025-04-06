# Volatility MCP

## Overview

Volatility MCP is a project that integrates Volatility 3, a memory forensics framework, with a Python FastAPI backend. This setup allows memory image analysis via the Model Context Protocol (MCP). The FastAPI backend exposes Volatility 3 plugins as RESTful APIs, enabling seamless integration with a web front end for interactive memory forensics analysis. MCP clients like Claude Desktop or custom web applications can consume these APIs to leverage Volatility plugins such as `pslist` and `netscan`.

## Features

* **Volatility 3 Integration:** Leverages the Volatility 3 framework for memory image analysis.
* **FastAPI Backend:** Provides RESTful APIs to interact with Volatility plugins.
* **Web Front End Support:** Designed to connect with a web-based front end for interactive analysis.
* **Model Context Protocol (MCP):** Enables standardized communication with MCP clients like Claude Desktop.
* **Plugin Support:** Supports various Volatility plugins, including `pslist` for process listing and `netscan` for network connection analysis.


## Architecture

The project architecture consists of the following components:

* **MCP Client:** MCP client like Claude Desktop that interacts with the FastAPI backend.
* **FastAPI Server:** A Python-based server that exposes Volatility plugins as API endpoints.
* **Volatility 3:** The memory forensics framework that performs the actual analysis.

This architecture allows users to analyze memory images through MCP clients such as Claude desktop. Users can use natural language prompts to perform memory forensics analysis such as
show me the list of the processes in memory image x, or show me all the external connections made

## Getting Started

### Prerequisites

* Python 3.7+ installed on your system
* Volatility 3 installed (see [Volatility 3 Installation Guide](https://github.com/volatilityfoundation/volatility3?tab=readme-ov-file#installing))

### Installation

1. Clone the repository:

    ```
    git clone <repository_url>
    cd <repository_directory>
    ```

2. Install the required Python dependencies:

    ```
    pip install -r requirements.txt
    ```

3. Start the FastAPI server to expose Volatility 3 APIs:

    ```
    uvicorn volatility_fastapi_server:app --port 8000 
    ```
4. Install Claude Desktop (see [Claude Desktop](https://claude.ai/download)
5. To configure Claude Desktop as a volatility MCP client, navigate to Claude → Settings → Developer → Edit Config, locate the claude_desktop_config.json file, and insert the specified configuration details.


### Configuration

The FastAPI server can be configured  or by modifying the configuration file (`config.py`). Key configuration options include:

* `HOST`: The host address for the FastAPI server (default: `127.0.0.1`).
* `PORT`: The port for the FastAPI server (default: `8000`).

### Usage

1. Start the FastAPI server as described above.
2. Connect a MCP client (e.g., Claude Desktop) to the FastAPI server.
3. start asking question about the memory image

#### Example API Request

To run the `pslist` plugin via an API request:


## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. Fork this repository.
2. Create a new branch (`git checkout -b feature/my-feature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to your branch (`git push origin feature/my-feature`).
5. Open a pull request.

