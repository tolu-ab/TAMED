# TAMED
Our AI-powered tool analyzes vast amounts of unstructured data to provide accurate and comprehensive information about a company's ESG performance using the power of Natural language processing techniques to make sense of unstructured data which traditionally requires the need for an human analyst. It provides actionable recommendations for investment decisions, improving the decision-making process for investors, asset managers and risk managers looking to align their investments and portfolio with their values or looking to minimize climate-related risks. The tool's AI-powered recommendation engine will have the power to analyze more data and provide more objective analysis than human analysis. It will feature a user-friendly interface for easy access and interaction with the data and insights. This will make it easy for both novice and experienced investors to use. 
# HIGH LEVEL PROTOTYPE
![image](https://user-images.githubusercontent.com/57208663/212286798-ac592f1e-824a-4590-9cec-e698f23ab1be.png)
prototype link - https://www.figma.com/proto/kTGwQJo6m7WrzJG3SAWvxL/TAMED?page-id=0%3A1&node-id=2%3A1186&viewport=466%2C1053%2C0.44&scaling=contain&starting-point-node-id=2%3A1186
# APP INFRASTRUCTURE
![Group 300](https://user-images.githubusercontent.com/57208663/212309961-4b7a95a5-4a8a-43c2-b398-212322ca80a3.png)
- Data Collection and Preparation:
Collection of unstructured data from various sources such as company reports, news articles, reporting frameworks, legal information and social media.
The data will be cleaned and preprocessed, removing any irrelevant information and formatting the data in a way that is usable for the NLP model.
The cleaned data is then stored in a database or other data storage system for later use.
- Natural Language Processing (NLP) Model:
NLP libraries and machine learning models will be used to extract insights from the unstructured data. The models will be trained and fine-tuned using a large dataset of labeled data. The NLP model will then be able to identify sentiment, entities and topics from the data.
- ESG Analysis and Scoring:
The app will use the insights generated by the NLP model and other data sources to analyze and score the ESG performance of various companies. It will use predefined metrics and standards to analyze and score the companies' ESG performance. The results of the analysis and scoring will then be stored in the database.
- User Interface (UI):
Users will be able to access and interact with the data and insights generated by the model via the GUI. The GUI will include features like search, filtering, and visualization of the data.
- Backend:
The app's backend will communicate with the front end, the database and other components of the tool. It will manage the data flow and the access to the data, ensuring the security and privacy of the data. It will also ensure that the app will be able to handle large amounts of data and can scale as needed.

**Others things that should be considered:**
A variety of different algorithms for natural language processing tasks such as tokenization, named entity recognition, sentiment analysis, and topic modeling will be needed to extract insights from the unstructured data. Additionally, algorithms such as supervised and unsupervised learning, recurrent neural networks, transformer models and others might be needed.

A variety of APIs might also be needed to access data from different sources, such as company reports, news articles, legal regulations, financial data, and social media.

combination of different ML methods to extract insights from the unstructured data. For example, it could use supervised learning methods, such as decision trees, random forests, or logistic regression, to classify text based on predefined categories. It could also use unsupervised learning methods, such as clustering or dimensionality reduction, to identify patterns and relationships in the data.

This is an high level code snippet of how it might work. Real-world implementation might require more complexity and expertise than we currently have access to

```python
import pandas as pd
import numpy as np
import spacy

# Load the NLP model
nlp = spacy.load('en_core_web_sm')

# Function to extract insights from unstructured data
def extract_insights(text):
    doc = nlp(text)
    sentiment = 0
    entities = []
    topics = []
    for token in doc:
        sentiment += token.sentiment
        if token.ent_type_ == "ORG":
            entities.append(token.text)
        if token.text in ["renewable energy", "carbon emissions", "diversity and inclusion"]:
            topics.append(token.text)
    return sentiment, entities, topics

# Load the data
data = pd.read_csv("companies_data.csv")

# Extract insights from the data
insights = []
for i in range(data.shape[0]):
    sentiment, entities, topics = extract_insights(data.iloc[i, 0])
    insights.append([sentiment, entities, topics])

# Store the insights in a new dataframe
insights_df = pd.DataFrame(insights, columns=["sentiment", "entities", "topics"])

# Add the insights to the original dataframe
data = pd.concat([data, insights_df], axis=1)

# Analyze and score the companies' ESG performance
scores = []
for i in range(data.shape[0]):
    score = 0
    if data.iloc[i, 1] > 0:
        score += 1
    if "renewable energy" in data.iloc[i, 3]:
        score += 1
```   
