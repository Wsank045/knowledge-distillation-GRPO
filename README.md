# Faithful Reasoning in Small Language Models via DeepSeek Distillation

This project explores how to enhance the **faithfulness** and **logical consistency** of reasoning in **small language models** using **Chain-of-Thought (CoT) fine-tuning** and **synthetic data distillation**. We propose a novel framework to transfer high-quality reasoning skills from the **DeepSeek-R1** model to a **LLaMA-3B-Instruct** model using **LoRA** and **reinforcement learning (GRPO/Unsloth)**.

## 🧠 Project Overview

Large Language Models (LLMs) like GPT-4 can perform step-by-step reasoning when prompted with Chain-of-Thought examples. However, **small models** often struggle to reason accurately and faithfully. This project addresses the problem by:

- Using **DeepSeek-R1** to generate high-fidelity, step-by-step reasoning data.
- Fine-tuning a **LLaMA-3B-Instruct** model with LoRA adapters on this synthetic dataset.
- Applying **Group Reward Policy Optimization (GRPO)** with custom reward functions to reinforce logical consistency.

## 🔍 Motivation

- Existing small models hallucinate or produce flawed rationales.
- Human-annotated CoT datasets are limited and expensive.
- We leverage **synthetic CoT generation** from advanced models like DeepSeek-R1 to overcome data scarcity and improve reasoning reliability.

## 📦 Key Components

### 1. DeepSeek Data Generation
- Prompted DeepSeek-R1 with diverse math and reasoning problems.
- Extracted full step-by-step reasoning and answers.
- Applied a **faithfulness filter** scoring CoTs for logical validity, coherence, and alignment to the question.

### 2. Fine-Tuning with LoRA
- Used the [LoRA](https://arxiv.org/abs/2106.09685) method for efficient parameter tuning.
- Fine-tuned only the adapters for cost-effective training on standard GPUs.

### 3. Reinforcement Fine-Tuning (Unsloth / GRPO)
- Applied **Unsloth**, a lightweight RL fine-tuning library.
- Custom reward functions encouraged **faithful intermediate reasoning**, not just final answer correctness.

## 📊 Evaluation

- **Benchmark**: GSM8K (Grade School Math Word Problems)
- **Metrics**:
  - Final answer accuracy
  - Rationale consistency and faithfulness
- **Findings**:
  - Notable improvement in reasoning accuracy over base LLaMA-3B
  - Better stepwise alignment to the actual problem-solving process

## 🚀 Contributions

- 📁 **Synthetic CoT Dataset**: Curated dataset of high-quality reasoning traces from DeepSeek.
- 🧠 **LoRA Fine-Tuning + RL**: Two-stage training pipeline combining supervised and reward-based learning.
- 🧪 **Faithfulness Evaluation**: Proposed new metrics and benchmark analysis to assess reasoning validity.
- 🔬 **Small Model Insights**: Analysis of how much reasoning skill a small model can acquire with strong supervision.

## 📚 Related Technologies

- [LLaMA 3B Instruct](https://ai.meta.com/llama/)
- [DeepSeek](https://github.com/deepseek-ai)
- [LoRA (Low-Rank Adaptation)](https://arxiv.org/abs/2106.09685)
- [Unsloth (RLHF library)](https://github.com/unslothai/unsloth)
- [GSM8K Benchmark](https://github.com/openai/grade-school-math)

## 🛠 How to Use

> 🚧 This is a research prototype and not a production-ready release.

1. **Clone the repo**  
   ```bash
   git clone https://github.com/your-team/project-repo-name.git
   cd project-repo-name

2. **Instal dependencies**
   Ensure you have a suitable environment (Pyhton 3.10+, PyTorch, Hugging Face Transformers, Unsloth, etc..)
4. **Train the model**
   Fine-tune the model using our training scripts and provided configuration for LoRA +RL
6. **Evaluate the model**
   Use ethe provided evaluation script on GSM8K to compare performance with baseline

## 👥 Team
This project was developed collaboratively as part of a graduate-level research project.
Contributors : Souleymane Wilfried Sankara, Devansh Kumar
