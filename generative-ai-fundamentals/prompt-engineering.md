# Prompt Engineering & Context Management

Techniques to optimize interactions with Large Language Models (LLMs) to ensure accurate, grounded, and structured outputs.

## 1. Prompting Frameworks

| Technique | Description | Example Structure |
|---|---|---|
| **Zero-Shot Prompting** | Giving the LLM a task without any examples. | "Classify the sentiment of: 'I love this!'" |
| **Few-Shot Prompting** | Providing 2-5 examples to establish tone, format, and pattern. | "Positive: 'Great job.' Negative: 'This is awful.' Classify: 'Not bad.'" |
| **Chain of Thought (CoT)** | Forcing the model to explicitly write out its reasoning steps before answering. | "Think step-by-step. First, calculate X. Then, solve Y..." |
| **ReAct (Reason + Act)** | Model interleaves reasoning traces with actions (e.g., API calls, searches) to solve complex tasks. | "Thought: I need to find the CEO. Action: Search[CEO of company]." |

## 2. Anatomy of a Robust System Prompt

A strong system prompt generally contains:
1.  **Persona/Role:** "You are an expert Python data scientist."
2.  **Task Definition:** "Analyze the provided log data."
3.  **Constraints/Guardrails:** "Do not output Markdown. Only output valid JSON. Never hallucinate API endpoints."
4.  **Formatting Rules:** "Use the following Pydantic schema..."

## 3. Dealing with Context Limits

*   **Lost in the Middle:** LLMs tend to recall information at the beginning and end of a context window better than the middle. Place critical instructions at the very end of the prompt.
*   **Context Window Optimization:** Use Markdown headers to clearly separate instructions from user data (e.g., `### INSTRUCTIONS ###`, `### USER DATA ###`).


*©️ Created by Wecncode Developer Community!*
