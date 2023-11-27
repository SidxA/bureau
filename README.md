# project aim
pdf comprehension backend to build personal bureaucratic database

# situation

- proof of concept of text extraction from scanned documents
- german language, needs a translation pipeline
- first steps are testing out the different versions of [layoutlm](https://github.com/microsoft/unilm/blob/master/layoutlmv3/README.md) (utilizing OCR optical character recognition intermediate step) and [donut](https://github.com/clovaai/donut) (just image based) on a couple of test documents
- hardware and backend/frontend combination is easy using huggingface such as in [this example](https://www.youtube.com/watch?v=6b3S2D2TiAo), but very picy to experiment
- approach is colab T4 / local hosting for now

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
