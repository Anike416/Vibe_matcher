# 🛍️ Nexora Vibe Matcher: Semantic Search for E-commerce
This repository contains the source code for a "vibe matcher" proof-of-concept, as part of an assignment. It's a simple semantic search engine built in a Python notebook that allows users to find products based on abstract vibes or styles rather than exact keywords.

# 🚀 The Business Case: Why AI at Nexora?
At Nexora, many customers browse with a specific vibe or style in mind (e.g., "cozy fall outfit"), not a precise product name. Traditional keyword search fails to capture this intent, leading to missed sales and a frustrating user experience. By implementing an AI-powered semantic search, we bridge this gap. This "vibe matcher" converts our product descriptions into rich vector embeddings, allowing us to understand the meaning behind queries. This not only creates a more intuitive and personalized shopping journey but also drives superior product discovery, which directly leads to higher customer engagement and increased conversion rates.

# ✨ Features
Semantic Search: Understands the meaning of queries, not just keywords.

Vibe Matching: Finds products that match abstract queries like "energetic urban chic" or "comfortable casual."

Vector Embeddings: Uses the google/embeddinggemma-300m model via the Hugging Face Inference API to convert text into numerical vectors.

Cosine Similarity: Ranks search results by calculating the mathematical "closeness" between the query vector and the product vectors.

Performance Metrics: Includes basic latency tracking to measure search speed.

# ⚙️ How to Run This Notebook
This notebook is designed to be run in an environment like Google Colab or a local Jupyter server.

## Clone the Repository:


'''  git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
cd YOUR-REPOSITORY  '''
Install Dependencies: The notebook will install its own dependencies, but you can also install them manually:



''' pip install pandas numpy scikit-learn matplotlib huggingface_hub
Set Your API Key (Securely): This project requires a Hugging Face API Token to run. It is intentionally not hard-coded. The notebook uses getpass to securely ask for your key when you run it.

When prompted, paste your hf_... token into the secure input box.

Python

## The code used in the notebook:
'''python
from getpass import getpass
import os

if "HF_TOKEN" not in os.environ:
    os.environ["HF_TOKEN"] = getpass("Enter your Hugging Face API Key: ) 
'''
Run the Notebook: Open vibe_matcher.ipynb and select "Run All" in your notebook environment. The notebook is saved with all outputs visible, so you can also review the results directly without re-running.

# 📈 Example Results
The evaluation loop tests three queries. The system successfully finds 9 "good matches" (similarity > 0.7) across these queries, indicating high relevance.

## Query Latency
The plot below shows the time taken for each query. The first query takes the longest (approx. 0.36s) due to the "cold start" of establishing a secure connection to the API. Subsequent queries are much faster as they reuse the warm connection.

# 🔮 Reflection & Future Improvements
This notebook is a simple proof-of-concept. To make it a production-ready feature, the following steps would be necessary:

Integrate a Vector Database: For scalable and fast search across millions of products, we would replace the numpy array with a dedicated vector database (e.g., Pinecone, Weaviate, or ChromaDB).

Expand the Dataset: The model would be much more effective if trained or fine-tuned on a larger dataset with richer product details (e.g., materials, user reviews, multi-modal image data).

Dynamic Thresholding: Implement user feedback (e.g., "was this relevant?") to dynamically refine matching thresholds and improve relevance over time.

Query Understanding: Handle synonymy ("comfy" vs. "comfortable") and slang in vibe queries for better recall.

Optimize Caching: Implement embedding caching to reduce redundant API calls and latency. A vector database would handle this automatically.
