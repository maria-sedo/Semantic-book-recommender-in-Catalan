# Semantic book recommender in Catalan
Exercise 3 of the Natural Language Processing course. Master in Theoretical and Applied Linguistics

This project developed a semantic book recommender in Catalan that processes users’ preferences and matches them with book synopses. The aim was to assess whether NLP techniques can accurately capture natural language input and whether such a system can be built for Catalan. Although no similar system was found in open access, we expected that currently available resources would make it feasible.

To develop a book recommender that truly connected users’ interests with book content, instead of relying on genres, as many recommenders do, we developed a semantic book recommender that considers users’ preferences in their own words and matches them with books synopses. Specifically, this recommender was built using NLP techniques to process preferences in natural language and transform them into numerical representations (embeddings), in order to compute the semantic similarity between users’ input and book synopses. The system was built following a FreeCodeCamp tutorial (2025, January 27), complemented with additional resources (Barcelona Supercomputing Center, 2026; W3Schools, 2026b).

The development involved five main steps: dataset creation and cleaning, asking the user’s input, embedding generation, computing semantic similarity and presenting the recommendations.
As no suitable Catalan dataset was available, one was generated with Claude (Anthropic, 2026). With our guidance, Claude created a dataset of 671 books published between 1990 and 2025 with title, author, year, genre, synopsis and source, covering both original Catalan works and translations. To guarantee sufficiently descriptive content, synopses were required to contain at least 25 words. After verification, this threshold proved adequate. The dataset was created as an excel file (catalan_books.xlsx).

Both the user input and the synopses were encoded into embeddings using the SentenceTransformer model ST-NLI-ca_paraphrase-multilingual-mpnet-base (Barcelona Supercomputing Center, s.d), chosen for its support of vector representation and semantic search in Catalan. Cosine similarity was then computed to identify the most relevant books.

Similarity between the user’s description and the synopses was computed at the text-level (one embedding per text). Additionally, a word-level similarity analysis was performed between the user’s input and the final recommended books to improve interpretability by identifying the most similar words.

The output for the user presents five books with titles, synopses, similarity scores and keywords from the user’s input explaining the recommendation.

The project showed that a semantic book recommender in Catalan can be built using NLP techniques to capture natural language input. Despite the lack of existing datasets, the generated dataset proved to be useful and appropriate, like the SentenceTransformer model, for both text and word-level analysis, although a model trained specifically on book synopses could yield better results.

The recommendations are generally accurate. For example, we entered an input describing the first Harry Potter book and the system returned Harry Potter i la pedra filosofal as the top result, which matches the query perfectly. Overall, the word-level analysis produced mostly meaningful pair matches, indicating that the recommender captures relevant narrative aspects, even though some less precise pairs suggest room for improvement.

In this repository, the code for the recommender is provided along with the excel file containing the dataset created for the project. Different libraries are required: pandas, matplotlib, seaborn, sentence-transformers, spaCy and stopwordsiso. It also requires the SentenceTransformer model ST-NLI-ca_paraphrase-multilingual-mpnet-base (Barcelona Supercomputing Center, s.d), and the spaCy’s model ca_core_news_sm (Explosion, 2026). Development was carried out in Google Colab.

***References***

Anthropic (2026). Claude Sonnet 4.6. https://claude.ai/new

Barcelona Supercomputing Center (2026). AinaKit. https://langtech-bsc.gitbook.io/aina-kit

Barcelona Supercomputing Center (s.d). Projecte Aina. ST-NLI-ca_paraphrase-multilingual-mpnet-base. Hugging Face. https://huggingface.co/projecte-aina/ST-NLI-ca_paraphrase-multilingual-mpnet-base

Diaz, G. (2020). Stopwords ISO. GitHub. https://github.com/stopwords-iso/stopwords-iso?tab=readme-ovfile

Explosion (2026). Catalan. Ca_core_news_sm. https://spacy.io/models/ca

FreeCodeCamp (2025, January 27). LLM Course. Build a Semantic Book Recommender (Python, OpenAI, LangChain, Gradio) [video]. Youtube. https://www.youtube.com/watch?v=Q7mS1VHm3Yw&t=707s

W3Schools (2026b). Python Tutorial. https://www.w3schools.com/python/default.asp
