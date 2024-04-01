aimed at a 3090,4090,t4 level

https://huggingface.co/TheBloke/OpenHermes-2.5-neural-chat-7B-v3-1-7B-GGUF

open hermes 7b function calling
https://www.reddit.com/r/LocalLLaMA/comments/185fksv/forget_openai_function_calling_openhermes_outlines/

https://github.com/arthurwolf/llmi/blob/main/README.md

With a system limited machine (2017 i5 iMac Cpu only) I am getting very pleasing results with:

Openhermes2-mistral (7B 4bit K_M quant) for general chat, desktop assistant, and some coding assistance - Ollama backend with my own front end U/I and llama-index libraries implementation. Haven’t tried 2.5 but may.

Synatra 7B mistral fine tune (4bit K_M quant) seems to produce longer responses and spicier with same system prompt (same use case as above)

Deepseek-coder 6.7B (4bit quant) as a coding assistant alternative to GPT-3.5 - just trying out in last week or so and building the personalized coding assistant front end u/I for fun

I was using WizardCoder 13b Q4 with very good results. So, give it a shot, see how it compares to DeepSeek Coder 6.7b, which I now run in Q8 with again, very good results.

phind in vs code https://marketplace.visualstudio.com/items?itemName=phind.phind

LoneStriker_OpenHermes-2-Mistral-7B-8.0bpw-h6-exl2 - my generic goto

LoneStriker_airoboros-l2-70b-3.1-2.4bpw-h6-exl2 - this one (and the whole family) is great for creative and precise tasks. If they don't work I jump to wizardlm or vicuna.

oobabooga_CodeBooga-34B-v0.1-EXL2-4.250b and phind-codellama-34b-v2.Q4_K_M.gguf are great for coding. I haven't decided which one is better yet.

Llama2-70B for generating the plan and than using CodeLlama-34B for coding, or LLama-13B for executing the instructions from LLama-2-70B

Currently in the process of exploring what other models to add once LLama2-70B generates the plan for what needs to get done

latimar/Phind-Codellama-34B-v2-megacode-exl2 4.8BPW. As far as I know the best instruct programming model?

setting up the 34 b phind coder model

Phind-Codellama-34B
20GB size

GGUF (made for lama)
AWQ
GPTQ

The default groupsize for a GPTQ is 1024, so a model "without groupsize" is actually using a much higher value.

As perlamer then explains, the lower the groupsize, the better the accuracy but also the higher the VRAM requirements.

128 appears to be the optimal value, but it will use more VRAM than a model created with the default of 1024.

The reason that 30B models are being offered at both 128 and 1024 groupsize is that a 128 model is likely to exceed 24GB VRAM on longer responses, which means it can't be reliably run on a 3090, 4090, 3090Ti, A5000, etc. Whereas a model with 1024 can be.

vllm for serving
https://github.com/vllm-project/vllm

awq is slightly higher quality then gptq but its very slightly. Gguf and exl2 tho reach similar quality to awq.
the highest 4 bit quality i believe is with spqr

xwincoder 33b is new and subjectively anecdotally I think i'm happier with it than phind and deepseek

I think deepseek is a top contender in the battle to put random characters after pretty good output

One really powerful thing people do is train a ton of soft prompts and store them in a vectordb under an embedding of the user request that the soft prompt is trained on

I have a function that finds the last code block and merges the dict there with the workflow that the state machine is operating over

INSTLD: the simplest package management can solve package problems

oogabooga or llama are model installation environments

i use viimium and have a script running which monitors my clipboard for code
i just monitor ~/Downloads/ for text files with inotify/python

