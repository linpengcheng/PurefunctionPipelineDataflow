# DeepSeek's Warehouse/Workshop Model Architecture

Copyright © 2025.02.01 Pengcheng Lin, All rights reserved.

Based on DeepSeek's answer about its architecture, 
let's design DeepSeek's Warehouse/Workshop Model architecture.

## Warehouse

- Storage: task queue, GPU resource pool, input text, context vector, input sequence, target sequence

- Scheduler: Dynamic scheduling based on task demand and resource state, automatic load balancing.

## Workshop

Natural distributed, heterogeneous parallelism, concurrency, asynchronous support. And linear scalability, which is important!

- Input Embedding Layer
- Encoder
- Decoder
- Multi-Head Latent Attention (MLA)
- Feedforward Neural Networks [Mixture-of-Experts（MoE）Architecture]
  - Routing
  - Selection
  - Expert Processing
    - Routed Experts
    - Shared Experts
  - Weighting and Aggregation
- Optimizer
- Resource monitoring
- Fault Tolerant Processing
- Communication
  
## Conclusion

According to DeepSeek's answer, the original DeepSeek's architecture describes a more complex, 
the storage of the big model is an important part, which is ignored and not described, 
the scheduler is mixed in the feed-forward neural network to describe.

The DeepSeek's architecture is very suitable for the “warehouse/workshop model”, 
but the location and role of the storage and the scheduler can be dealt with better, 
they are part of the warehouse, although they have no direct impact on the AI effect of the big model, 
but if we do a good job of functional pipelining and enhance the independence of the workshop, 
the warehouse-centered scheduling, can be a better global optimization 
to improve the efficiency of the utilization of the workshop to enhance the performance. 

![](https://qiniu.meowparty.cn/coder.2023/2025-01-11/Lesson-c017bd061abc5.png)
