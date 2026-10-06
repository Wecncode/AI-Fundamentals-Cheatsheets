# AI Fundamentals & Algorithm Cheatsheets

An open-source repository of cheatsheets, high-yield reference guides covering Data Science, Machine Learning, Deep Learning, and Generative AI. 

These cheatsheets are structured with a focus on rigorous pedagogical methodology, designed to democratize technical education and streamline complex AI concepts into accessible, practical blueprints. The formatting is intentionally minimalist—optimized for plain white backgrounds, high readability, and clean export to PDF guidebooks for technical instruction.

## 📂 Repository Architecture

The repository is modularized by technical domain:

### `/data-science-for-ai/`
*   **Data Preprocessing:** Handling missing data, feature scaling, categorical encoding, and outlier detection.

### `/machine-learning-for-ai/`
*   **Supervised Learning:** Core algorithms (Linear/Logistic Regression, SVMs, Decision Trees, XGBoost), mathematical formulations, and evaluation metrics.
*   **Unsupervised Learning:** Clustering methodologies (K-Means, Hierarchical, DBSCAN) and dimensionality reduction (PCA, t-SNE, UMAP).

### `/deep-learning-for-ai/`
*   **Neural Networks:** Network architectures, backpropagation fundamentals, activation functions, optimizers (SGD, Adam), and regularization strategies.

### `/generative-ai-fundamentals/`
*   **Prompt Engineering:** Zero-shot, few-shot, Chain of Thought (CoT), ReAct frameworks, and system prompt optimization.
*   **RAG Architecture:** End-to-end Retrieval-Augmented Generation pipelines, vector databases (ChromaDB), embedding models, and advanced retrieval logic (hybrid search, re-ranking).
*   **LLM Security:** OWASP Top 10 for LLMs (prompt injection, data poisoning), MITRE ATLAS threat models, and implementation of robust input/output guardrails.

## Design & Usage

This repository serves as a foundational curriculum resource. All markdown files are designed to be framework-agnostic but are highly applicable when building workflows with tools like LangChain, Gemini API, Ollama, and local open-source models. 

To use these files:
1. Clone the repository: `git clone https://github.com/wecncode/ai-fundamentals-cheatsheets.git`
2. Navigate to the desired domain folder.
3. Export the `.md` files to PDF or HTML using your preferred markdown converter (e.g., Pandoc or VS Code extensions) to distribute as clean, distraction-free study guides.

## Contributing

Contributions to expand these guides are welcome. When submitting a Pull Request, please adhere to the existing structural rules:
*   Maintain the structure of the cheatsheets (no heavy graphics, keep formatting clean).
*   Focus on concrete, practical implementations and mathematical accuracy.
*   Ensure any new RAG, LLM, or cybersecurity concepts align with current industry frameworks.
*   Follow the directory architecture strictly.

Review the `CONTRIBUTING.md` file for full workflow rulesets and repository guidelines.

*©️ Created with love by Wecncode Developer Community!* 
