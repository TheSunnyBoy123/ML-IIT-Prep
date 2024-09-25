# [LORA Paper](https://arxiv.org/pdf/2106.09685v2)

## Introduction
Fine tuning used for adapting model for specific application.  
Too many parameters in large models:  
- Possible to use external modules  
    - Store, load and train task-specific parameters
    - Boosts operational efficiency
    - Introduces inference latency due to:
        - Model depth extension
        - Model's usable sequence length reduced

## Terminologies and Convention
$d_{model}$: Input/Output Dimension of Transformer layer  
$W_{q}$: Query Matrix  
$W_{k}$: Key Matrix  
$W_{v}$: Value Matrix  
$W_{o}$: Output Matrix  
$W_{0}/W$: Pre-trained Matrix  
$\Delta W$: Gradient Update  
$r$: Rank of LoRA Module

## Key Ideas

1. **Low-Rank Hypothesis**: LoRA optimizes matrices which need to be re-evaluated instead of the full weight matrix.
   
2. **LoRA Design**:
    - In Transformer architectures, many operations involve matrix multiplication with weight matrices.
    - LoRA assumes that during task adaptation, the required updates to weight matrices are of lower rank than the full pre-trained matrix.
    - For a pre-trained matrix $W_0 \in R^{d\times k}$, the update matrix $\Delta W$ is decomposed as $\Delta W = BA$, where $B \in \mathbb{R}^{d \times r},$ $A \in \mathbb{R}^{r \times k}$.

3. **Advantages**:
   - **Lower Inference Latency**: After adaptation, the matrices can be merged into the original weights, resulting in lower additional inference latency compared to fully fine-tuned models.
   - **Efficiency**: LoRA significantly reduces hardware and computational requirements during training.
   - **Task-Specific Adaptation**: The method enables efficient adaptation to multiple tasks by swapping out the low-rank matrices for different tasks without modifying the core model.

## Application

LoRA can be applied to any dense layer in a neural network, the paper focuses on the application on the self-attention layer.

[Additional Material for attention layers in LLM](https://medium.com/@geetkal67/attention-networks-a-simple-way-to-understand-self-attention-f5fb363c736d)

### 4.1 Targeting Layers
In transformer layers, LoRA modifies the following weight matrices:
- Query matrix
- Key matrix
- Value matrix
- Output matrix

The selective application reduces the number of parameters to be updated.

### 4.2 Rank Selection
The rank $r$ is an important hyperparameter for LoRA, which controls the trade-off between efficiency and performance. The paper suggests $r = 1,2$ is sufficient for most use cases.

---
# [QLora Implementation](https://github.com/TheSunnyBoy123/Peshwas_Do_I_Know_You)
---


# [RAG Paper](https://arxiv.org/pdf/2005.11401v4)



