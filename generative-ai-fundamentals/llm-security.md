# LLM Security & Guardrails

Securing Large Language Models requires defending against both traditional software vulnerabilities and novel adversarial AI techniques.

## 1. OWASP Top Vulnerabilities for LLMs

The Open Worldwide Application Security Project (OWASP) identifies the most critical security risks for GenAI applications.

| Vulnerability | Mechanism | Mitigation Strategy |
|---|---|---|
| **Prompt Injection** | Crafting inputs that override the system prompt to execute unauthorized actions (e.g., "Ignore previous instructions and do X"). | Strict system prompts, delimiter separation, and input filtering layers. |
| **Indirect Prompt Injection** | Hiding malicious instructions inside external data (like web pages or PDFs) that the LLM retrieves via RAG. | Treat all retrieved data as untrusted. Parse and sanitize RAG context. |
| **Insecure Output Handling** | Blindly passing LLM output to backend systems or rendering it in a browser, leading to XSS or remote code execution (RCE). | Validate outputs against strict schemas (e.g., Pydantic). Sanitize output before rendering. |
| **Sensitive Info Disclosure** | The model leaking proprietary data, PII, or credentials memorized during training or placed in the context window. | Implement data redaction pipelines (PII masking) before data hits the model. |
| **Training Data Poisoning** | Adversaries manipulating the fine-tuning dataset to introduce backdoors, biases, or specific trigger behaviors. | Cryptographically verify dataset provenance and use anomaly detection on training data. |

## 2. MITRE ATLAS Framework

MITRE ATLAS (Adversarial Threat Landscape for AI Systems) is a knowledge base of adversary tactics and techniques against AI.

*   **Reconnaissance:** Attackers query the model to determine its architecture, training data, or guardrails (e.g., Model Inversion, Prompt Probing).
*   **Initial Access:** Exploiting public-facing inference APIs or compromising the supply chain (e.g., downloading a compromised model from Hugging Face).
*   **ML Attack Staging:** Crafting adversarial inputs or poisoning data specifically designed to fool the target model.
*   **Exfiltration:** Extracting model weights, sensitive RAG documents, or proprietary system prompts via carefully crafted queries.

## 3. Implementing AI Guardrails

Guardrails are programmable constraints that sit between the user, the LLM, and the backend systems to ensure safe and predictable execution.

### Input Guardrails (Protecting the Model)
*   **PII Scrubbing:** Detecting and masking names, emails, and phone numbers before the prompt reaches the LLM.
*   **Topic Restriction:** Using a lightweight classifier to block queries unrelated to the application's domain.
*   **Injection Detection:** Running inputs through a specialized security model (e.g., Llama Guard) to classify intent before processing.

### Output Guardrails (Protecting the User & System)
*   **Format Validation:** Forcing the LLM to output structured data and using parsers (like Pydantic) to drop responses that break the schema.
*   **Toxicity & Bias Filtering:** Evaluating the generated text for hate speech, bias, or harmful advice before displaying it.
*   **Fact-Checking (Self-Correction):** Using a secondary LLM step to verify that the primary model's answer is strictly grounded in the retrieved RAG context.

  
  *©️ Created by Wecncode Developer Community!*
