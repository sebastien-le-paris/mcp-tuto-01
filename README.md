# MCP Server with FastMCP & Next.js Chat UI

## Project Overview

This project implements a Model Context Protocol (MCP) server using the FastMCP Python SDK and creates a modern chat interface using Next.js. MCP enables AI systems to interact with external tools, data sources, and services in a standardized way.

### ✅ What’s the Goal?
This project shows a simple working version (called a “Proof of Concept”) of something called an MCP Server using Python. It helps us explore and test how AI tools can talk to other apps and services automatically.

### 🤔 What is MCP?
MCP stands for Model Context Protocol. It’s like a universal translator that helps AI systems (like chatbots or virtual assistants) connect with other tools, apps, or data—without needing a bunch of custom code for each one.

Think of it like a power strip: instead of needing a different plug for every device, everything can connect through one system—quickly and securely.

### 💡 Why Does It Matter?
Normally, connecting an AI model to apps like Google Sheets or Slack means writing separate code for each one, managing access, and keeping it updated.
With MCP:
+ You set up the connection once
+ All AI tools can use it
+ It saves time and reduces technical headaches
+ It allows AI to both get info and take action—automatically

Imagine an AI not just answering questions, but also:
+ Updating a spreadsheet
+ Sending a message
+ Pulling files from a shared drive
+ All with one shared system.

### 🧩 What Are the Main Parts of MCP?
Here’s how MCP works behind the scenes (don’t worry—no coding required to understand this!):
+ Host – A tool like an AI assistant that wants to do something (e.g., update a report).
+ Client – A helper that sends requests between the host and the MCP server.
+ MCP Server – The middleman that knows how to talk to apps like Google Sheets or Slack.
+ Local Data – Files or databases on your computer or company server.
+ Remote Services – Online apps like Google Drive, Slack, or Outlook.

### 🧵 A Simple Example
Let’s say you’re using an AI tool (like Cursor) to manage your project’s budget:
+ You ask the AI to update your budget in Google Sheets and send a summary to Slack.
+ The AI passes this to the MCP client.
+ The client sends it to two MCP servers—one for Google Sheets and one for Slack.
+ Each server talks to its respective app to do the task.
+ The results are passed back to the AI, which shows you what happened.
All of this happens behind the scenes—fast, secure, and without writing new code for every app.

### 🔧 Building an MCP Server (Tech-lite Overview)
There are two ways to build an MCP Server:
+ One using Python (what this project uses)
+ One using JavaScript
For this demo, we focus on Python, which is a common programming language that's easy to experiment with.

### Key Components:

1. **FastMCP Server**: A Python server that follows the MCP specification, providing tools and resources that can be accessed by AI models
2. **Next.js Chat UI**: A modern web interface similar to [Mastra](https://github.com/mastra-ai/mastra) that allows users to interact with AI through a chat interface

## What is MCP?

The Model Context Protocol (MCP) is a standardized way for AI models to interact with external tools and data sources. It enables:

- AI models to call functions (tools) defined on an MCP server
- Access to structured data through resource URLs
- Secure file system access with defined roots
- Standardized communication between clients and servers

With MCP, you can build powerful AI applications that can:
- Update spreadsheets
- Send messages to communication platforms
- Access and process files
- Call external APIs
- And much more!

## Project Structure

```
mcp-project/
├── server/               # FastMCP server implementation
│   ├── server.py         # Main server file
│   ├── tools/            # Custom tools implementation
│   └── resources/        # Resource definitions
├── client/               # Next.js chat interface
│   ├── app/              # Next.js app directory
│   ├── components/       # UI components
│   ├── lib/              # Utility functions
│   └── public/           # Static assets
└── docs/                 # Documentation
```

## Getting Started

### Prerequisites

- Python 3.10+
- Node.js 18+
- npm or yarn

### Server Setup

1. Create a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Install FastMCP:
   ```
   pip install fastmcp
   ```

3. Run the server in development mode:
   ```
   fastmcp dev server/server.py
   ```

### Client Setup

1. Navigate to the client directory:
   ```
   cd client
   ```

2. Install dependencies:
   ```
   npm install
   # or
   yarn install
   ```

3. Start the development server:
   ```
   npm run dev
   # or
   yarn dev
   ```

4. Open [http://localhost:3000](http://localhost:3000) in your browser

## Key Features

### FastMCP Server

- **Tool Definitions**: Create functions that can be called by AI models
- **Resource Endpoints**: Expose structured data via resource URLs
- **File Access**: Secure access to the file system with defined roots
- **Input Validation**: Validate inputs using Pydantic models
- **Error Handling**: Proper error handling and logging

### Next.js Chat UI

- **Modern Interface**: Clean, responsive design inspired by Mastra
- **Real-time Updates**: Instant message updates
- **Tool Visualization**: Display tool results in a user-friendly way
- **Markdown Support**: Render markdown and code highlighting
- **Mobile-friendly**: Works on all device sizes

## Example Server

Here's a simple example of a FastMCP server:

```python
from fastmcp import FastMCP
mcp = FastMCP("Demo Server")

@mcp.tool()
def add(a: int, b: int) -> int:
    """Add two numbers"""
    return a + b

@mcp.resource("data://greeting")
def greeting():
    return "Hello, world!"

if __name__ == "__main__":
    mcp.run()
```

## Additional Resources

- [FastMCP Documentation](https://github.com/jlowin/fastmcp)
- [MCP Specification](https://github.com/anthropics/anthropic-cookbook/tree/main/mcp)
- [Next.js Documentation](https://nextjs.org/docs)

## References

https://composio.dev/blog/mcp-server-step-by-step-guide-to-building-from-scrtch/
