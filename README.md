# Basic-RAG-Implementation
Built a RAG pipeline which enables us to generate responses based on a query.

## What is RAG?

RAG stands for Retrieval Augmented Generation.

Each phase can be approximately divided into: 

  1. Retrieval - Act of searching for relevant information from a source based on a specific query. For instance, retrieving relevant snippets of Wikipediacontent from            database in response to a certain question.
        
  2. Augmented - Process of utilizing relevant returned information to alter an input for a generative model, such as an LLM.
        
  3. Generation - Process of producing an output based on a particular input. For instance, while considering an LLM, the task involves creating a written piece based            on a specified prompt.
  

● The main goal of RAG is to improve the generation outputs of LLMs.



## Workflow of RAG

Now let’s understand the basic workflow of a RAG based LLM architecture in three steps:

1. Ingestion
2. Synthesis
3. Retrieval

<img src="https://github.com/Ananya0104/Basic-RAG-Implementation/blob/main/rag.jpeg">


### Ingestion

● This involves storing the documents in a vector database. It has the following parts:

1. Chunking - Chunking is breaking up the documents to be accessed into smaller pieces. One can define these chunks either by a given character count, sentences or paragraphs. Larger chunks could contain useless material, adding noise and maybe lower the retrieval accuracy. Reducing the chunk size helps RAG to strike a balance between accuracy and completeness.
  
2. Embeddings - Once documents are chunked appropriately, the next step is to embed it. They are the vector representations of every text in the document that convert the user's query and the knowledge base documents into a numerical format for relevance comparison using similarity techniques. This mechanism helps RAG answer user queries with the most relevant knowledge base information.
  
3. Database - These embedding vectors are stored in vector databases. A vector database stores data as embeddings. Vector databases are advantageous for fast and accurate similarity search and data retrieval as it allows to find the most relevant data based on semantic or contextual meaning instead of exact matches or predefined criteria.


   
### Retrieval

●  Here the user query is embedded using the same embedding technique applied for embedding documents. Using cosine similarity method, top k relevant chunks present in the form of embeddings in our vector database are obtained by means of this embedded user query. These relevant bits are then rebuilt in their original form.



### Synthesis

●  The last step of the RAG pipeline is to generate responses back to the user. In this step, the model synthesizes the retrieved information with its pre-trained knowledge to generate contextually relevant responses.



## Limitations of RAG

   1. Confusing different meanings — Words with many meanings are a major retrieval difficulty. The term “apple” may mean fruit or technological enterprise. RAG systems may              misinterpret these meanings and retrieve irrelevant information.
  
   2. Difficulty in finding close matches — RAG algorithms may find it difficult to distinguish among closely related subjects in big datasets, which would lead to less precise          matches.
   
   3. Inadequate augmentation — naive RAG systems may struggle to properly contextualize or synthesize the retrieved data, leading to augmentation that lacks depth to accurately         address the objective of the query.
