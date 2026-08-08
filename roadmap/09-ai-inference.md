# DreamRun Roadmap — Weeks 55-59

## Week 55 — Math refresh, linear layers, MLP and training basics
**Phase:** AI Fundamentals & Inference Systems  
**Dates:** 2027-08-23 to 2027-08-29  
**Read:** Dive into Deep Learning: linear algebra/calculus refresh, linear regression, MLP chapters. MTech notes only as secondary reference.  
**Build / break / measure:** Implement matrix ops with NumPy, then tiny MLP forward pass. Train tiny model in PyTorch for reference; manually inspect tensor shapes.  
**Mastery gate:** Explain matrix multiply shapes, activation, loss, train/inference distinction and forward-pass computation without ML buzzwords.  
**DSA:** Company-style mixed set  
**Video A:** Neural Networks Explained to a C++ Systems Engineer  
**Video B:** I Built an MLP Forward Pass Without Hiding the Math

## Week 56 — Backpropagation, optimization and numerical precision
**Phase:** AI Fundamentals & Inference Systems  
**Dates:** 2027-08-30 to 2027-09-05  
**Read:** D2L automatic differentiation/backprop/optimization sections. Read FP32/FP16/BF16 concepts from NVIDIA docs where relevant.  
**Build / break / measure:** Derive tiny 2-layer backprop on paper; implement NumPy backprop; compare autograd gradients. Experiment with precision where supported.  
**Mastery gate:** Explain chain rule through tensor shapes, gradients, optimizer role and why reduced precision changes memory/throughput/numerics.  
**DSA:** Company-style mixed set  
**Video A:** Backpropagation Is Just a Computation Graph  
**Video B:** I Wrote Backprop From Scratch and Checked Every Gradient

## Week 57 — Transformers, attention, embeddings and tensor flow
**Phase:** AI Fundamentals & Inference Systems  
**Dates:** 2027-09-06 to 2027-09-12  
**Read:** D2L attention/transformer chapters. Original Transformer paper selectively for architecture, not memorization.  
**Build / break / measure:** Implement scaled dot-product attention in NumPy/PyTorch; inspect Q/K/V shapes, masking and multi-head reshape. Trace one toy sequence.  
**Mastery gate:** Explain attention mathematically enough to derive shapes and complexity; embeddings, residuals, normalization and MLP block roles.  
**DSA:** Google-style coding set  
**Video A:** Transformers Explained From Tensors, Memory and Compute  
**Video B:** I Implemented Attention From Scratch — Q, K, V Included

## Week 58 — Inference lifecycle: prefill/decode, KV cache, batching, quantization
**Phase:** AI Fundamentals & Inference Systems  
**Dates:** 2027-09-13 to 2027-09-19  
**Read:** Read inference-serving docs/articles from primary framework vendors as needed; D2L transformer inference concepts; NVIDIA precision/performance docs.  
**Build / break / measure:** Build toy autoregressive decoder or simulation. Implement KV-cache data structure. Compare naive recompute vs cached attention conceptually/with toy workload. Simulate batching latency/throughput.  
**Mastery gate:** Explain prefill vs decode, KV-cache memory growth, batch-size trade-off, quantization concept and latency vs throughput.  
**DSA:** HFT-style C++ coding/data structures  
**Video A:** What Happens When an LLM Generates ONE Token?  
**Video B:** KV Cache: I Removed Repeated Work and Measured the Trade-off

## Week 59 — AI infrastructure/system design: model serving, scheduling and observability
**Phase:** AI Fundamentals & Inference Systems  
**Dates:** 2027-09-20 to 2027-09-26  
**Read:** Use current AI-infrastructure role requirements as checklist. Study model-server architecture concepts: batching, admission control, routing, GPU utilization, memory capacity, retries, rollout.  
**Build / break / measure:** Design model-serving service: API, tokenizer boundary, request queue, batch scheduler, GPU worker, KV memory budget, metrics, overload policy. Run 60-min AI infra design mock.  
**Mastery gate:** Can design an inference service with SLOs, batching, capacity estimates, GPU memory constraints, failure isolation and observability.  
**DSA:** Google-style coding set  
**Video A:** LLM Inference Is a Systems Problem  
**Video B:** Design an AI Inference Service: Staff-Level System Design
