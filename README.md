# Hierarchical Document and Form Comprehension Strategy

## Hierarchical Structure

### Document Level
- **Type**: Form, letter, invoice, report, etc.
- **Metadata**: Title, author, date, document ID.

### Section Level
- **Major Sections**: Header, footer, main content, sidebars.
- **Subsections**: Introduction, conclusion, abstract, etc.

### Content Level
- **Textual Elements**: Paragraphs, headings, subheadings.
- **Lists**: Bullet points, numbered lists.
- **Tables**: Headers, rows, columns.
- **Form Elements**: TextRuns, Widgets, Text Fields, Choice Groups.
- **Visual Elements**: Images, figures, graphs.

## Data Prediction Format
- **JSON Structure**: Nested JSON objects for each level, with metadata, content, and children.

## Multi-Page Strategy
- **Page-wise Segmentation**: Each page as a separate entity.
- **Cross-Page Linking**: Connect related elements across pages.
- **Metadata Consistency**: Across pages for multi-page documents.

## Implementation

### Machine Learning Models
- **Specialized Models**: Different models for text, images, structure.
- **Training**: On respective hierarchical levels.

### Human Validation and Feedback Loop
- **Review and Correction**: Of machine-generated labels.
- **Model Refinement**: Based on feedback.

### Tool Integration
- **Layout Parser**: For image analysis.
- **Custom Models**: For text and structure analysis.

# Prominent Python OCR Tools

## Standard OCR
- **Tesseract**: An open-source OCR engine.
- **Pytesseract**: Python wrapper for Tesseract.

## Advanced OCR
- **ABBYY FineReader**: Known for high accuracy in complex layouts.
- **Google Cloud Vision API**: Offers powerful image analysis.

## Handwriting Recognition
- **Microsoft Azure Computer Vision**: Good for handwriting and print.
- **Google Cloud Vision API**: Also handles handwriting effectively.

## Language-Specific OCR
- **Tesseract with Language Packs**: Supports multiple languages.
- **EasyOCR**: User-friendly and supports over 60 languages.



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
