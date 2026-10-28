s = 's = %r\nprint(s %% s)'
print(s % s)
import os
import chromadb
from chromadb.utils import embedding_functions

# 1. Initialize the Chroma Client (Persistent Storage)
chroma_client = chromadb.PersistentClient(path="./chroma_code_db")

# 2. Use a standard embedding function (Default or OpenAI)
# For OpenAI, use: embedding_functions.OpenAIEmbeddingFunction(api_key="YOUR_KEY")
sentence_transformer_ef = embedding_functions.DefaultEmbeddingFunction()

# 3. Create or get the collection for your codebase
collection = chroma_client.get_or_create_collection(
    name="my_codebase", 
    embedding_function=sentence_transformer_ef
)

# 4. Helper to ingest code snippets with metadata
def add_code_to_chroma(file_path: str, snippet_id: str, code_content: str, line_start: int):
    collection.add(
        documents=[code_content],
        metadatas=[{"file_path": file_path, "line_start": line_start}],
        ids=[snippet_id]
    )
    print(f"Ingested {snippet_id} from {file_path}")

# Example Ingestion
sample_code = """
def calculate_fibonacci(n):
    if n <= 0:
        return 0
    elif n == 1:
        return 1
    return calculate_fibonacci(n-1) + calculate_fibonacci(n-2)
"""
add_code_to_chroma(
    file_path="math_utils.py", 
    snippet_id="fib_001", 
    code_content=sample_code, 
    line_start=1
)

# 5. Query the codebase using semantic natural language
def query_codebase(user_query: str, num_results: int = 1):
    results = collection.query(
        query_texts=[user_query],
        n_results=num_results
    )
    return results

# Example Query
search_result = query_codebase("Find the function that computes a recursive sequence")
print("\n--- Search Results ---")
for doc, metadata in zip(search_result['documents'][0], search_result['metadatas'][0]):
    print(f"Found in {metadata['file_path']} (Line {metadata['line_start']}):")
    print(doc)
