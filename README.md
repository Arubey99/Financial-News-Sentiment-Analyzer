## Financial News Sentiment Analysis

This project focuses on analyzing sentiment in financial news articles to gauge market sentiment and recession-related fears in the U.S. equity market. Developed as part of an assignment for BNP Paribas, this project uses **language models (LLMs)** and financial data to create a sentiment analysis pipeline tailored for financial news.

### Features
- **Data Collection**:
  - Uses the **NewsAPI** to fetch equity-focused articles in English within a specified date range.
  - Daily data retrieval is saved locally to avoid redundant API calls.
  - Processes up to 10 articles per day, adhering to API rate limits.

- **Sentiment Analysis**:
  - Employs **OpenAI's GPT-3.5-Turbo** for scoring sentiment based on recession fears.
  - Sentiment scores range from:
    - Negative (recession-safe): -1 to -0.33
    - Neutral: -0.33 to 0.33
    - Positive (recession fears): 0.33 to 1
  - Extracts relevant sectors, confidence scores, and sentiment from news articles.

- **Visualization and Trends**:
  - Generates time series visualizations of sentiment trends across 39 predefined sectors.
  - Compares sentiment trends with the **Fear and Greed Index** for validation.
  - Sector-specific time series allow detailed analysis of trends.

- **Error Handling and Efficiency**:
  - Implements exponential backoff for handling API rate limits and timeout errors.
  - Saves prompts and responses for debugging purposes.
  - Efficiently manages token constraints for GPT API usage.

### Methodology
1. **Preprocessing**:
   - Removes irrelevant HTML tags, styles, and scripts from article text.
   - Cleans and structures raw data into a readable format.

2. **Sentiment Analysis Pipeline**:
   - Retrieves full article content.
   - Sends cleaned text to GPT-3.5 for sentiment scoring.
   - Extracts and logs sentiment scores, confidence levels, and sector relevance.

3. **Data Storage and Updates**:
   - Stores sentiment data in CSV files to track daily sentiment trends.
   - Processes and appends new data without reprocessing previously analyzed dates.

4. **Visualization**:
   - Plots time series for daily sentiment and confidence scores.
   - Creates sector-specific sentiment trends for in-depth analysis.

### Challenges
- **API Limitations**:
  - Free NewsAPI only provides access to the past month of articles and limits daily article retrieval.
  - Token constraints led to switching from GPT-4 to GPT-3.5-Turbo for budgetary reasons.

- **Efficiency**:
  - Managed multiple API keys to maximize article coverage.
  - Minimized batch processing due to limited data volume.

### Future Work
- **Forecasting**:
  - Incorporate models like ARIMA or LSTM to predict future sentiment trends.
- **Sector-Specific Insights**:
  - Use topic modeling for deeper analysis within sectors.
- **Expanded Indicators**:
  - Extend analysis to other economic indicators, such as inflation or interest rates.
- **Model Cross-Validation**:
  - Validate sentiment scores using additional AI models.

### Libraries and Tools
- **Python Libraries**: pandas, NumPy, Matplotlib, requests, and others for data processing and visualization.
- **APIs**: NewsAPI for article retrieval and OpenAI API for sentiment scoring.

---

This repository provides an innovative approach to understanding financial sentiment through news analysis. Contributions and suggestions for improving the methodology or extending its scope are welcome.
