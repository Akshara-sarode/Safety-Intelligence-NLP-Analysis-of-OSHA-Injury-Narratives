# Safety-Intelligence-NLP-Analysis-of-OSHA-Injury-Narratives
This project uses NLP to analyze OSHA-style injury narratives, extracting sentiment and keywords to identify machine-specific risks. A Power BI dashboard visualizes key patterns in injury severity, causes, and body parts, enabling data-driven workplace safety insights.


# PROJECT OVERVIEW

This project implements a data-driven safety analytics dashboard leveraging Natural Language Processing (NLP), SQL-based data exploration, and business intelligence visualization. Centered on OSHA-style hand injury reports, the workflow includes sentiment analysis using TextBlob, keyword extraction via RAKE and TF-IDF, and structured querying in SQLite. Narrative data is classified by polarity to capture urgency and severity, while machine-specific risk terms are extracted to support root cause analysis. The results are integrated into an interactive Power BI dashboard, offering multi-dimensional filtering, decomposition trees, and visual KPIs to support predictive safety management and informed decision-making.

# KEY OUTCOMES:

- Identified high-risk machines such as Machine Saw and Hydraulic Press based on incident frequency and narrative severity.

- Applied sentiment analysis to classify over 20,000 injury narratives into categories: Urgent, Severe, and Confusing/Neutral.

- Extracted machine-specific risk keywords using both RAKE and TF-IDF, enabling granular hazard profiling.

- Mapped injury trends across states and time, revealing peak risk periods and regional safety gaps.

- Combined unstructured narrative data with structured metadata to build a comprehensive safety intelligence layer.

- Developed an interactive Power BI dashboard integrating NLP insights, EDA results, KPI tracking, and drill-downs for real-time decision-making.

- Enabled data-backed recommendations for training, inspection prioritization, and policy revision.


# DATASET INFORMATION:

# SOURCE:
- Internal OSHA records and Hand Injuries with Machines dataset

# DESCRIPTION:
  The dataset includes narrative descriptions of workplace injuries, especially hand injuries related to equipment. Each record typically contains:
  
- Final Narrative: Free-text description of how the injury occurred

- Cleaned Source: Type of machine involved (e.g., Machine Saw, Hydraulic Press)

- Event Title: Coded category of incident cause (e.g., Caught in equipment, Overexertion)

- Likely Cause: Root cause or trigger leading to the injury

- General Nature: Nature of the injury (e.g., Laceration, Fracture, Burn)

- General Part of Body: Body region affected (e.g., Upper Extremities, Hand)

- State: Location where the injury occurred

- Month: Month in which the injury was reported

# RECORD COUNT:
- ~20,000 injury incidents across multiple U.S. states and machine types.

# PREPROCESSING:

- Null values removed from critical columns (Final Narrative, Cleaned Source)

- Narrative column normalized for NLP

- Machine names standardized into Cleaned Source


# OBJECTIVES:

- Analyze injury trends across machines, body parts, states, and time to uncover patterns in workplace safety incidents.

- Leverage Natural Language Processing (NLP) techniques to process and extract insights from unstructured injury narratives.

- Classify narratives by sentiment (e.g., Severe, Urgent, Neutral) using polarity-based scoring to assess narrative tone and urgency.

- Extract key risk terms per machine using keyword extraction methods like RAKE and TF-IDF for hazard profiling.

- Develop an interactive Power BI dashboard to enable real-time, multi-filtered visualizations of safety metrics.

- Perform SQL-based exploratory data analysis (EDA) to validate hypotheses and identify high-risk patterns in structured fields.

- Bridge structured and unstructured data to form a unified view of occupational safety intelligence.

# ANSWER CRITICAL SAFETY QUESTIONS:
- Which machines are linked to the most severe hand injuries?

- Can narrative descriptions predict the type or severity of injuries?

- Which body parts are most vulnerable for each machine type?

- Support data-driven decision-making by delivering insights for training focus, inspection planning, and policy refinement.


# METHODS & TOOLS USED:

# PYTHON LIBRARIES:
pandas, spaCy, nltk, TextBlob, matplotlib, seaborn, wordcloud, rake-nltk, scikit-learn

# NLP TECHNIQUES:

- Sentiment analysis using TextBlob for polarity classification

- Keyword extraction using RAKE and TF-IDF (via rake-nltk and TfidfVectorizer)

- spaCy-based preprocessing: tokenization, lemmatization, stopword filtering

- Optional Named Entity Recognition (NER) and pattern matching using spaCy pipelines

# DATA EXPLORATION & MODELLING:

- SQL-based EDA using SQLite

- Aggregation and pattern mining across machines, causes, and body parts

- Structured + unstructured data fusion using pandas

# VISUALIZATION:

- Power BI Dashboard with KPI cards, stacked bar charts, and decomposition trees. 



# RECOMMENDATIONS:

- Prioritize safety protocols for machines with the highest frequency and severity scores, such as Machine Saws and Hydraulic Presses.

- Use narrative-based sentiment scoring to flag potentially underreported or urgent cases in real-time systems.

- Integrate RAKE-extracted keywords into machine maintenance and inspection checklists to address recurring risks.

- Focus state-level safety programs in regions like Texas and Ohio, which report the highest incidents.

- Incorporate this analysis framework into real-time incident tracking dashboards for early warning and preventive actions.
