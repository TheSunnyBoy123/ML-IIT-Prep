# [LORA Paper](https://arxiv.org/pdf/2106.09685v2)

## Introduction
Fine tuning used for adapting model for specific application.  
Too many parameters in large models:  
- Possible to use external modules  
    - Store, load and train task-specific parameters
    - Boosts operational efficiency
    - Introduces inference latency due to:
        - Model depth extended
        - Model's usable sequence length reduced
    