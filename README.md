# 🤖 Fine-Tuned T5 Model for LeetCode-Style Question Title Generation 🎓💻

Welcome to the **T5 LeetCode-style Title Gen** repository! 🌟 This AI model has been fine-tuned on over 2,000 LeetCode questions to generate **LeetCode-style question titles** for coding questions on **University Computer Science Entrance Exams**. 📚✨

---

## 🧠 Model Purpose
This model is designed to:

- 📝 **Generate concise, professional, and LeetCode-style titles** for coding problems.
- 📖 **Help organize and standardize the presentation of questions** on University-level **Computer Science Entrance Exams**, mandatory assessments that aspiring computer science majors must pass to obtain official entrance into the major and take upper level courses. 🧑‍🎓👩‍🎓

By streamlining the titling process, this model supports:
- 🎯 Effective classification of coding problems allowing for more effective topic-based studying.
- 🏆 A polished and consistent experience for students and educators alike.

---

## 📊 Training Data
The model was fine-tuned on approximately **2,360 LeetCode problems** using the **`greengerong/leetcode` dataset** available on Hugging Face.

### Dataset Details:
- 💻 **Problem Descriptions**: Clear explanations of coding challenges.
- 📑 **Associated Question Titles**: Well-structured and concise titles for each problem.
- 💡 **Code Solutions**: Implementations in multiple languages, including:
  - Java
  - C++
  - Python
  - JavaScript

The fine-tuning process ensured that the model learned the **style and structure** of these titles, making it highly effective for generating LeetCode-style titles for new problems.

---

## 🛠️ How It Works
This fine-tuned version of the **T5 model** leverages its sequence-to-sequence capabilities to:

1. 💬 **Take a coding problem description as input** (e.g., "Write a function to find the longest common prefix in an array of strings.").
2. 🪄 **Generate a clear, professional title** (e.g., "Longest Common Prefix").

---

## 🔬 Evaluation Metrics
The model was evaluated using:

- 📏 **ROUGE Scores**: Measures the overlap between generated titles and reference titles.
  - **ROUGE-1**: Precision, recall, and F1 for unigrams.
  - **ROUGE-2**: Precision, recall, and F1 for bigrams.
  - **ROUGE-L**: Precision, recall, and F1 for longest common subsequences.

💻 Results indicate a strong ability to generate accurate and concise titles! 🚀

---

## 🚀 Quickstart

Here’s how you can use this model:

```python
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer

# Load the model and tokenizer
model = AutoModelForSeq2SeqLM.from_pretrained("your-username/fine-tuned-t5-model")
tokenizer = AutoTokenizer.from_pretrained("your-username/fine-tuned-t5-model")

# Input a coding problem description
description = "Write a function to check if a string is a valid palindrome."

# Tokenize and generate the title
inputs = tokenizer(f"Generate a LeetCode-style question title: {description}", return_tensors="pt")
outputs = model.generate(**inputs, max_length=15, num_beams=4, early_stopping=True)

# Decode the generated title
generated_title = tokenizer.decode(outputs[0], skip_special_tokens=True)
print("Generated Title:", generated_title)
