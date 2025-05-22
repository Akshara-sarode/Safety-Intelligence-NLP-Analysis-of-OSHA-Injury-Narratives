## 🧠 Safety Intelligence: NLP Analysis of OSHA Injury Narratives
This project applies Natural Language Processing (NLP) to analyze OSHA-style injury narratives, extracting sentiment and keywords to identify machine-specific risks. An interactive Power BI dashboard visualizes key patterns in injury severity, causes, and affected body parts, enabling data-driven workplace safety insights.



![image](https://github.com/user-attachments/assets/8f0e7363-ee81-4666-841e-9a4ba77bd45d)



## 🔍 PROJECT OVERVIEW
- This project builds a data-driven safety analytics system using:

## 🧠 NLP techniques for narrative classification

## 🗃️ SQLite for structured data exploration

- 📊 Power BI for rich visual dashboards

- The focus is on OSHA-style hand injury reports, where:

- Sentiment is analyzed using TextBlob 🧪

- Keywords are extracted using RAKE and TF-IDF 🔍

- Narrative polarity (Urgent, Severe, Neutral) helps gauge severity

- Machine-specific terms aid root cause analysis 🛠️

- All insights are presented via an interactive Power BI Dashboard, with KPIs, decomposition trees, and filtering capabilities for predictive safety management ✅

## 🚀 KEY OUTCOMES

- 🔧 Identified high-risk machines (e.g., Machine Saw, Hydraulic Press)

- ⚠️ Classified 20,000+ narratives as Urgent, Severe, or Neutral

- 🧵 Extracted risk keywords using RAKE and TF-IDF

- 🗺️ Mapped state-wise and time-based injury trends

- 🧬 Fused structured + unstructured data for holistic insights

- 📊 Built a rich, interactive Power BI dashboard

- 📌 Enabled recommendations for training, inspections, and policy

## 📂 DATASET INFORMATION

##📦 SOURCE
- Internal OSHA data + Hand Injuries with Machines dataset

## 📝 DESCRIPTION
- Includes 20,000+ U.S. workplace incidents across states & machines.
  
- Each record has:
  
- 🗣️ Final Narrative: Free-text injury description

- ⚙️ Cleaned Source: Machine type

- 📌 Event Title: Incident category

- 🎯 Likely Cause: Root cause

- 💥 General Nature: Injury type

- ✋ Body Part: Affected region

- 📍 State & 🗓️ Month

## 🛠️ PREPROCESSING
- Cleaned missing values

- Standardized machine names

- Normalized narrative text for NLP

## 🎯 OBJECTIVES
- 🧾 Track injury trends across machines, states & time

- 🧠 Apply NLP to extract hidden insights from narratives

- 📉 Classify by sentiment (Urgent, Severe, Neutral)

- 🔍 Extract hazard-specific terms using RAKE/TF-IDF

- 📊 Create an interactive Power BI dashboard

- 🧪 Validate insights with SQL-based EDA

- 🧬 Bridge narrative + structured data for complete safety intelligence

## ❓ CRITICAL QUESTIONS ANSWERED

- ⚙️ Which machines cause the most severe hand injuries?

- 🧠 Can text descriptions predict severity or type?

- ✋ Which body parts are most at risk for each machine?

- 🧩 How to improve safety training and inspections using this data?

## 🛠️ METHODS & TOOLS USED

## 💻 Python Libraries
- pandas, spaCy, nltk, TextBlob, matplotlib, seaborn, wordcloud, rake-nltk, scikit-learn

## 🧠 NLP Techniques
- Sentiment with TextBlob

- Keyword extraction: RAKE & TF-IDF

- spaCy for tokenization, lemmatization, NER

## 🗄️ Data Exploration
- Structured EDA using SQLite

- Aggregation across machine types, causes, and body parts

- Data fusion with pandas

## 📊 Visualization
- Power BI Dashboard with:
  
- KPI cards
  
- Stacked bar charts
  
- Decomposition trees

- State-level filtering

## 🧭 RECOMMENDATIONS

- 🔧 Prioritize safety for high-risk machines (e.g., Saws, Presses)

- 🚨 Use sentiment flags for real-time urgency detection

- 🧾 Add risk keywords to inspection checklists

- 📍 Focus programs in Texas, Ohio with high incident rates

- 🌐 Use this model in real-time dashboards for early alerts

