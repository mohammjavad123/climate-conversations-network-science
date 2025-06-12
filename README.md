
# 🌍 Reddit Climate Network Analysis Project

This project performs an in-depth **network science analysis** and **topic modeling** on Reddit comments and submission titles related to climate change. We collected real Reddit data using specific climate-related keywords and analyzed it using both **graph-based community detection** (Louvain) and **semantic-based clustering** (BERTopic), with powerful visualizations and statistical breakdowns.

## 📦 Dataset

- **Source**: Reddit via PRAW (Python Reddit API Wrapper)
- **Keywords used**: `climate`, `melting`, `ice`, `pollution`, `co2`, `oil`, `gasoline`, `electric`, `energy`
- **Data collected**:
    - ~6,300 comments and submission titles
    - Columns: `submission_title`, `comment_body`, `author`, `created_utc`, `keyword`, `subreddit`

## 🧹 Preprocessing

- Removed duplicates
- Filtered out irrelevant or short content
- Cleaned text (punctuation, casing, stopwords)
- Tokenized into words
- Saved cleaned dataset with `clean_text` and `tokens`

## 🔗 Louvain Community Detection (Graph-Based)

**Graph Construction**:
- Built similarity graph using **cosine similarity** of sentence embeddings
- Nodes: Reddit comments or titles
- Edges: Similarity > threshold (e.g., 0.6)

**Community Detection**:
- Applied **Louvain algorithm** using NetworkX
- Assigned each node a `louvain_community` ID

**Visualizations**:
- UMAP/t-SNE projections of communities
- Cluster size distribution
- Label centroids with top keywords (extracted by frequency)
- Sentiment heatmap per community
- Graph metrics: degree distributions for documents and words

## 💬 BERTopic Topic Modeling (Transformer-Based)

**Embedding**:
- Used `all-MiniLM-L6-v2` SentenceTransformer for dense embeddings of `clean_text`

**Topic Modeling**:
- Ran BERTopic on comments and titles
- Reduced to 10–20 topics for interpretability
- Extracted top keywords per topic

**Visualizations**:
- Interactive UMAP plots with topic hover info
- Topic heatmaps
- Word clouds for each topic
- Topic similarity matrices

## 🔁 Louvain vs. BERTopic Comparison

- Matched top 5 Louvain clusters to top 5 BERTopic topics
- Extracted top 5 keywords per cluster/topic
- Compared sentiment distributions side-by-side
- Plotted cluster/topic overlap heatmap

## 📈 Sentiment Analysis

- Used HuggingFace Transformers `pipeline(sentiment-analysis)`
- Applied to comments and titles
- Labeled each row with `sentiment` (POSITIVE / NEGATIVE)

## 📊 Network Graph & Word Co-Occurrence

- Built document-level and word-level co-occurrence graphs
- Calculated degree distribution
- Plotted power-law distributions on log-log scale
- Highlighted hub nodes

## 🧬 Hierarchical Clustering (Optional Step)

- Applied agglomerative clustering to embeddings
- Dendrograms and cluster assignments for both titles and comments

## ☁️ Word Clouds

- Generated word clouds for:
    - Top BERTopic topics
    - Louvain communities
    - Sentiment-filtered content

## 🧠 Technologies Used

- Python, Pandas, NLTK, NetworkX, BERTopic, SentenceTransformers
- Matplotlib, Seaborn, Plotly, Scikit-learn, UMAP
- Reddit API (PRAW)

## 📁 Project Structure

- `reddit_climate_cleaned.csv`: Final cleaned dataset
- `reddit_with_louvain_and_bertopic.csv`: Enriched dataset with topic labels
- `notebooks/`: Code notebooks for clustering, graph building, topic modeling
- `figures/`: Saved plots and graphs

## 🙌 Credits

Project inspired by network science coursework and Reddit NLP use-cases.

Developed by: **Your Name**  
Date: June 2025
