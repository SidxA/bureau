https://kubernetes.io/
https://www.reddit.com/r/LocalLLaMA/comments/185a3mh/what_kind_of_specs_to_run_local_llm_and_serve_to/
https://www.reddit.com/r/LocalLLaMA/comments/185mu00/llamacpp_on_colab_with_bakllava1q8_0_mistralllava/
https://cloud-gpus.com/

t4 colab can barely run a 7B model on full precision
for a 34b model you need a good a100 80gb or 2 x a6k 48gb

https://github.com/randaller/llama-chat

In terms of model size, bigger model size is always better. This graph shows perplexity for each model. The 65B has the least, the 7b has the most. A 13b q2 has less perplexity than a full, non-quantized, 7b.

https://preview.redd.it/r9gd7dn2ksgb1.png?width=792&format=png&auto=webp&s=b9dce2e22724665754cc94a22442f2795f594345

In terms of quants, someone put out a great comparison of them. Almost all of them performed equally, except for some reason 6_K was garbage... it might be broken, so I just avoid it and get 5_K_Ms instead.

https://www.reddit.com/r/LocalLLaMA/comments/16gmfwd/15_comparisons_with_3bit_4bit_5bit_6bit_and_8bit/

And finally:

GPTQ == runs entirely on your GPU. You need enough VRAM to fit the whole thing or you'll see slowness like you can't imagine. These only come in q8 and q4 flavors, generally

GGUF == can run on both CPU and GPU. I like these the most

Pure GPU gives better inference speed than CPU or CPU with GPU offloading.

Smaller models give better inference speed than larger models.

If speed is all that matters, you run a small model on a GPU. If quality matters, you run a larger model. But you need to put your priorities in order. :-)

24GB VRAM generally allows for 30/34B models at 4bit quantization running on pure GPU. (GPTQ). I like TheBloke_Phind-CodeLlama-34B-v2-GPTQ_gptq-4bit-32g-actorder_True, as it appears to work great for my python coding questions. (As well as general stuff. Running on a 3090.)


I used the original 34B last night with 4 bit through accelerate and I was absolutely blown away. I got goosebumps because it finally felt like we have models we can run on consumer hardware (single 3090 in this case) and did not feel like a toy. I purposely broke some functions, it fixed it. I asked some complex questions and it answered it well. I’m excited for what’s to come. I wish there was a Phind instruct model for me to play with. Text completion hasn’t really been all that useful for my use case.

https://github.com/turboderp/exllamav2 and https://github.com/turboderp/exui

https://github.com/gotzmann/collider

https://arxiv.org/abs/2211.17192