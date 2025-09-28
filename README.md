# 📝 Umma Prayer App Sentiment Analysis

This project performs a sentiment analysis of Umma prayer app reviews collected from the Google Play Store. It uses a **Lexicon-Based** approach for sentiment labeling and then classifies reviews using various **Machine Learning** models, including Naive Bayes, Random Forest, Logistic Regression, and Decision Tree.

-----

## 🎯 Key Features

The project covers a complete text analysis pipeline, from data acquisition to model implementation:

1.  **Data Collection (Web Scraping):** Scrapes up to **1000** recent reviews for the Umma app (`com.muslim.android`) directly from the Google Play Store.
2.  **Indonesian Text Preprocessing:**
      * **Data Cleaning:** Removes duplicates, links, mentions, hashtags, numbers, and punctuation.
      * **Case Folding & Slang Normalization:** Converts text to lowercase and normalizes Indonesian slang words (e.g., 'ga' to 'tidak', 'aja' to 'saja') using an external slang dictionary.
      * **Stopword Removal:** Eliminates common words (stopwords) in both Indonesian and English.
      * **Stemming (Sastrawi):** Reduces words to their root form (e.g., 'menggunakan' to 'guna').
3.  **Sentiment Labeling (Lexicon-Based):** Applies an Indonesian sentiment lexicon dictionary to score and label reviews as **Positive, Negative,** or **Neutral**.
4.  **Data Visualization:**
      * Bar and pie charts to show the **distribution of sentiment polarity**.
      * **Word Clouds** to visualize the most frequent words across Global, Positive, and Negative reviews.
      * Visualization of the **Top 20 Words** based on TF-IDF values.
5.  **Sentiment Classification (Machine Learning):**
      * Feature extraction using **TF-IDF Vectorization**.
      * Implementation and evaluation of models: **Naive Bayes (BernoulliNB), Random Forest, Logistic Regression,** and **Decision Tree**.
6.  **Model Testing:** The model with the highest test accuracy (**Logistic Regression** at approximately $\approx 81\%$) is selected for predicting the sentiment of new, unseen reviews.

-----

## 🛠️ System Requirements & Installation

To run this notebook, you need a Python environment. Use `pip` to install the necessary libraries.

### 📦 Libraries

The following libraries must be installed. You can install them all at once:

```bash
!pip install google-play-scraper
!pip install sastrawi
!pip install nltk
!pip install swifter
!pip install pandas numpy matplotlib seaborn scikit-learn wordcloud requests
```

Alternatively, if you have a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### 🌍 External Requirements

  * **Internet Access:** Required for web scraping reviews from the Google Play Store, downloading NLTK resources, and loading the slang dictionary and sentiment lexicon from GitHub URLs.
  * **Slang and Sentiment Lexicons:** The project automatically loads these resources from the GitHub URLs provided in the code (`slangdict.json`, `lexicon_positive.csv`, `lexicon_negative.csv`).
  * **Google Drive (Optional):** Required if you intend to use the checkpoint feature to save the pre-processed data to Google Drive.

-----

## 🚀 How to Run

1.  **Download or Clone** this repository (if available, or copy the code to your Colab/Jupyter environment).
2.  **Open the `Umma_Prayer_App_Sentiment_Analysis.ipynb` file** in Jupyter Notebook or Google Colab.
3.  **Run all code cells sequentially.** Make sure to:
      * Run the installation cells (`!pip install...`) first.
      * Run the library import and NLTK initialization cells (`nltk.download(...)`).
4.  **Scraping Dataset:** The scraping code cell will fetch new reviews (up to 1000) from the Play Store.
5.  **Preprocessing:** This process, especially **Stemming** and **Slang Normalization** using `swifter`, will take some time to complete.
6.  **Labeling & Analysis:** Sentiment visualizations and model evaluations will appear in subsequent cells.
7.  **Final Testing:** The last cell allows you to input a new sentence to test its sentiment using the trained **Logistic Regression** model.
