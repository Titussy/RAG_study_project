# RAG_study_project


This is the case study for Retrieval Augmented Generation, and this project mainly follows https://github.com/mrdbourke/simple-local-rag.
Notice: The workout will not be the same as the above link


The file `00-simple-local-rag.ipynb` will show the detailed steps and my progress for how to build up a Local Retrieval Augmented Generation (RAG) from Scratch.


## Workflow

1. **Download PDF Book**: Automate downloading *Human Nutrition: 2020 Edition* using `requests` or manually, then save as book `human-nutrution-text.pdf`
2. **Text Extraction and Chunking**: Extract text with `PyMuPDF`, split into 10 sentence chunks with overlap
3. **Embedding Generation**: Generate embeddings with `google/gemma-2b-it` and store in CSV file (`text_chunks_embeddings_df.csv`) (can be vector database, update later).
4. **Vector Search**: Perform a cosine similarity search to retrieve top-k relevant chunks for a query.
5. **Prompt Formatting**: Combine query and retrieved texts into an augmented prompt with clear instructions.
6. **Load LLM**: Use a quantized model (e.g., Mistral 2B) for local inference.
7. **RAG Pipeline**: Build a function to process query > embedding > retrieval > LLM generation.
8. **Generate Answer**: Pass the augmented prompt to the LLM for a concise, accurate response.

## Setup

Using Python 3.11.x for the PyTorch version
Make sure the PyTorch version is for CUDA

## Later Extension
- Deploy a chatbot application using Streamlit or Gradio for interactive querying.
- Add metadata filtering (e.g., by chapter) and query history.
- Deploy on cloud platforms (e.g., Heroku, AWS) with Pinecone for scalability.

## Test Queries
See `Test_Queries.txt` for 20 queries to evaluate the RAG system, covering nutrient functions, carbohydrate roles, and more.

## Limitations
- PDF parsing may miss interactive elements or tables.
- Local LLM performance depends on hardware (GPU recommended).
- Initial CSV storage may be replaced with Chroma for efficiency.
