# 🤖 ML for Cybersecurity: Phishing URL Detector

This mini-project is a hands-on demonstration of applying machine learning for cybersecurity. I built a classifier using Python, Pandas, and Scikit-learn to detect phishing URLs from legitimate ones.

This project was built to bridge my skills in **data analysis** and **mathematical modeling** from my physics background directly to the **threat detection** and **analytical** challenges in cybersecurity.

---

## 🎯 Project Objective

The goal is to build and evaluate a machine learning model that can accurately classify a URL as either "legitimate" or "phishing." This has direct applications in real-world security tools like email filters and web browser security.

---

## 🛠️ How It Works

### 1. Data Source
* **Dataset:** [Phishing Site URLs](https://www.kaggle.com/datasets/shashwatwork/phishing-dataset-for-machine-learning)
* **Size:** 10,000 URLs, evenly split between 5,000 legitimate and 5,000 phishing.

### 2. Feature Engineering
This was the core of the project. I extracted 6 numerical "clues" (features) from each raw URL string:
* `url_length`: The total number of characters in the URL.
* `has_ip`: Does the URL use an IP address instead of a domain name? (1 for Yes, 0 for No).
* `has_at`: Does the URL contain an `@` symbol? (A common trick).
* `special_chars`: The total count of `.`, `-`, `?`, `=`, `&`, and `/`.
* `has_httpss`: Does the URL use `https`?
* `digit_count`: The total number of digits (0-9) in the URL.

### 3. Model & Training
* **Model:** I used a **Random Forest Classifier** (`n_estimators=100`), which is an ensemble of 100 decision trees.
* **Process:** The data was split 80/20 into a training set and a testing set. The model was trained *only* on the training data.

---

## 📈 Results & Evaluation

The model was evaluated on the 20% test set (data it had never seen before).

* **Overall Accuracy:** **97.10%** *(This was the result from my test; your exact number may vary slightly.)*

### Key Metrics:
* **Recall (Phishing):** **97%**. This is the most important security metric. It means our model successfully **caught 97% of all actual phishing sites** in the test set.
* **False Negatives:** **28**. This is the number of real phishing sites that the model *missed* (classified as legitimate). In a real-world scenario, this is the number one metric to minimize.

### Feature Importance
The model found that the most important "clues" for detecting a phish were:
1.  `special_chars`
2.  `url_length`
3.  `digit_count`

---

## 🚀 How to Run This Project

1.  Clone this repository:
    ```bash
    git clone [https://github.com/theoretical2015physics-dev/ML-in-Cybersecurity.git](https://github.com/theoretical2015physics-dev/ML-in-Cybersecurity.git)
    ```
2.  Install the required libraries:
    ```bash
    pip install -r requirements.txt
    ```
3.  **Download the data:** Go to [this Kaggle link](https://www.kaggle.com/datasets/shashwatwork/phishing-dataset-for-machine-learning) and download `Phishing_Legitimate_full.csv`. Place it in the root of the project folder.
4.  Run the Jupyter Notebook:
    ```bash
    jupyter lab ML_for_cybersecurity_phishing_detector.ipynb
    ```
