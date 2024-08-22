# Today Learning Resources - Day 6 and 7

# Finetuning LLMs:

## Quantization:

Conversion from higher memory format to a lower memory format.

1. Full Precision/ Half Precision
2. Calibration( Squeezing the values from higher format to lower format)
3. Modes of Quantization 
    1. Post Training Quantization
    2. Quantization Aware Training

![Quantization2.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/Quantization2.png)

### How to Perform Quantization:

1. Symmetric Quantization (→ Batch Normalization)
2. Asymmetric  Quantization

**Symmetric uint8 Quantization:** 

Imp 2 parameters: Zero Point (default=0), Scale 

![SymmetricQuantization.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/SymmetricQuantization.png)

![SymmetricQuantization2.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/SymmetricQuantization2.png)

**ASymmetric uint8 Quantization:**

Imp 2 parameters: Zero Point , Scale

![AsymmetricQuantization.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/AsymmetricQuantization.png)

1. **Post Training Quantization (PTQ):** 

![PTQ.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/PTQ.png)

1. Quantization Aware Training (QAT): 

![QAT.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/QAT.png)

For More Information: https://medium.com/@anhtuan_40207/introduction-to-quantization-09a7fb81f9a4

# Fine Tuning LLMs - LORA, QLORA:

## Low-Rank Adoptaion (LORA) of LLMs:

**Training an LLM:**

![TrainingAnLLM.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/TrainingAnLLM.png)

**Full Parameter Fine Tuning [Challenges]:**

1. Update all model Weights (175B)
2. Hardware Resource Constraints (For down tasks such as Model monitoring, Model inferencing, GPU,RAM)

![HowLORAworks.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/HowLORAworks.png)

![HowLORAworks2.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/HowLORAworks2.png)

![EffectOfLORA.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/EffectOfLORA.png)

![lora_diagram.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/lora_diagram.png)

Note: When you should use Higher Rank:  If the model wants to learn Complex things , then you can use higher rank.

**For more information, Read this blog:** https://medium.com/@Shrishml/lora-low-rank-adaptation-from-the-first-principle-7e1adec71541

Summary: All the track weights are decomposed into two smaller matrixes with different different ranks. When you are fine tuning , the first things is that you are really need to set that rank

### QLoRA (Quantized Low-Rank Adaptation):

QLORA is a fairly new approach to fine-tuning large language models (LLMs). It tackles the two major challenges to widespread LLM adoption: computational cost and resource accessibility.

![Qlora.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/Qlora.png)

![Qlora_QuantizeDecomposeMatrix.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/Qlora_QuantizeDecomposeMatrix.png)

# Fine Tuning Model with Parameter-Efficient Transfer Learning for NLP

My Google colab code:  https://colab.research.google.com/drive/1jFT41HftOk6LOhcbi5XbyAaFcu0HFgVp?usp=sharing

![FinetunedSuccesfully.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/FinetunedSuccesfully.png)

![SaveTheModel.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/SaveTheModel.png)

Read this blog also: https://medium.com/@csakash03/fine-tuning-llama-2-llm-on-google-colab-a-step-by-step-guide-cf7bb367e790

# Era of 1-bit LLMS:

Research Paper: https://arxiv.org/pdf/2402.17764

In this work, we introduce a 1-bit LLM variant,
namely **BitNet b1.58**, in which every single parameter (or weight) of the LLM is
**ternary {-1, 0, 1}**. It matches the full-precision (i.e., FP16 or BF16) Transformer
LLM with the same model size and training tokens in terms of both perplexity
and end-task performance, while being significantly more cost-effective in terms
of latency, memory, throughput, and energy consumption. More profoundly, the
1.58-bit LLM defines a new scaling law and recipe for training new generations of
LLMs that are both high-performance and cost-effective.

![BitNet.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/BitNet.png)

Hightlighted Points:

- It provide a Pareto solution to reduce inference cost (latency,
throughput, and energy) of LLMs while maintaining model performance. The new computation
paradigm of BitNet b1.58 calls for actions to design new hardware optimized for 1-bit LLMs.
- The recent LLM models have demonstrated remarkable performance in a wide range of natural
language processing tasks, but their increasing size has posed challenges for deployment and raised
concerns about their environmental and economic impact due to high energy consumption.
- One approach to address these challenges is to use post-training quantization to create low-bit models.
- This technique reduces the precision of
weights and activations, significantly reducing the memory and computational requirements of LLMs.
The trend has been to move from 16 bits to lower bits, such as 4-bit variants.
- Recent work on 1-bit model architectures, such as **BitNet**, presents a promising direction for reducing the cost of LLMs while maintaining their performance. Vanilla LLMs are in 16-bit
floating values (i.e., FP16 or BF16), and the bulk of any LLMs is matrix multiplication. Therefore, the major computation cost comes from the floating-point addition and multiplication operations. In contrast, the matrix multiplication of BitNet only involves integer addition, which saves orders of energy cost for LLMs. As the fundamental limit to compute performance in many chips is power, the energy savings can also be translated into faster computation.
- **About BitNet:  I**ntroduced a significant 1-bit LLM variant called **BitNet b1.58,** where every parameter
is ternary, taking on values of {-1, 0, 1}. They have added an additional value of 0 to the original 1-bit
BitNet, resulting in 1.58 bits in the binary system. BitNet b1.58 retains all the benefits of the original
1-bit BitNet, including its new computation paradigm, which requires almost no multiplication
operations for matrix multiplication and can be highly optimized. Additionally, it has the same energy
consumption as the original 1-bit BitNet and is much more efficient in terms of memory consumption,
throughput and latency compared to FP16 LLM baselines.
- Furthermore, BitNet b1.58 offers two
additional advantages.
    - Firstly, its modeling capability is stronger due to its explicit support for feature
    filtering, made possible by the inclusion of 0 in the model weights, which can significantly improve
    the performance of 1-bit LLMs.
    - Secondly, our experiments show that BitNet b1.58 can match full
    precision (i.e., FP16) baselines in terms of both perplexity and end-task performance, starting from a
    3B size, when using the same configuration (e.g., model size, training tokens, etc.).
- BitNet b1.58 is based on the BitNet architecture, which is a Transformer that replaces **nn.Linear** with
**BitLinear**.
- **Quantization Function:** To constrain the weights to -1, 0, or +1, we adopt an **absmean quantization**
function. It first scales the weight matrix by its average absolute value, and then round each value to
the nearest integer among {-1, 0, +1}:

![QuantizationFunction.png](Today%20Learning%20Resources%20-%20Day%206%20and%207%20970a14c9c2424917a9356638607c2a98/QuantizationFunction.png)

## Fine Tuning using Google Gemma’s Model:

- My Github code: https://github.com/SaiKumarSeela/FineTuning-LLMs/tree/main/FineTune_Gemma_2b

## Building LLM Pipelines with No code:

Go and check VEXT_:  [https://app.vextapp.com/](https://app.vextapp.com/)

Steps:

1. Login with your credentials
2. Click on Create a project 
3. Add data set through platform by uploading files
4. Select any specific LLM model , and write how it should behave and save
5. Experiment with playground
6. Create an API Key , and Write the simple python code to access this LLM pipeline by providing API key, and the URL which they specify

## Fine Tuning with own custom data:

Gradient: https://gradient.ai/

**Fine-tune Gemma models With Custom Data:**

Kaggle-Gemma :   https://kaggle.com/models/google/gemma

 Watch this tutorial : https://www.youtube.com/watch?v=IZXNgu4dW70&list=PLZoTAELRMXVN9VbAx5I2VvloTtYmlApe3&index=6

My github repo: https://github.com/SaiKumarSeela/FineTuning-LLMs/tree/main/Finetune_Gemma_WithCustomData