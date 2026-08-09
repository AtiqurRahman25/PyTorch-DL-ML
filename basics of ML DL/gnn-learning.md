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


