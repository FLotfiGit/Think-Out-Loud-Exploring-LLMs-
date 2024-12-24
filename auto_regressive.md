## 📌 What We Are Talking About?

Imagine trying to guess what someone will say next. That’s what an autoregressive model does one word at a time, like filling in the blanks of a story. This is how does "autoregressive" work.

#### 🎯 **How Do They Think?**

Autoregressive models predict one token based on the ones before it. It's like assembling a sentence piece by piece:

>> ***P(sentence) = P(w₁) × P(w₂ | w₁) × P(w₃ | w₁, w₂) ...***

But here’s the catch, they don’t look ahead, they’re all about the past. What that is interpreted as ***causality*** in sequence generation.

#### 🎯 **Causality**
Autoregressive models are fundamentally causal, meaning that each token is generated based exclusively on the sequence of tokens that came before it. No cheating by looking ahead—future tokens remain inaccessible during both training and inference. This design ensures that the generation respects the temporal flow of language, where the present depends only on the past.

In practice:
>>* *At any time step t, the model predicts w_t conditioned on the preceding tokens {w_1, w_2, ..., w_{t-1}}.*
>>* *The **future context** {w_{t+1}, w_{t+2}, ... } \) is deliberately ignored, enforcing a strict left-to-right processing paradigm that respects causality.*

#### 🎯 **Encoder-based LLM**
LLMs leverage the **autoregressive method**, where the next token in a sequence is predicted based on all previously generated tokens. This approach enables LLMs to generate text step-by-step, with each token conditioned on the context of prior tokens, allowing coherent and contextually relevant outputs. Actually, the words come from:



>>* ***💥Self** – It refers to the fact that the model relies on its own previous outputs (or previous values in a sequence) to make predictions.*
>>* ***💥Based on dependencies** – Each prediction depends on the values that came before it in the sequence.*


> *Example: The LLM wants to answer this question "What is the capital of France?"*
> <p align="center">
> <img src="Figures/LLM_auto_reg.png" alt="LLM Autoregressive Process" width="600">
> </p>
> The above figure illustrates the autoregressive process step by step:  

>  1. **Step 1**: The input prompt *"What is the capital of France?"* is fed into the LLM, which predicts the first token: **"It"**.  
> >    - Context so far: *"What is the capital of France? It"*.  

>  2. **Step 2**: The model takes the updated context and predicts the next token: **"is"**.  
> >    - Updated context: *"What is the capital of France? It is"*.  

>  3. **Step 3**: With the expanded context, the model generates the next token: **"Paris"**.  
> >    - Final context: *"What is the capital of France? It is Paris"*.

<div style="text-align: center; line-height: 1.8;">
   💥  <strong>Token-by-Token:</strong> Predictions are made one word at a time. <br>
   💥  <strong>Context Matters:</strong> Each prediction uses the original prompt + previous outputs as input.
</div>
