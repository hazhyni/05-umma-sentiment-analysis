# 📝 Umma Prayer App Sentiment Analysis

This project performs a sentiment analysis of user reviews for the Umma prayer app, collected from the Google Play Store. The workflow involves extensive Indonesian text preprocessing, sentiment labeling using a **Lexicon-Based** approach, and classification using various **Machine Learning** models.

The final classification demonstrated the **Logistic Regression** model achieving the highest test accuracy ($\approx 81\%$).

## 🎯 Key Features

The project covers a complete Natural Language Processing (NLP) pipeline, from data acquisition to model implementation:

1.  **Data Collection (Web Scraping):** Scrapes up to **1000** recent user reviews for the Umma app (`com.muslim.android`) directly from the Google Play Store using the `google-play-scraper` library.
2.  **Robust Indonesian Text Preprocessing:**
      * **Data Cleaning:** Handles duplicates, links, mentions, hashtags, numbers, and punctuation.
      * **Slang Normalization:** Converts Indonesian slang words (e.g., 'ga' to 'tidak', 'aja' to 'saja') using an external slang dictionary.
      * **Stopword Removal:** Eliminates common words in both Indonesian and English.
      * **Stemming (Sastrawi):** Reduces Indonesian words to their root form (e.g., 'menggunakan' to 'guna').
3.  **Sentiment Labeling:** Applies a custom Indonesian sentiment lexicon to automatically label reviews as **Positive, Negative,** or **Neutral**.
4.  **Data Visualization:**
      * Distribution charts to visualize the **polarity of sentiment**.
      * **Word Clouds** to show the most frequent words across Global, Positive, and Negative review sets.
      * Bar plot of the **Top 20 Words** based on TF-IDF scores.
5.  **Machine Learning Classification:**
      * Feature extraction using **TF-IDF Vectorization**.
      * Comparative evaluation of four models: **Naive Bayes (BernoulliNB), Random Forest, Decision Tree,** and **Logistic Regression**.

-----

## 🛠️ System Requirements & Installation

To run this analysis, you need a Python environment with the following libraries installed.

### 📦 Pustaka (Libraries)

You can install all necessary packages using `pip`:

```bash
!pip install google-play-scraper
!pip install sastrawi
!pip install nltk
!pip install swifter
!pip install pandas numpy matplotlib seaborn scikit-learn wordcloud requests
```

### 🌍 External Data Dependencies

  * **Internet Access:** Required for the initial data scraping and to load external resources.
  * **External Dictionaries:** The project relies on the following files, which are automatically fetched from the provided GitHub URLs during runtime:
      * Indonesian Slang Dictionary
      * Positive Sentiment Lexicon (`lexicon_positive.csv`)
      * Negative Sentiment Lexicon (`lexicon_negative.csv`)

-----

## 🚀 How to Run the Analysis

1.  **Clone or Download:** Get a copy of the `Umma_Prayer_App_Sentiment_Analysis.ipynb` file.
2.  **Open:** Run the notebook in an environment like Google Colab or Jupyter Notebook.
3.  **Execute Cells:** Run all code cells sequentially from top to bottom.
      * The notebook will first install libraries and load the required dictionaries.
      * The **Scraping Dataset** section will retrieve up to 1000 new reviews.
      * The **Preprocessing** section, particularly Stemming and Slang Normalization, may take a few minutes to complete.
      * The **Machine Learning Implementation** section will train and evaluate all models, confirming Logistic Regression as the best performer.
4.  **Test New Input:** Use the final cell to test a new sentence, which will be processed and classified by the best-performing model (Logistic Regression).

-----

Now that we have the full documentation, we can dive into the **results** section of the project. We saw that **Logistic Regression** gave the highest test accuracy ($\approx 81\%$). Would you like to explore:

1.  The surprising reason why **Logistic Regression** often outperforms more complex models like Random Forest on sparse text data?
2.  How we could try to *improve* the accuracy, perhaps by tuning the TF-IDF parameters or using a different classification model?
3.  Analyzing the specific **positive and negative keywords** that the Lexicon method identified?
