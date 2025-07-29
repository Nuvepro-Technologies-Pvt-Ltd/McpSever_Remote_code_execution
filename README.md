execution in a secure and scalable lab setup.

⚙️ Lab Virtual MCP Server (Execute Code Remotely via Claude AI)
Create a virtual lab for users to run custom code remotely using the Model Context Protocol (MCP) and integrate with Claude AI or other clients.

  
<img src="video/test.gif" alt="description" height="300" width="900" />


🔗 GitHub Repo
<pre>
📦 https://github.com/Nuvepro-Technologies-Pvt-Ltd/McpSever_Remote_code_execution.git
</pre>
📂 This repo has moved to base/base-mcp

🚀 What This Lab Server Does
🧠 Enables remote Python code execution through cline AI


🧪 Supports real-time lab scenarios (code evaluation, sandbox testing, etc.)

📋 Prerequisites
Ensure you have the following on your system:

✅ Python 3.10.11

✅ pip (Python package manager)

✅ fastmcp (to serve the MCP endpoint)

✅ uv (virtual environment manager, via scoop or curl)

✅ Access to Claude Desktop or Cursor or cline (for testing)



🧱 Installation Steps

1. Clone the MCP Server Repo
<pre>
git clone https://github.com/Nuvepro-Technologies-Pvt-Ltd/McpSever_Remote_code_execution.git
</pre>

2. Set up Python Environment

<pre>
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
</pre>

<pre>
scoop install python
</pre>

<pre>
scoop install uv
</pre>




cd McpSever_Remote_code_execution

3. Set Up Virtual Environment

<pre>
python -m venv .venv
</pre>
<pre>
.\.venv\Scripts\activate   # Windows
</pre>
<pre>
source .venv/bin/activate  # macOS/Linux
</pre>

4. Install Dependencies

<pre>
pip install fastmcp
</pre>

<pre>
pip install cryptography
</pre>

<pre>
pip install shelve
</pre>

5. Run the Server
<pre>
fastmcp run app.py
</pre>
You now have a remote code execution server listening for requests via MCP.

🧪 MCP Client Configuration
For Claude Desktop / Cursor, update your mcp_config.json:


<pre>
{
  "mcpServers": {
    "CloudlabMcp": {
      "disabled": false,
      "timeout": 500,
      "type": "stdio",
      "command": "uv",
      "args": [
        "run",
        "--with",
        "fastmcp",
        "python",
        "%PROJECT_PATH%\\app.py"
      ],
      "env": {
        "API_KEY": "your_private_key",
        "Baseurl": "your seed phrase here",
        "compnaykey": "your_private_key"
      },
      "autoApprove": [*]
    }
  }
}


</pre>

Beofre start Mcp set path
<pre>
set PROJECT_PATH=D:\YourProject
</pre>
<pre>
cline run CloudlabMcp
</pre>

✅ Available Tools (Prebuilt in MCP)

Tool Description
execute_code	Executes user-provided Python code


💡 Recommendations for Lab Admins
✅ Add sandboxing logic to app.py if users can run arbitrary code.

✅ Use Docker or subprocess isolation for safer execution (optional).

✅ Monitor logs and set execution timeouts.

