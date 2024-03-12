# IPEN5810mini-project1

## Objectives

The primary objective of this project was to analyze and extract meaningful insights from a collection of text reviews. We aimed to understand the underlying sentiment, identify prevalent topics, and determine the relationship between the sentiment and these topics. The analysis was intended to provide a comprehensive overview of the general sentiment expressed in the reviews and to uncover the dominant themes that could inform future business decisions.

## Methodologies

### Data Preprocessing

- **Data Consolidation:** The textual data from four columns, namely `review_summary`, `review_advice`, `review_pros`, and `review_cons`, were merged into a single column to create a unified text corpus for analysis.
- **Text Cleaning:** We performed several preprocessing steps on the review data, which included:
  - Removing punctuation to avoid any interference in the analysis.
  - Eliminating stop words to focus on more meaningful words in the text.
  - Converting all text to lowercase to maintain uniformity and avoid duplication.
  - Tokenization to break down the text into individual words or tokens.

### TF-IDF Calculation

- We calculated the Term Frequency-Inverse Document Frequency (TF-IDF) values to reflect the importance of each word in the corpus.
- Words with lower TF-IDF values, which are less relevant to the context, were removed to refine the dataset.
- Plots were drawn to reflect the relationship between `tf-idf ranking` and `term ranking` 

### Topic Modeling

- Using the cleaned and preprocessed data, we constructed a Latent Dirichlet Allocation (LDA) model to discover the top ten themes in the text.

- The model was optimized by tuning hyperparameters such as the number of topics and learning decay based on 10% sample subset.
- We evaluated the model using metrics like Log Likelihood and Perplexity, and adjusted the model iteratively to improve its performance.
- We visualized the topic clusters by word clouds.

##### Additional notifications: LDA topic detection model specification

- `n_components`: the number of latent topics to be extracted
- `doc_topic_prior`/`alpha`: sparsity/density of the document-topic distribution
- `topic_word_prior`/`eta` or `beta`: sparsity/density of the topic-word distribution
- `learning_method`: algorithm used to update the topic-word distribution (`lambda`)
  - `batch`/`online`
  - `learning_decay`: learning rate in the 'online' learning method
- `learning_offset`: downweights early iterations
- `max_iter`: The maximum number of iterations to run the algorithm
- `evaluate_every`: Determines how often the perplexity is calculated to check convergence
- `perp_tol`: Perplexity tolerance in batch learning
- ......

### **Income correlation**

- We used 2 methods to rank the correlations between different topics and the 'income/wage/salary' cluster
  - Detect simple correlation with `df["rating_compensation_and_benefits"]` value
  - Apply the unsupervised machine learning method: Word2Vec similarity model
    - Borrow a pre-trained Word2Vec model of similarity from Google Drive
      - https://drive.google.com/file/d/0B7XkCwpI5KDYNlNUTTlSS21pQmM/edit?resourcekey=0-wjGZdNAUop6WykTtMip30g
    - Extract top keywords for each clustered topic
    - Define income-related keywords income', 'wage', 'salary', 'pay', 'compensation’
    - Measure similarity between vectors
- The two methods yield different ranks of correlations
  - with the machine learning one is considered more reliable

### Sentiment Analysis

- We applied sentiment analysis to extract `dominant topics`, `sentiments`, and `Sentiment_score`from the intergrated `review` data.
  - The sentiment scores were calculated using the compound metric from VADER, which provides a single continuous measure of sentiment from negative to positive.


#### Visualizations

##### **Sentiment Compound Score Distribution**

- Visualizes the spread of sentiment compound scores across the dataset.
- Scores range from -1 (very negative) to +1 (very positive), with 0 being neutral.
- Helps identify overall sentiment bias in the text data.
- Useful for understanding the emotional tone conveyed in large text corpora.

##### **Top 20 Named Entities**

- Lists the 20 most frequently occurring named entities (people, organizations, locations, etc.).
- Highlights key subjects and entities being discussed in the text.
- Can be used to track trends, brand mentions, or influential figures.
- Assists in content categorization and information extraction.

##### **Average Sentiment Score by Dominant Topic**

- Displays the mean sentiment score for each identified topic.
- Indicates which topics are discussed in more positive or negative terms.
- Aids in assessing the emotional context of different themes.
- Can inform content and communication strategies based on topic sentiment.

##### **Correlation between Sentiment Scores and Topic Weights**

- Shows the relationship between sentiment scores and the prominence of topics.
- Identifies topics that have stronger associations with positive or negative sentiments.
- Helps in understanding how certain topics influence the overall sentiment.
- Provides insights for targeted marketing or product feedback analysis.

## Findings

- **Sentiment Analysis:** The sentiment analysis revealed the overall sentiment distribution among the reviews, showing the prevalence of positive, neutral, or negative tones.
- **Topic Discovery:** The LDA model successfully uncovered the top ten/ five themes prevalent in the review data, providing a clear depiction of the subjects that reviewers focused on.
- **Named Entities:** The extraction of named entities highlighted the key focus areas and entities within the reviews, which could be of interest to stakeholders.
- **Correlation Insights:** The correlation analysis between sentiment scores and topic weights provided insights into how the sentiment of the reviews was influenced by the various themes identified by the LDA model.
- **Visualization:** The visualizations offered an intuitive understanding of the data, making it easier to interpret complex relationships and patterns.
