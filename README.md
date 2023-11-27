# project aim
pdf comprehension backend to build personal bureaucratic database

# situation

- proof of concept of text extraction from scanned documents
- german language, needs a translation pipeline
- first steps are testing out the different versions of [layoutlm](https://github.com/microsoft/unilm/blob/master/layoutlmv3/README.md) (utilizing OCR optical character recognition intermediate step) and [donut](https://github.com/clovaai/donut) (just image based) on a couple of test documents
- hardware and backend/frontend combination is easy using huggingface such as in [this example](https://www.youtube.com/watch?v=6b3S2D2TiAo), but very picy to experiment
- next step: find a hosting solution for layoutlm, might be possible just locally?, approach is colab T4?

examples
- layoutlm with huggingface,streamlit,pytorch: [colab](https://colab.research.google.com/drive/1I0Qyajp_DFzKvQfUwwRc9p6fs6NfI-Kx?usp=sharing), [extensive](https://www.mlexpert.io/machine-learning/tutorials/document-classification-with-layoutlmv3)
- 

## outlook

- bureaucratic documents often have a distinct layout that structures the content
- goal is to identify key-value pairs to parse to a database later, this might require extensive fine-tuning
- test larger / multiple parallel smaller models
- pipeline might require to work in token space (english), try different embedding models

## examples

- [pdfplumber: extract tabular pdf data](https://www.youtube.com/watch?v=x9IDL8eruAw)
- [document key-value finetuning of layoutlm using labelstudio](https://www.youtube.com/watch?v=bBwDTY38X58&list=PLeNIpK8NwtHtxa2wC1OcPb8RmQ9vy-Uav)
- [transformer fine tuning tutorials](https://github.com/NielsRogge/Transformers-Tutorials)
- [fine tuned donut model for document content extraction](https://github.com/katanaml/sparrow)
  
## further ressources
- [gptchat powered online research](https://github.com/assafelovic/gpt-researcher)
- [usefull api list](https://github.com/public-apis/public-apis)
- [browser automation tools](https://github.com/angrykoala/awesome-browser-automation)
- [gptchat powered python app development](https://github.com/Pythagora-io/gpt-pilot)
- [open code interpreter](https://github.com/shroominic/codeinterpreter-api)
- [some unsupervised learning ideas](https://www.youtube.com/watch?v=UaJDdft6BdI)

# theory

## principles and mechanics

- finetuning data set creation can be automatized
- starting point is always a simple pipeline - indeed the flow of information is fundamental project topology
- the bridge to the users is vital - feedback, chat option
- a simple pipeline can be achieved with digital invoices and already exist
- the document layout - structuring the content - is difficult, ie. a meta-task
- overall, the project needs to incorporate different temporal paths, ie. obsolete models/tunes/databases need to be connected even when they are not in use (as inference marks the moment of existence)

## software parts
- database system
- content retrieval system


for the tool to be applicable in regards to privacy
- it can either run locally
- or encryption is vital

need some good hosting plan and interaction with local database
### database system

- can be first a secure database (eg. [supabase}(https://github.com/supabase/supabase)) with essential bureaucratic information, which ties to hardware
- has a meta-knowledge obligation, ie. feedback of content and categorization
- llm hybrid-query and rag accessing
- different parallel categorical systems (better then nested?, both limited)
- embedding models are also part of the database system

### content retrieval system

- there is multi-modality, but the focus is on text-llm for now
- structured content requires structured reading
- ocr - extract words and positions from document


# project roadmap

the project is aimed at 'mid-threshold hardware' and full open source implementation

1. 'external' tool execution pipeline / agent
2. structured content extraction model finetuning
3. pipeline to frontend for testing deployment

1. 'external' tool execution pipeline / agent
   - the goal of content understanding of bureaucratic forms is so involved, there is no way without automatized code generation and pseudo-self supervision, might aswell do it from the start
   - code generation, execution and logging is supervised and validated externally
   - this creates the need for a baseline agent class built on an instruct llm
   - the baseline class requires a 'narrow goal script generation' action, including validation steps
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
2. structured content extraction model finetuning
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
3. pipeline to frontend for testing deployment
   - two aims using content structure extraction
       - creating personal bureaucratic database entry from scans
       - assisting in filling out empty forms
