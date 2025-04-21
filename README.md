# AIML-MCP
The Model Context Protocol (MCP) is an open standard that enables AI systems– such as large language models (LLMs) — to securely connect with the tools and data sources organizations already use


1: Start the Server:
	Make sure you have FastAPI and Uvicorn installed:

	pip install fastapi uvicorn
	Then, start the MCP server:

	cd server
	uvicorn main:app --reload
	This starts a FastAPI server with:

	POST /rpc: JSON-RPC handler for tool listing and invocation
	GET /events: Simulated SSE endpoint emitting heartbeat messages every 5 seconds
	
2️: Run the Client:
	Install the required Python requests package:

	pip install requests
	Then run the client to interact with the server:

	cd client
	python main.py
	Output:

	Tools: [{'name': 'greet', 'description': 'Greets the user', ...}]
	Response: {'message': 'Hello, Sri!'}
	You can run http://localhost:8000/events and you should see the heartbeat event being returned like the one shown below.

	_data: {'event': 'heartbeat'}

	data: {'event': 'heartbeat'} _ ...
	
What It Demonstrates:
	A basic MCP server exposing tools via tools/list and tools/call
	A client sending JSON-RPC requests to list and call tools
	Simulated real-time connection using /events SSE endpoint
	Modular structure ready to extend for resources/ and prompts/ support
	
Next Steps:
	You can expand this prototype by:

	Adding more tools with different schemas
	Supporting resources/list and resources/read
	Managing prompt templates with prompts/get
	Implementing authentication and access control
	Handling streaming responses from server to client
	
https://modelcontextprotocol.io/introduction
https://www.jsonrpc.org/specification
https://fastapi.tiangolo.com/
https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events
