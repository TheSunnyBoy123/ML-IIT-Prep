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

LoRA decomposes parameter matrices to a very low rank for fine tuning giving  
1. Storage Efficiency
2. Computational Efficiency (~12k rank decomposed to 1-2 rank for GPT3)  

### Terminologies and Conventions
---
 
