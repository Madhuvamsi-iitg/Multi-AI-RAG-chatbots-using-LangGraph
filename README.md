# Multi-AI-RAG-chatbots-using-LangGraph

### End-to-End Multi-AI RAG Chatbots Using LangGraph and AstraDB

This project leverages **LangGraph** and **AstraDB** to create a multi-AI Retrieval-Augmented Generation (RAG) chatbot system. The system is designed to intelligently route user queries to the most relevant data source, retrieve information, and generate accurate responses using advanced language models. Below is a detailed breakdown of the enhanced project:

---

### **Key Components and Enhancements**

1. **Database Setup with AstraDB**:
   - A database instance is created in **DataStax AstraDB**.
   - Website URLs are loaded into the database, and their content is preprocessed using a **Recursive Character Text Splitter** to create smaller, manageable text chunks.
   - These text chunks are converted into **vector embeddings** using **Hugging Face embeddings** and stored in AstraDB for efficient retrieval.

2. **External Data Sources**:
   - The system integrates external tools like **Wikipedia Search** and **Arxiv Search** to augment the knowledge base.
   - These tools are used to fetch real-time or domain-specific information when needed.

3. **LangGraph for State Management and Workflow**:
   - **LangGraph** is used to manage the state and workflow of the chatbot system.
   - The graph starts at the **START node**, where the user query is received.
   - A **Router** node determines the most relevant data source (e.g., AstraDB vector store, Wikipedia, or Arxiv) based on the query context.

4. **Enhanced Routing Mechanism**:
   - The **Router** is improved with a **multi-agent decision-making system** that uses **LLM-based classification** to route queries more accurately.
   - For example, factual queries are routed to Wikipedia, research-related queries to Arxiv, and domain-specific queries to the AstraDB vector store.

5. **LLM Integration with Groq API**:
   - The **Groq API** is used to power the LLM, with the **Gemma-2b-9It** model serving as the core language model.
   - A **custom prompt template** is designed to ensure the LLM generates contextually accurate and concise responses.

6. **Multi-Agent Collaboration**:
   - Multiple agents are employed within LangGraph to handle different tasks:
     - **Query Understanding Agent**: Parses and understands the user query.
     - **Retrieval Agent**: Fetches relevant data from AstraDB or external sources.
     - **Response Generation Agent**: Uses the LLM to generate a response.
     - **Validation Agent**: Ensures the response is accurate and relevant before sending it to the user.
   - These agents communicate and maintain state using LangGraph’s built-in state management capabilities.

7. **End-to-End Workflow**:
   - The workflow progresses from the **START node** to the **Router**, then to the appropriate data source, and finally to the **Response Generation** and **Validation** nodes.
   - The process concludes at the **END node**, where the final response is delivered to the user.

8. **Scalability and Flexibility**:
   - The system is designed to be scalable, allowing additional data sources or LLMs to be integrated seamlessly.
   - The use of LangGraph ensures flexibility in modifying the workflow or adding new agents as needed.

---

### **Summary**

This project creates a sophisticated multi-AI RAG chatbot system using **LangGraph** for state management and workflow orchestration, **AstraDB** for vector storage, and **Groq API** with the **Gemma-2b-9It** model for response generation. By integrating external data sources like Wikipedia and Arxiv, the system provides accurate and contextually relevant responses to user queries. The enhanced routing mechanism, multi-agent collaboration, and dynamic query handling make the system highly efficient and scalable. This project demonstrates the power of combining advanced AI tools and frameworks to build intelligent, end-to-end chatbot solutions.
