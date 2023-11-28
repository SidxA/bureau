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

# project aim
pdf comprehension backend to build personal bureaucratic database

# next step

'baseline' llm pipeline / agent
- try out open interpreter
- try out langchain code generation pipelines
- set up execution pipeline

# project roadmap

the project is aimed at 'mid-threshold hardware' and full open source implementation

1. 'external' tool execution pipeline / agent
2. structured content extraction model finetuning
3. pipeline to frontend for testing deployment 

## 1. 'external' tool execution pipeline / agent
- the goal of content understanding of bureaucratic forms is so involved, there is no way to test it out seriously without some kind of automatized code generation and pseudo-self supervision, might aswell do it from the start
- code generation, execution and logging is supervised and validated externally
- this creates the need for a baseline agent class built on an instruct llm
- the baseline class requires a 'narrow goal script generation' action, including internal validation steps
- the external agent is not aimed at beeing aware of its own action history
- the action performance logging should go into a logging dump
- an idling action should be to archive the logging dump
- the external pipeline needs an action-execution-mechanic freeing all ressources for the individual tasks
- implementation is aimed at something like langchain or open interpreter
- first versions should run on colab t4
- aim is to build subsequent agent versions with more actions:
   - web based research
   - model finetuning
   - web scraping for bureaucratic forms
   - pseudo labelling of these using GPT4 vision
   - model inference run
   - testing suite built on model inference run
- using this external validation pipeline with a version control, the goal is to fine-tune a model for bureaucratic form content understanding
- bureaucratic form content understanding is mainly tied to understanding the form structure
- this is going to be computationally expensive
- its all going to be in python
- version control unclear: git/packages/libraries
- reliable translation framework required
## 2. structured content extraction model finetuning
- bureaucratic forms are highly ordered
- aim is to understand this structure based on ordered/nested classes
   - department/correspondence
   - header, optional subheader(s)
   - sections structure with (sub)headers
   - cross/tick structure
   - text structure
   - indentation structure within text
   - additional information structure such as page layout info
   - table structure
   - often, structures arise in a (nested) key-value structure
## 3. pipeline to frontend for testing deployment
- two aims using content structure extraction
   - creating personal bureaucratic database entry from scans
   - assisting in filling out empty forms


database system

- can be first a secure database (eg. [supabase](https://github.com/supabase/supabase)) with essential bureaucratic information, which ties to hardware
- has a meta-knowledge obligation, ie. feedback of content and categorization
- llm hybrid-query and rag accessing
- different parallel categorical systems (better then nested?, both limited)
- embedding models are also part of the database system

# resources

- [layoutlm](https://github.com/microsoft/unilm/blob/master/layoutlmv3/README.md) utilizing OCR optical character recognition intermediate step
- [donut](https://github.com/clovaai/donut) image based
- layoutlm with huggingface,streamlit,pytorch: [colab](https://colab.research.google.com/drive/1I0Qyajp_DFzKvQfUwwRc9p6fs6NfI-Kx?usp=sharing), [extensive](https://www.mlexpert.io/machine-learning/tutorials/document-classification-with-layoutlmv3)

- [pdfplumber: extract tabular pdf data](https://www.youtube.com/watch?v=x9IDL8eruAw)
- [document key-value finetuning of layoutlm using labelstudio](https://www.youtube.com/watch?v=bBwDTY38X58&list=PLeNIpK8NwtHtxa2wC1OcPb8RmQ9vy-Uav)
- [transformer fine tuning tutorials](https://github.com/NielsRogge/Transformers-Tutorials)
- [fine tuned donut model for document content extraction](https://github.com/katanaml/sparrow)

- [gptchat powered online research](https://github.com/assafelovic/gpt-researcher)
- [usefull api list](https://github.com/public-apis/public-apis)
- [browser automation tools](https://github.com/angrykoala/awesome-browser-automation)
- [gptchat powered python app development](https://github.com/Pythagora-io/gpt-pilot)
- [open code interpreter](https://github.com/shroominic/codeinterpreter-api)
- [some unsupervised learning ideas](https://www.youtube.com/watch?v=UaJDdft6BdI)
