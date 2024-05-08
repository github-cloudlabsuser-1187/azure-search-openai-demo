Backend Documentation
The backend of the application is built using Quart, a Python framework for asynchronous web applications. The backend code is stored in the app/backend folder.

Structure
The primary backend code you'll want to customize is in the app/backend/approaches folder. This folder contains the classes powering the Chat and Ask tabs. Each class uses a different RAG (Retrieval Augmented Generation) approach.

Chat Approach
The chat tab uses the approach programmed in chatreadretrieveread.py. This approach involves the following steps:

It calls the OpenAI ChatCompletion API (with a temperature of 0) to turn the user question into a good search query.
It queries Azure AI Search for search results for that query (optionally using the vector embeddings for that query).
It then combines the search results and original user question, and calls the OpenAI ChatCompletion API (with a temperature of 0.7) to answer the question based on the sources. It includes the last 4K of message history as well (or however many tokens are allowed by the deployed model).
The system_message_chat_conversation variable is currently tailored to the sample data since it starts with "Assistant helps the company employees with their healthcare plan questions, and questions about the employee handbook." You should change that to match your data.

Running the Backend
To start the backend, you can use the "Start App" task defined in the .vscode/tasks.json file. This task runs the start.sh or start.ps1[ script in the ](command:_github.copilot.openSymbolFromReferences?%5B%7B%22%24mid%22%3A1%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2Fazure-search-openai-demo%2Fdocs%2Fcustomization.md%22%2C%22scheme%22%3A%22file%22%7D%2C%7B%22line%22%3A0%2C%22character%22%3A0%7D%5D "docs/customization.md")app`` folder, depending on your operating system.

Customizing the Backend
You can customize the backend by modifying the code in the app/backend/approaches folder. For example, you can change the system_message_chat_conversation[ variable in the ](command:_github.copilot.openSymbolFromReferences?%5B%7B%22%24mid%22%3A1%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2Fazure-search-openai-demo%2Fdocs%2Fcustomization.md%22%2C%22scheme%22%3A%22file%22%7D%2C%7B%22line%22%3A0%2C%22character%22%3A0%7D%5D "docs/customization.md")chatreadretrieveread.py file to match your data.

For more details on customizing the backend, refer to the customization guide.