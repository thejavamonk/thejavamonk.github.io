---
layout: post
title:  "Improving mathematical reasoning using multi-agent collaboration"
date:   2025-02-01 17:48:44 +0530
categories: project
featured_image: "/images/math-chat.png"
---

A research paper exploring how LLM agent architectures — including Reflection, Reflexion, and Multi-Agent Collaboration — can enhance the mathematical reasoning capabilities of Large Language Models. This work was published as a journal paper — *"A Study on Improving Mathematical Reasoning using Multi-Agent Collaboration"*.

### Abstract

Interactive question-answering with human tutors is a proven method for teaching mathematics. Large language models (LLMs) have the potential to automate parts of this process, including interactive discussions. Though LLMs have demonstrated significant potential, they are limited by problems such as hallucination, outdated knowledge, knowledge gaps, and insufficient training data. LLM Agents with Tools can enhance LLM responses by incorporating verified external knowledge into the model's prompts, and tools can be used to verify thoughts and solve this issue. In this paper, we designed experiments on mathematical reasoning using LLM Agent architectures integrated with tools on a sample of 700 questions from MATH and 1,319 questions from the GSM8K test datasets. We determine the base performance of GPT-4o-mini using zero-shot and evaluate the efficacy of different LLM agent architectures like Reflection, Reflexion, and Multi-agent collaboration implemented using LangGraph. We demonstrate that multi-agent collaboration can improve response accuracy and reduce hallucinations.

### Datasets & Model

- **GSM8K** — 8,792 human-written elementary school math word problems (7,473 training / 1,319 test). Each requires 2–8 steps using basic arithmetic, with solutions in plain language. ([GitHub](https://github.com/openai/grade-school-math))
- **MATH** — 5,000 problems across seven subjects (Pre-calculus, Pre-algebra, Algebra, Geometry, Intermediate Algebra, Probability, Number Theory) and five difficulty levels. We selected 700 level-5 problems due to their complexity — even college students could struggle with half of them.
- **Model** — GPT-4o-mini accessed via OpenAI's API and LangChain.

### Tools & Frameworks

- **LangGraph** — A flexible framework for building complex multi-agent systems with graph-based workflows where nodes represent agents or processes and edges specify information flow. Supports multi-agent orchestration, tool integration, reflection/feedback loops, and human-in-the-loop.
- **E2B Code Interpreter** — A sandboxed environment for executing, modifying, and analyzing code in real-time with persistent state between runs — essential for iterative debugging and experimentation.

### Experiments

**Experiment 1: Baseline Performance** — Assess GPT-4o-mini's performance by prompting each question exactly once using a few-shot derived prompt: *"Solve the problem carefully. Enclose the final answer in \\boxed{}."*

**Experiment 2: Program-of-Thought** — A LangGraph agent integrated with an E2B code interpreter to execute generated code in a sandboxed environment using the Program-of-Thought prompt.

**Experiment 3: Self-Reflection** — A generator agent attempts to solve the problem; a reflector agent (role-playing as a teacher) provides constructive criticism. The loop proceeds up to 3 iterations.

**Experiment 4: Reflexion** — The generator writes a program to solve the problem. The reflector critiques the response using feedback from executing the program in the E2B interpreter, providing detailed comments on missing aspects.

**Experiment 5: Multi-Agent Collaboration** — Specialized Researcher and Programmer agents collaborate through conversation to solve the problem. After *n* rounds of discussion, the final output is generated using the accumulated conversational data.

### Results — GSM8K

| Experiment | Accuracy |
|---|---|
| Baseline Performance | **69%** |
| Self-Reflection | **84%** |
| Program-of-Thought | **90%** |
| Reflexion | **91%** |
| Multi-Agent Collaboration | **93%** |

Multi-agent collaboration improves accuracy by 2% over Reflexion on GSM8K. The increase is attributed to the relatively simple nature of GSM8K word problems involving basic arithmetic.

### Results — MATH (Level-5)

| Experiment | Accuracy |
|---|---|
| Baseline Performance | **28.6%** |
| Program-of-Thought | **37.6%** |
| Multi-Agent Collaboration | **44.7%** |

On the more challenging MATH dataset, multi-agent collaboration improves total accuracy by another 6% over Program-of-Thought, showing consistent performance across all problem categories. The improvement is particularly pronounced in subjects requiring extensive formal numerical calculations (Counting & Probability, Number Theory) and more abstract subjects (Intermediate Algebra, Precalculus).

### Key Findings

- **Tool-augmented agents significantly outperform vanilla prompting** — Using a Python interpreter as a tool provides concrete feedback that helps agents self-correct.
- **Multi-agent collaboration yields the best results** — 93% on GSM8K and 44.7% on MATH level-5, representing a 6% overall improvement on MATH.
- **Code execution as feedback is critical** — Agent performance improves significantly when it receives feedback by executing generated code solutions.
- **Effect varies by problem complexity** — Tool-augmented models show more pronounced improvement on straightforward problems (GSM8K) than on complex mathematical problems (MATH).
- **Program-of-Thought is particularly effective for numerical subjects** — Accuracy gains are strongest in Counting & Probability, Number Theory, Intermediate Algebra, and Precalculus.

### Future Work

- Integrating tools like Wolfram Alpha, Z3, and SAT solvers for advanced logical reasoning, and OMCS knowledge bases for commonsense understanding.
- Studies with more advanced agent architectures.
- Developing advanced planners capable of dynamically tailoring tool selection to each problem's unique requirements.

### Paper

You can read the full paper here: [A Study on Improving Mathematical Reasoning using Multi-Agent Collaboration (PDF)](/resources/papers/math-agent-collaboration.pdf)


