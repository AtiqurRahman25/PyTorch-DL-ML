# What is a Graph?

A **Graph** is a non-linear data structure used to represent relationships between different objects.

It is made up of two main components:

## 1. Nodes (Vertices)
- Represent the **objects** or **entities** in the graph.
- Also called **vertices**.
- Examples: People in a social network, cities on a map, web pages on the internet.

## 2. Edges
- Represent the **connections** or **relationships** between nodes.
- Edges can be:
  - **Directed (→):** One-way connection.
  - **Undirected (—):** Two-way connection.
  - **Weighted:** Contains a value (cost, distance, time, etc.).
<img width="1920" height="1080" alt="Graphs-in-DSA" src="https://github.com/user-attachments/assets/b1828146-9ada-4d73-9693-39a7f54db5e7" />

# Why Can't Normal Neural Networks Handle This?

Traditional neural networks work well with **structured data**, such as:

- 🖼️ **Images** → Pixels arranged in a fixed grid
- 📝 **Text** → Words arranged in a sequence
- 🎵 **Audio** → Signals ordered over time

However, **graphs are fundamentally different**.

## Example Graph

```text
A ----- B

C ----- D ----- E
```

### Why is this difficult?

Graphs do **not** have a fixed structure:

- Each node can have a **different number of neighbors**.
- There is **no fixed ordering** of the nodes.
- Connections between nodes can vary significantly from one graph to another.

Unlike images or text, graph data cannot be represented as a simple matrix with a consistent layout.

## The Limitation of Traditional Neural Networks

Traditional neural networks expect inputs with a **fixed size and fixed structure**.

For example:

- CNNs assume pixels are arranged in a regular grid.
- RNNs and Transformers assume tokens appear in an ordered sequence.

Graphs violate both of these assumptions, making standard neural networks unsuitable for directly learning from graph data.

## The Solution: Graph Neural Networks (GNNs)

**Graph Neural Networks (GNNs)** are specifically designed to process graph-structured data.

They work by:

- Learning from both **node features** and **graph connectivity**.
- Aggregating information from neighboring nodes.
- Producing representations that capture both local and global graph structure.

> **In short:** Traditional neural networks struggle with irregular graph structures, while **Graph Neural Networks (GNNs)** are built to understand and learn from them.

## Types of Graphs
<img width="1920" height="1080" alt="graphs" src="https://github.com/user-attachments/assets/21390f4f-b4e2-41ca-9fc1-b8936b316a2a" />
<img width="1920" height="1080" alt="images" src="https://github.com/user-attachments/assets/c98b8afa-53e5-4973-9598-e9475d6b376c" />

## Graph Algorithm
<img width="1920" height="1080" alt="images" src="https://github.com/user-attachments/assets/2099dfcb-982f-4588-98fe-8b11d0fc98be" />

# Word2vec: A Guide to Distributed Word Representations

**Word2vec** is a pioneering technique in Natural Language Processing (NLP) used to generate **word embeddings**—dense vector representations of words in a continuous vector space. 

Developed by a team of researchers at Google led by Tomas Mikolov in 2013, Word2vec revolutionized how computers understand human language by capturing the **semantic and syntactic meanings** of words based on their context in text.

---

## 🔑 Key Concepts

* **Vector Representation:** Words are converted into lists of numbers (vectors), typically ranging from 100 to 300 dimensions. 
* **Semantic Proximity:** Words with similar meanings or contexts are mapped close to each other in the vector space (e.g., `"cat"` and `"dog"` have numerically similar vectors).
* **Vector Arithmetic:** One of the most famous features of Word2vec is its ability to capture linear relationships and analogies through vector math:
  > $\text{Vector}(\text{"King"}) - \text{Vector}(\text{"Man"}) + \text{Vector}(\text{"Woman"}) \approx \text{Vector}(\text{"Queen"})$

---

## ⚙️ How Word2vec Works (Architectures)

Word2vec uses shallow, two-layer neural networks to learn word associations from a large corpus of text. It comes in two primary architectures:

1. **Continuous Bag-of-Words (CBOW)**
   * **Goal:** Predict a target word based on its surrounding context words (the context window).
   * **Use case:** Works faster and is slightly better at handling more frequent words.
2. **Skip-gram**
   * **Goal:** Predict the surrounding context words given a target word.
   * **Use case:** Works well with smaller amounts of data and does a better job representing less frequent or rare words.

---

## 🚀 Why Word2vec Was a Breakthrough

* **Contextual Awareness:** Older methods like **One-Hot Encoding** treated words as independent, isolated categories where semantic relationships couldn't be computed. Word2vec solved this by encoding meaning into continuous dimensions.
* **Efficiency:** It significantly reduced computational complexity compared to earlier neural network language models, allowing it to be trained on massive datasets (billions of words).

---

## ⚠️ Limitations

* **Static Embeddings:** Word2vec assigns a single, fixed vector to a word regardless of its context. For example, the word `"bank"` (river bank vs. financial bank) will have the exact same vector, ignoring polysemy. *(Note: This was later solved by contextual models like BERT and GPT).*
* **Out-of-Vocabulary (OOV):** It struggles to generate vectors for words it has never seen during training.

# DeepWalk and Random Walk in Graph Machine Learning

In network analysis and graph machine learning, **Random Walk** is a foundational data-sampling technique, while **DeepWalk** is a specific algorithm that uses random walks to build graph embeddings. 

---

## 1. What is a Random Walk?

A **random walk** is a stochastic (probabilistic) process on a graph where you start at a specific node and randomly move to one of its neighboring nodes. 

* **How it works:** 
  1. Choose a starting node ($u$).
  2. Randomly select one of its neighbors ($v$) based on a transition probability.
  3. Repeat this process from the new node until you hit a pre-defined maximum walk length.
* **Analogy:** Imagine a person wandering randomly through a city's street network, moving from one intersection to an adjacent intersection at random. 
* **Role in Graph Theory:** It simulates local network structures. Nodes that frequently appear together in the same random walks share structural proximity (they belong to the same local community or cluster).

---

## 2. What is DeepWalk?

**DeepWalk** (introduced in 2014) is the pioneering algorithm that bridges graph structures with Natural Language Processing (NLP) by turning random walks into "sentences".

It was built on a brilliant core insight: **the frequency distribution of nodes visited in random walks follows a power-law, mirroring the frequency distribution of words in human languages.**

### The DeepWalk Pipeline:
1. **Generate Random Walks:** For every node in the graph, DeepWalk samples multiple truncated random walks of a fixed length.
2. **Treat Walks as Sentences:** Each sequence of nodes (e.g., Node $\text{A} \rightarrow \text{Node C} \rightarrow \text{Node B}$) is treated like a sentence, and individual nodes are treated like "words".
3. **Train Word2vec (Skip-gram):** It passes these node "sentences" into a Word2vec model (specifically the Skip-gram architecture). 
4. **Output Embeddings:** The model learns a continuous, low-dimensional vector space where nodes that frequently co-occur in random walks are mapped close together.

---

## 📊 Key Differences & Relationship

| Feature | Random Walk | DeepWalk |
| :--- | :--- | :--- |
| **What is it?** | A **sampling strategy/technique** to traverse a graph. | A complete **machine learning algorithm** for generating node embeddings. |
| **Core Function** | Generates sequences of connected nodes. | Takes those sequences, runs them through Word2vec, and outputs dense vector coordinates. |
| **Dependency** | Independent (can be used for search, node ranking like PageRank, or graph visualization). | Dependent (relies strictly on random walks as its foundational data engine). |

---

## 💡 Summary

* **Random Walk** is the *method* of exploring a graph by taking steps from neighbor to neighbor.
* **DeepWalk** is the *framework* that uses Random Walks combined with Word2vec to translate graph topology into machine-learning-ready vectors.
