# IPEN5810mini-project1
Text analysis project: Topics of employee reviews
(Note that the dataset used for this project is too large to be uploaded in the repository)
## objectives
## methodologies
First, I combine the four columns of review_summary, review_advice, review_pros and review_cons into one column for the analysis of the complete data. I then preprocessed the review data, such as removing punctuation, stopping words, all lowercase, tokenization, etc. Then the df and tf-idf values of the words were calculated, and the words with smaller tf-idf values were deleted. For the cleaned words, I constructed an LDA model. And found the top ten themes. These ten themes were then visualized.
## findings
