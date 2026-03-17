# Project Description: Banking App Review Sentiment and Topic Analysis

## Project Details:
This project involves performing a detailed sentiment and topic analysis on banking application reviews for HDFC Bank and Yono SBI. The primary goal is to understand user perceptions, identify key areas of satisfaction and dissatisfaction, and categorize common pain points using advanced Natural Language Processing (NLP) techniques.

## Problem Statements:
1.  To understand the overall sentiment (positive, negative, neutral) of user reviews for HDFC Bank and Yono SBI mobile applications.
2.  To identify and compare the effectiveness of traditional (VADER) versus advanced (RoBERTa) sentiment analysis models in classifying banking app reviews.
3.  To pinpoint specific themes and recurring issues in both positive and negative reviews for each bank.
4.  To uncover latent groupings of negative feedback (pain points) across both banking apps through clustering, enabling a deeper understanding of user grievances.

## Key Activities:
1.  **Data Loading and Preprocessing:** Loading review data from CSV files for HDFC Bank and Yono SBI, and initial cleaning.
2.  **VADER Sentiment Analysis:** Applying VADER (Valence Aware Dictionary and sEntiment Reasoner) to classify reviews into Positive, Negative, and Neutral sentiments for both banks.
3.  **RoBERTa Sentiment Analysis:** Utilizing a pre-trained RoBERTa model from Hugging Face Transformers for more nuanced sentiment classification.
4.  **Sentiment Comparison:** Generating a comparative table of sentiment distribution (Positive, Negative, Neutral counts) for both banks across VADER and RoBERTa models.
5.  **Topic Extraction:** Identifying the top 10 most frequently discussed topics within positive and negative review subsets for each bank, after refining stopwords to exclude generic sentiment words.
6.  **Combined Negative Review Clustering:** Combining all negative reviews from both banks, performing TF-IDF vectorization and Truncated SVD for dimensionality reduction.
7.  **Optimal Cluster Determination:** Employing the Elbow Method to determine the optimal number of clusters for the combined negative reviews.
8.  **K-Means Clustering and Interpretation:** Applying K-Means clustering and interpreting each cluster by extracting its top topics, thereby identifying distinct categories of user pain points.

## Technologies Used:
*   **Python:** Programming language for analysis.
*   **pandas:** For data manipulation and analysis.
*   **numpy:** For numerical operations.
*   **matplotlib & seaborn:** For data visualization.
*   **nltk:** For natural language processing tasks (tokenization, stopwords, VADER sentiment).
*   **transformers (Hugging Face):** For implementing the RoBERTa sentiment analysis model.
*   **scikit-learn:** For TF-IDF vectorization, Truncated SVD, and K-Means clustering.

## Nature and Source of Data:
The data consists of user reviews for banking applications. Specifically, reviews for HDFC Bank and Yono SBI were used, sourced from respective CSV files: `/content/HDFC_Bank_Reviews.csv` and `/content/Yono_SBI_Reviews.csv`. Each dataset was downsampled to the first 500 rows for efficient processing during analysis.

## Observation:

### 1. Sentiment Analysis Overview (Positive/Negative Counts):

| Bank     | Method  | Positive | Negative | Neutral |
| :------- | :------ | :------- | :------- | :------ |
| HDFC     | VADER   | 350      | 88       | 62      |
| HDFC     | RoBERTa | 269      | 133      | 98      |
| Yono SBI | VADER   | 255      | 149      | 96      |
| Yono SBI | RoBERTa | 178      | 216      | 106     |

*   **HDFC Bank:** VADER identifies a significantly higher number of positive reviews (350) compared to RoBERTa (269). RoBERTa classifies more reviews as Negative (133) and Neutral (98) for HDFC.
*   **Yono SBI:** VADER shows more positive reviews (255) than negative (149). In contrast, RoBERTa identifies more negative reviews (216) than positive (178), suggesting a stricter or more accurate negative sentiment detection for Yono SBI.

### 2. Cluster Topics from Combined Negative Sentiments (Ranked by Strength/Size):

**Total Negative Reviews Clustered:** 349

1.  **Cluster 2: Core App Functionality & Login Issues (Largest Cluster)**
    *   **Number of Reviews:** 225
    *   **Top Keywords:** `app`, `update`, `new`, `time`, `bank`, `login`, `one`, `open`, `account`, `issue`
    *   **Interpretation:** This is the most prevalent pain point, focusing on fundamental app problems, especially concerning updates, login difficulties, and accessing accounts. This cluster highlights critical issues that affect a large user base.

2.  **Cluster 4: Version Change & Usability Problems**
    *   **Number of Reviews:** 34
    *   **Top Keywords:** `version`, `app`, `new`, `old`, `working`, `user`, `use`, `friendly`, `cant`, `download`
    *   **Interpretation:** Users are struggling with usability and interface changes due to new app versions, encountering difficulties in using, downloading, or finding the app user-friendly.

3.  **Cluster 3: App Not Working Properly**
    *   **Number of Reviews:** 25
    *   **Top Keywords:** `working`, `app`, `application`, `properly`, `update`, `always`, `also`, `every`, `new`, `mobile`
    *   **Interpretation:** This cluster explicitly addresses performance issues where the app or application does not function correctly, often after updates and sometimes tied to mobile device compatibility.

4.  **Cluster 6: Recurring Experience & Login Issues**
    *   **Number of Reviews:** 21
    *   **Top Keywords:** `experience`, `app`, `update`, `login`, `new`, `show`, `working`, `unable`, `last`, `months`
    *   **Interpretation:** This cluster signifies long-standing or repeated problems, with users reporting persistent negative experiences related to app performance, updates, and login failures over several months.

5.  **Cluster 0: Overall App/Service Issues & Difficulty**
    *   **Number of Reviews:** 18
    *   **Top Keywords:** `app`, `ever`, `service`, `bank`, `aap`, `seen`, `compared`, `banking`, `difficult`, `understand`
    *   **Interpretation:** Represents general dissatisfaction with the banking app and service, often citing difficulties in understanding or navigating, and comparing unfavorably to other experiences.

6.  **Cluster 1: Outdated/Old App Version Issues**
    *   **Number of Reviews:** 16
    *   **Top Keywords:** `app`, `old`, `new`, `time`, `aap`, `experience`, `application`, `many`, `times`, `working`
    *   **Interpretation:** Users express concerns about the app's version, preferring older versions or noting a decline in experience with newer ones, indicating stability or feature changes are not well-received.

7.  **Cluster 5: Disappointment with Updates/Login**
    *   **Number of Reviews:** 10
    *   **Top Keywords:** `disappointed`, `update`, `time`, `login`, `version`, `working`, `unable`, `account`, `every`, `want`
    *   **Interpretation:** This smallest cluster captures reviews with strong negative sentiment and `disappointment` directly linked to app `update`s and `login` issues, often resulting in an inability to access accounts.


# Overall Insights (Market-Level Perspective)

From a competitive standpoint, this analysis highlights key gaps and opportunities in the existing banking app ecosystem:

- **Authentication & access are major failure points**  
  Competitors are struggling with login reliability and account access — a critical trust factor in fintech.

- **Frequent updates are harming user experience**  
  Instead of improving the product, updates are introducing bugs and reducing stability.

- **Core functionality is not stable**  
  Basic features like app opening, navigation, and transactions are unreliable.

- **User experience is declining over time**  
  New versions are perceived as less intuitive and less user-friendly.

- **Issues are recurring, not one-time**  
  Problems persist across months, indicating weak feedback loops and poor issue resolution.

---

# Strategic Recommendations (For a New Market Entrant)

If you are launching a new product in this market, you can gain a strong competitive advantage by addressing these gaps:

## 1. Make Reliability Your Core Differentiator
- Ensure **zero-failure login systems** (biometric + OTP + fallback mechanisms)  
- Focus on **high uptime and crash-free performance**  
- Build trust by making core banking functions flawless  

## 2. Adopt a “Stability Over Features” Approach
- Avoid frequent disruptive updates  
- Release **well-tested, incremental updates**  
- Use staged rollouts (beta → full release)  

## 3. Deliver a Superior User Experience (UX)
- Design a **simple, intuitive interface**  
- Reduce steps for key actions (login, transfer, account view)  
- Prioritize **ease of use for non-tech-savvy users**  

## 4. Build Strong Feedback & Resolution Systems
- Implement **real-time issue tracking and resolution**  
- Actively respond to user complaints  
- Use feedback loops to continuously improve  

## 5. Ensure Cross-Device Compatibility
- Optimize for **all mobile devices and OS versions**  
- Test extensively across low-end and high-end devices (important for Indian market)  

## 6. Position Your Brand Around Trust & Consistency
- Market your app as:
  - “Reliable”
  - “Always accessible”
  - “Hassle-free banking”  
- Trust is a major differentiator in financial services  

---


> **Key Takeaway:**  
> The biggest opportunity in this market is not innovation, but **execution excellence** — delivering a stable, reliable, and user-friendly product where competitors are currently failing.
