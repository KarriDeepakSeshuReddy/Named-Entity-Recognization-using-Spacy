# Named Entity Recognition (NER) with spaCy and Visualization

## 📌 Project Overview

This project trains a custom Named Entity Recognition (NER) model using **spaCy** to identify medical-related entities like medicines and medical conditions. The project also includes multiple visualization techniques to analyze and present the extracted entities.

## 🚀 Features

- Train a **custom NER model** with labeled medical data.
- Use `spaCy` for entity recognition.
- **Visualize entities** using:
  - `displacy` for inline visualization.
  - Matplotlib for **bar charts**.
  - WordCloud for **entity representation**.
  - Save entity visualization as an **HTML file**.

## 📂 Project Structure

```
├── model-best/                 # Trained NER Model
├── train.spacy                 # Training Data (Processed)
├── config.cfg                  # Training Configuration
├── ner_visualization.html      # Saved NER visualization
├── main.py                     # Python script for inference and visualization
├── README.md                   # Project Documentation
└── requirements.txt             # Python dependencies
```

## 🛠 Installation & Setup

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/spacy-ner-medical.git
cd spacy-ner-medical
```

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Download spaCy model

```bash
python -m spacy download en_core_web_lg
```

## 🔥 Usage

### Run Named Entity Recognition (NER) on Sample Text

```python
import spacy
from spacy import displacy

# Load the trained model
nlp_ner = spacy.load("model-best")

# Sample text
doc = nlp_ner("Pepto-Bismol is used for treating diarrhea. Loperamide is another medicine that helps.")

# Display extracted entities
for ent in doc.ents:
    print(f"{ent.text} - {ent.label_}")
```

### 📊 Visualization

#### 1️⃣ Inline Visualization (Jupyter Notebook)

```python
displacy.render(doc, style="ent", jupyter=True)
```

#### 2️⃣ Save Visualization as HTML

```python
html = displacy.render(doc, style="ent", page=True)
with open("ner_visualization.html", "w", encoding="utf-8") as f:
    f.write(html)
```

#### 3️⃣ Bar Chart of Entities

```python
import matplotlib.pyplot as plt
from collections import Counter

entity_counts = Counter([ent.label_ for ent in doc.ents])
plt.bar(entity_counts.keys(), entity_counts.values(), color='skyblue')
plt.xlabel("Entity Type")
plt.ylabel("Count")
plt.title("Named Entity Recognition (NER) Counts")
plt.show()
```

#### 4️⃣ WordCloud of Extracted Entities

```python
from wordcloud import WordCloud

entity_text = " ".join([ent.text for ent in doc.ents])
wordcloud = WordCloud(width=800, height=400, background_color="white").generate(entity_text)

plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation="bilinear")
plt.axis("off")
plt.show()
```

## 🏆 Results

- Successfully trained a **custom spaCy NER model**.
- Identified entities like **medicines and medical conditions**.
- Visualized entities using multiple techniques.

## 📜 License

This project is licensed under the MIT License.

## 💡 Contributing

Feel free to contribute by submitting **issues** or **pull requests**!

## 🔗 Contact

For any queries, reach out to: [**your.email@example.com**](mailto\:your.email@example.com)

