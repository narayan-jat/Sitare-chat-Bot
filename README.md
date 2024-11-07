# Sitare Chat Bot

This project is a Q&A bot designed to answer frequently asked questions (FAQs) about Sitare University, particularly focusing on the admissions process. The bot leverages sentence embeddings to provide accurate, contextually relevant answers to users’ questions based on a pre-existing dataset of question-answer pairs.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Technology Stack](#technology-stack)
3. [Dataset Preparation](#dataset-preparation)
4. [Methodology](#methodology)
5. [Deployment and Usage](#deployment-and-usage)
6. [Future Improvements](#future-improvements)

---

## Project Overview
The Sitare Chat Bot utilizes a **vector similarity search** approach to efficiently retrieve answers to frequently asked questions. Users can type in their questions about admissions, and the bot will return the most relevant answer based on a pre-stored database of question-answer pairs. 

This project can:
1. Provide immediate answers to common admissions queries.
2. Help Sitare University streamline responses to applicants.
3. Ensure that users receive consistent and accurate information.

## Technology Stack
The bot relies on the following tools and technologies:
- **Sentence-BERT (SBERT)**: Used for generating contextual embeddings for questions and answers, which capture the semantic meaning of text.
- **PG Vector Database**: A PostgreSQL database with vector extension for storing and querying embeddings.
- **Cosine Similarity**: Used to compare user questions with stored embeddings to find the closest match.
  
## Dataset Preparation
The dataset consists of pairs of questions and answers related to Sitare University admissions. Here’s an outline of how the dataset was processed:
1. **Question Embeddings**: Each question in the dataset is embedded using SBERT to generate a high-dimensional vector representation.
2. **Answer Embeddings**: Similarly, answer embeddings are generated for contextual matching.
3. **Database Storage**: The embeddings and their respective question-answer pairs are stored in a PG vector database for quick and efficient similarity search.

## Methodology
The bot follows these steps to handle user queries:

1. **User Query Processing**:
   - A user submits a question related to Sitare University admissions.
   
2. **Embedding Generation**:
   - The user’s question is processed through SBERT to generate an embedding vector.
   
3. **Similarity Calculation**:
   - The vector is compared with all question embeddings in the PG vector database using cosine similarity.
   - Only question-answer pairs with a similarity score above a predefined threshold are considered relevant.
   
4. **Answer Retrieval**:
   - The bot retrieves the most relevant question based on the similarity score.
   - It then returns the answer associated with that question to the user.

5. **Threshold Tuning**:
   - A similarity score threshold is used to filter out irrelevant matches, ensuring high relevance of the responses.

## Deployment and Usage
To deploy and use the Sitare Chat Bot:

1. **Requirements**:
   - Python 3.8+
   - Libraries: `transformers`, `torch`, `psycopg2` (for PostgreSQL), `sentence-transformers`
   - PostgreSQL database with vector extension (PG Vector)
   
2. **Database Setup**:
   - Set up a PostgreSQL database and install the PG Vector extension.
   - Load the question-answer pairs and their embeddings into the database.

3. **Running the Bot**:
   - Ensure that the model for embedding generation is loaded.
   - Run the bot script to allow real-time processing of user queries.

4. **Query Example**:
   - User asks: "What is the application deadline for the fall semester?"
   - The bot generates an embedding for this question and searches the database.
   - If a relevant match is found, the bot returns the associated answer.

## Future Improvements
Here are some ways to enhance the bot:

1. **Threshold Optimization**: Adjust the similarity score threshold dynamically based on query type or frequency.
2. **Answer Re-ranking**: Use additional NLP techniques to re-rank answers for ambiguous questions.
3. **Model Fine-Tuning**: Fine-tune SBERT with university-specific FAQs to improve response accuracy.
4. **User Feedback Loop**: Add a feedback mechanism to improve response quality over time.
