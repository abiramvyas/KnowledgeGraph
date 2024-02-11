# KnowledgeGraph

## Need for knowledge base and graph
In the context of natural language processing (NLP), RAG (Retrieval-Augmented Generation) is a framework that combines retrieval and generation models to improve the quality and relevance of generated text. With RAG being one of the most important steps involved while integrating LLMs into applications, knowledge bases and graphs are important. 

Most companies that wish to leverage LLMs do not have their underlying text available to the public. This underlying text could be internal documents, policies and other frameworks that is very specific to the employees of the company.

## Process
1. Use the Hugging Face rebel-large model that is used for text2text generation and reframeing the relation extraction
2. Identify steps in order to create a knowledge base from short text as well as long text
3. For short text, perform basic checks as to whether existing relations exist and whether it needs to be added. 
    3.1 As part of this process, the text is cleaned, tokenized and the relations are identified
    3.2 Based on the knowledge base code conditions, it is added appropriately
4. For long text, spans are added in order to get more context
    4.1 A long text is split into chunks based on a span length along with overlap. This helps have multiple sentences as part of the relation
    4.2 Steps are similar to that of step 3 otherwise. 
5. There are cases where data is pulled from URL
    5.1 Store the article source, published date, etc.
    5.2 Any similar relations are checked by leveraging the Wikipedia API
    5.3 Similar URL content are merged together into relations
    5.4 Process similar to Step 4
6. Builiding the network is critical. Pyvis is used. For this process, every entity identified has a node that is added to it and every relation is added as an edge to this graph. Based on this the graph is built.
7. There is a scope where data is procured from multiple URLs. In this case, the data is obtained from google news. Certain pages aren't downloadable and workarounds have to be obtained.

## Packages Used 
1. transformers - AutoModelForSeq2SeqLM, AutoTokenizer. Hugging Face tokenizers and models
2. math - to identify the span size and chunks
3. torch - outputs of the tokenizer are converted to tensors
4. wikipedia - used to procure articles
5. newspaper - Article, ArticleException. Data from articles
6. GoogleNews - procure articles from google news
7. pyvis.network - building the graph network

## Possible Inputs 
1. Sentence
2. Short Text
3. Long Text
4. URL
5. Articles
6. Multiple URLs

## Outputs
1. Knowledge base graph network stored as a HTML

Reference taken from - "https://medium.com/nlplanet/building-a-knowledge-base-from-texts-a-full-practical-example-8dbbffb912fa"

