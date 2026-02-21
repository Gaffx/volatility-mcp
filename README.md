![](https://img.shields.io/badge/License-Apache%202.0-blue?style=plastic&logo=adobefonts)
<p align="center">
<img src="assets/logo.png" height="300">
</p>
<h1 align="center">
Your AI Assistant in Memory Forensics
</h1>

<a href="https://glama.ai/mcp/servers/@Gaffx/volatility-mcp">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@Gaffx/volatility-mcp/badge" alt="Volatility MCP server" />
</a>

## Overview
Volatility MCP seamlessly integrates Volatility 3's powerful memory analysis with FastAPI and the Model Context Protocol (MCP). Experience memory forensics without barriers as plugins like `pslist` and `netscan` become accessible through clean REST APIs, connecting memory artifacts directly to AI assistants and web applications

## Features
* **Volatility 3 Integration:** Leverages the Volatility 3 framework for memory image analysis.
* **FastAPI Backend:** Provides RESTful APIs to interact with Volatility plugins.
* **Web Front End Support (future feature):** Designed to connect with a web-based front end for interactive analysis.
* **Model Context Protocol (MCP):** Enables standardized communication with MCP clients like Claude Desktop.
* **Plugin Support:** Supports various Volatility plugins, including `pslist` for process listing and `netscan` for network connection analysis.


## Architecture

The project architecture consists of the following components:

* **MCP Client:** MCP client like Claude Desktop that interacts with the FastAPI backend.
* **FastAPI Server:** A Python-based server that exposes Volatility plugins as API endpoints.
* **Volatility 3:** The memory forensics framework performing the analysis.

This architecture allows users to analyze memory images through MCP clients like Claude Desktop. Users can use natural language prompts to perform memory forensics analysis such as
show me the list of the processes in memory image x, or show me all the external connections made

## Getting Started

### Prerequisites

* Python 3.7+ installed on your system
* Volatility 3 binary installed (see [Volatility 3 Installation Guide](https://github.com/volatilityfoundation/volatility3?tab=readme-ov-file#installing)) and added to your env path called **VOLATILITY_BIN**

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
    uvicorn volatility_fastapi_server:app 
    ```
4. Install Claude Desktop (see [Claude Desktop](https://claude.ai/download)
5. To configure Claude Desktop as a volatility MCP client, navigate to Claude → Settings → Developer → Edit Config, locate the claude_desktop_config.json file, and insert the following configuration details
6. Please note that the `-i` option in the config.json file specifies the directory path of your memory image file.

   ```
       {
        "mcpServers": {
          "vol": {
            "command": "python",
            "args": [
              "/ABSOLUTE_PATH_TO_MCP-SERVER/vol_mcp_server.py", "-i",     
              "/ABSOLUTE_PATH_TO_MEMORY_IMAGE/<memory_image>"
            ]
          }
        }
    }
   ```
Alternatively, update this file directly:

`/Users/YOUR_USER/Library/Application Support/Claude/claude_desktop_config.json`

### Usage

1. Start the FastAPI server as described above.
2. Connect an MCP client (e.g., Claude Desktop) to the FastAPI server.
3. Start the prompt by asking questions regarding the memory image in scope, such as showing me the running processes, creating a tree relationship graph for process x, or showing me all external RFC1918 connections.

![image](https://github.com/user-attachments/assets/23f6fd4f-76b4-4255-a0a6-534ed3459bb3)
![image](https://github.com/user-attachments/assets/e5cd74ae-72ff-4c5b-8bd8-fbeb13488a70)
![image](https://github.com/user-attachments/assets/779707ef-4910-4503-b6b0-43f6c37075ef)
![image](https://github.com/user-attachments/assets/668e9b91-463a-424f-a3ef-ee2baf44308d)

## Future Features and Enhancements

*  **Native Volatility Python Integration:** Incorporate Volatility Python SDK directly in the code base as opposed to subprocess volatility binary
*   **Yara Integration:** Implement functionality to dump a process from memory and scan it with Yara rules for malware analysis.
*   **Multi-Image Analysis:** Enable the analysis of multiple memory images simultaneously to correlate events and identify patterns across different systems.
*   **Adding more Volatility Plugins:** add more volatility plugins to expand the scope of memory analysis
*   **GUI Enhancements:** Develop a user-friendly web interface for interactive memory analysis and visualization.
*   **Automated Report Generation:** Automate the generation of detailed reports summarizing the findings of memory analysis.
*   **Advanced Threat Detection:** Incorporate advanced techniques for detecting sophisticated threats and anomalies in memory.

## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. Fork this repository.
2. Create a new branch (`git checkout -b feature/my-feature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to your branch (`git push origin feature/my-feature`).
5. Open a pull request.

[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/gaffx-volatility-mcp-badge.png)](https://mseep.ai/app/gaffx-volatility-mcp)