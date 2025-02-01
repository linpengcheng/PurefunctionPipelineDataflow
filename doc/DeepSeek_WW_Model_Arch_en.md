# DeepSeek's Warehouse/Workshop Modeling Architecture

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
- Feedforward Neural Networks
- Optimizer
- Resource monitoring
- Fault Tolerant Processing
  
