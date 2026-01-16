Authored by Sahil Bhatia. You can follow him on [LinkedIn](www.linkedin.com/in/sahilbhatiaiitbhu) for the latest LLM, RAG and Agent updates
Repo: https://github.com/sahil-bhatia-iitbhu/AI-Interview-Questions

### 🚀 INTERVIEW - Model Quantization Decoded: Speed, Memory & Accuracy Trade-offs

**INTERVIEWER:** You work heavily with LLMs—walk us through quantization. Why are engineers obsessed with it right now?

**CANDIDATE:** Quantization is essentially precision reduction. We shrink model weights from 32-bit floating-point (FP32) down to 8-bit or even 4-bit integers, using a smaller numerical alphabet to represent values.

**INTERVIEWER:** And the payoff?

**CANDIDATE:** The payoff is huge in infrastructure savings. A 4-bit quantized LLM can cut memory by more than half and significantly reduce bandwidth requirements, because each parameter now uses far fewer bits.
On modern hardware, this often translates into 2–4× faster inference throughput, especially when kernels and hardware are optimized for low-precision math.

**INTERVIEWER:** But surely compressing to 1/8th precision destroys model quality?

**CANDIDATE:** Surprisingly, it usually doesn’t. Neural networks have a lot of redundancy, and many weights can be represented with lower precision without changing the model’s overall behavior much.
With good calibration and quantization schemes, many models retain over 95% of their original accuracy at 8-bit and even 4-bit precision, especially for classification and typical NLP tasks.

**INTERVIEWER:** So how do you actually do this without losing quality?

**CANDIDATE:** There are two main approaches. Post-training quantization (PTQ) takes a trained model and quantizes it afterwards using a small calibration set, making it fast to apply but sometimes causing a small accuracy drop.
Quantization-aware training (QAT) simulates quantization during training so the model learns to be robust to low precision, often matching FP32 accuracy even at INT8 by the time training finishes. 

**INTERVIEWER:** Which do you use in production?

**CANDIDATE:** For many inference-only workloads like recommendation or general LLM serving, PTQ is attractive because it’s quick and cheap to deploy.
For safety- or accuracy-critical applications—medical imaging, autonomous systems, or high-stakes financial models—QAT or carefully tuned mixed-precision quantization is preferred to keep accuracy loss minimal.

**INTERVIEWER:** Real talk—any gotchas?

**CANDIDATE:** Going too low, like sub-4-bit, can hurt quality unless you combine it with advanced techniques such as per-channel scales, group-wise quantization, or special training tricks.
Transformer attention and some normalization layers can be particularly sensitive, so they are often kept at higher precision or quantized with more careful schemes.

**INTERVIEWER:** Final question—what’s the trend?

**CANDIDATE:** Quantization is a standard for deploying large models efficiently, especially LLMs on cloud and edge hardware.
The direction is toward more aggressive but smarter quantization—mixed precision, 4-bit and below, and specialized algorithms—so that powerful models can run on cheaper GPUs and even consumer device.

**#LLMOptimization #ModelQuantization #AIInference #DeepLearning #EdgeAI #QuantizationAwareTraining #MLEngineering #ProductionAI #AIEfficiency #MachineLearning #LLMs**
