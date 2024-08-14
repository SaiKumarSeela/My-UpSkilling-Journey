# Today Learning Resourses - Day 2

## Prompt Engineering:

Resources: https://www.promptingguide.ai/techniques/

Vamsi Bhavani Playlist: https://www.youtube.com/watch?v=UPkIiUb-QKY&list=PLNgoFk5SYUgnte6sqbwyeKAMfvhqLcnkv

### Techniques:

- **Zero-shot Prompting:** Zero-shot prompting means that the prompt used to interact with the model won't contain examples or demonstrations.
- **One-shot prompting:** One-shot prompting is used to generate natural language text with a limited amount of input data such as a single example or template.
- **Few-shot prompting** can be used as a technique to enable in-context learning where we provide demonstrations in the prompt to steer the model to better performance. Standard few-shot prompting works well for many tasks but is still **not a perfect** technique, especially when dealing with more complex **reasoning tasks.**
- **Chain-of-Thought (COT) Prompting:** It enables complex reasoning capabilities through intermediate reasoning steps. You can combine it with few-shot prompting to get better results on more complex tasks that require reasoning before responding.
- **Zero-shot COT Prompting:** One recent idea that came out more recently is the idea of  zero-shot CoT that essentially involves adding **"Let's think step by step"** to the original prompt.
- **Automatic Chain-of-Thought (Auto-CoT):** Auto-CoT consists of two main stages: Stage 1): **question clustering**: partition questions of a given dataset into a few clusters.  Stage 2): **demonstration sampling**: select a representative question from each cluster and generate its reasoning chain using Zero-Shot-CoT with simple heuristics
- **Self-Consistency:** The idea is to sample multiple, diverse reasoning paths through few-shot CoT, and use the generations to **select the most consistent answer**.
- **Generated Knowledge Prompting:**  The limitations of LLMs to perform tasks that require more knowledge about the world. How do we improve this with knowledge generation? First, we generate a few "knowledges": Example: “”” Input: Greece is larger than mexico.
Knowledge: Greece is approximately 131,957 sq km, while Mexico is approximately 1,964,375 sq km, making Mexico 1,389% larger than Greece.
Input: Part of golf is trying to get a higher point total than others.
Knowledge:  “””
- **Prompt chaining:**  It ****is useful to accomplish complex tasks which an LLM might struggle to address if prompted with a very detailed prompt. In prompt chaining, chain prompts perform transformations or additional processes on the generated responses before reaching a final desired state.
- **Tree of Thoughts (ToT):** ToT maintains a tree of thoughts, where thoughts represent coherent language sequences that serve as intermediate steps toward solving a problem.
- **Role Prompting:** Another prompting technique is to assign a role to the AI. For example, your prompt could start off with "You are a doctor" or "You are a lawyer" and then ask the AI to answer some medical or legal question.

### Retrieval Augmented Generation (RAG):

RAG allows language models to bypass retraining, enabling access to the latest information for generating reliable outputs via retrieval-based generation.

![RagWorkflow.png](Today%20Learning%20Resourses%20-%20Day%202%203e84ec77d81d4e36a91fbfb43ccad1c1/RagWorkflow.png)

Credit: [https://medium.com/@unstructured-io](https://medium.com/@unstructured-io)

**Learn more here :** https://towardsdatascience.com/retrieval-augmented-generation-rag-from-theory-to-langchain-implementation-4e9bd5f6a4f2

**RAG WorkFlow**: https://ai.meta.com/blog/retrieval-augmented-generation-streamlining-the-creation-of-intelligent-natural-language-processing-models/

[119418143_276670007003484_4437323492839372115_n.mp4](Today%20Learning%20Resourses%20-%20Day%202%203e84ec77d81d4e36a91fbfb43ccad1c1/119418143_276670007003484_4437323492839372115_n.mp4)

- **Automatic Reasoning and Tool-use (ART):** ART works as follows:
    - given a new task, it select demonstrations of multi-step reasoning and tool use from a task library.
    - at test time, it pauses generation whenever external tools are called, and integrate their output before resuming generation
- **Automatic Prompt Engineer (APE):** The first step involves a large language model (as an inference model) that is given output demonstrations to generate instruction candidates for a task. These candidate solutions will guide the search procedure. The instructions are executed using a target model, and then the most appropriate instruction is selected based on computed evaluation scores. The prompt "Let's work this out in a step by step way to be sure we have the right answer."  elicits chain-of-thought reasoning and improves performance on the MultiArith and GSM8K benchmarks.
- **Active Prompt:**  The problem with COT is that the exemplars might not be the most effective examples for the different tasks.  The first step is to query the LLM with or without a few CoT examples. *k* possible answers are generated for a set of training questions. An uncertainty metric is calculated based on the *k* answers (disagreement used). The most uncertain questions are selected for annotation by humans. The new annotated exemplars are then used to infer each question.

### **ReAct Prompting:**

- ReAct is a general paradigm that combines reasoning and acting with LLMs. ReAct prompts LLMs to generate verbal reasoning traces and actions for a task.
- This allows the system to perform dynamic reasoning to create, maintain, and adjust plans for acting while also enabling interaction to external environments (e.g., Wikipedia) to incorporate additional information into the reasoning.
- The first step is to select cases from a training set (e.g., HotPotQA) and compose ReAct-format trajectories. These are used as few-shot exemplars in the prompts. The trajectories consist of **multiple thought-action-observation steps**.
- The free-form thoughts are used to achieve different tasks such as decomposing questions, extracting information, performing commonsense/arithmetic reasoning, guide search formulation, and synthesizing final answer.

![ReActPrompting.png](Today%20Learning%20Resourses%20-%20Day%202%203e84ec77d81d4e36a91fbfb43ccad1c1/ReActPrompting.png)

- **Reflexion:  T**he key steps of the Reflexion process are a) define a task, b) generate a trajectory, c) evaluate, d) perform reflection, and e) generate the next trajectory.
- **Multimodal CoT Prompting:** Traditional CoT focuses on the language modality. In contrast, Multimodal CoT incorporates text and vision into a two-stage framework. The first step involves rationale generation based on multimodal information. This is followed by the second phase, answer inference, which leverages the informative generated rationales.

## Youtube Summarizer Discord Bot using Ollama:

- Watch this video: https://www.youtube.com/watch?v=wU4R9Lj-Mqs&list=PLIkXejH7XPT8x9iUGvlsYt44aPx6ns8BV
- tiktoken library: https://github.com/openai/tiktoken
- OpenAI Prompt engineering best practises: https://platform.openai.com/docs/guides/prompt-engineering/six-strategies-for-getting-better-results