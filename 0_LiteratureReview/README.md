# Literature Review

Approaches or solutions that have been tried before on similar projects.

**Summary of Each Work**:

- **Source 1**: PyTorch Seq2Seq Translation Tutorial (Transformer free)
  - **[PyTorch Seq2Seq Translation Tutorial](https://docs.pytorch.org/tutorials/intermediate/seq2seq_translation_tutorial.html)**
  - **Objective**: Tutorial to teach the fundamentals of Neural Machine Translation (NMT) by building a translation system without using high-level libraries like Hugging Face.
  - **Methods**: It uses a Gated Recurrent Unit (GRU) based Encoder-Decoder architecture with an Attention mechanism. It covers data preprocessing (cleaning, tokenizing), teacher forcing and manual evaluation. **Encoder**: The sentence (one-hot, language 1) goes into an Embedder word by word, which produces a dense vector, which is fed into the GRU together with the previous hidden state. This produces an output and the new hidden state (context). This solves the short memory problem of RNNs. The context of the (original english) sentence then goes to the decoder as hidden state. **Decoder**: The decoder takes the hidden state (context of the sentence) and the previous output of the decoder (the first one will be a Start Token). This output is again embedded, fed into the Decoder GRU, which again produces an output and a new hidden state. But **Bottleneck problem**: Full context of input sentence is in one vector after the Encoder. Solution: Attention. The Decoder has access to every hidden state that the Encoder produced.
  - **Outcomes**: A functional model that can translate short sentences. Because it is an RNN-based model, it is naturally very small and comp. efficient for mobile CPUs compared to large Transformers.
  - **Relation to the Project**: This is a learning baseline. We could use this structure to experiment with Hyperparameter Search (e.g. hidden layer sizes, learning rates or the number of GRU layers). The Tutorial shows the example French to English. We could compare that to Portugueese to English. It is interesting to see how well a model without a transformer will perform (allthough RNNs are probably outdated nowadays)

- **Source 2**: Educational Project on Protuese-to-English using Transformer

  - **[Portugues-to-English Transformers (GitHub)](https://github.com/MohsenEbadpour/Neural-Machine-Translation-using-Transformers-on-Portuguese-to-English-)**
  - **Objective**: Focuses on implementing a Transformer architecture for Portuese-to-English translation using the TED Talk dataset (ted_hrlr_translate/pt_to_en) (Tensor flow datasets).
  - **Methods**: Implements a modern Transformer using Keras/TensorFlow. It includes Multi-Head Attention and uses visualization heatmaps to analyze how the model "attends" to specific Portuguese words when translating to English.
  - **Outcomes**: Demonstration of how a Transformer outperforms RNNs on the Port. language pair.
  - **Relation to the Project**: This is a Krease implementation of something we will likely do in PyTorch for comparison of Transformers to the previous architecture.

- **Source 3**: GPorTuguese-2 (Fine-tuning GPT-2 for Portuguese)

  - **[GPorTuguese-2](https://github.com/piegu/fastai-projects/blob/master/finetuning-English-GPT2-any-language-Portuguese-HuggingFace-fastaiv2.ipynb)**
  - **Objective**: Show how an English-centric model (GPT-2) can be fine-tuned to understand and generate Portuguese text using a limited dataset.
  - **Methods**: Transfer Learning (hugging face transformers and fastai libs). It adapts the pretrained English weights to the Portuguese vocabulary through a specific localization pipeline.
  - **Outcomes**: Produced model is capable of generating Port. text, which can be adapted for translation tasks.
  - **Relation to the Project**: This could be a presentation of how to apply finetuning. 


- **Source 4**: A Performance Evaluation of a Quantized Large Language Model on Various Smartphones

  - **[arxiv](https://arxiv.org/html/2312.12472v1)**
  - **Objective**: Evaluate inference performance of a quantized LLM across several iphone models
  - **Methods**: Benchmark sampling, prompt decoding, and token generation rates using a standardized prompt across different smartphones and quantization levels.
  - **Outcomes**: "recent iPhone generations possess the hardware capacity to run on-device LLMs, achieving sustained performance requires further advancements in power management and system integration"
  - **Relation to the Project**: The paper used a quantized 7B model somewhat successfully which gives us an upper limit for our older phone models 

- **Source 5**: Challenging GPU Dominance: When CPUs Outperform for On-Device LLM Inference

  - **[arxiv](https://arxiv.org/pdf/2505.06461)**
  - **Objective**: Test the common assumption that GPU/Metal inference is always faster than CPU on mobile devices.
  - **Methods**: Deploy models from 0.5B to 8B parameters via llama.cpp on an iPhone 15 Pro under varying precision and hardware configurations.
  - **Outcomes**: For sub-1B models, multi-threaded CPU inference achieves up to 1.33× speedup over GPU; realized 17 tok/s on a 1B model
  - **Relation to the Project**: Since 10-20 tok/s seem fast enough for translation tasks this paper gives us an idea about realistic model sizes

- **Source 6**: Misc

  - **[Awesome Mobile LLMs](https://github.com/stevelaskaridis/awesome-mobile-llm)**
  - Curated index of academic papers, frameworks, and tools for running LLMs on mobile and edge devices