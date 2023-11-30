# Enhanced Document Processing Pipeline

## Overview
This pipeline integrates advanced OCR, layout analysis, and AI (GPT-4) to address the challenges of bbox allocation and form widget processing in documents.

## Pipeline Steps

### 1. Preprocessing
- **Advanced OCR Implementation**
  - Input: Original document images.
  - Process: Apply advanced OCR technology to extract text, with a focus on form widgets.
  - Output: Text data with bbox coordinates.

- **Image Pre-Processing**
  - Process: Enhance image quality for OCR (noise reduction, contrast adjustment).
  - Output: Optimized images for OCR.

### 2. Layout Analysis
- **LayoutParser Application**
  - Input: Original or pre-processed document images.
  - Process: Use layoutparser to identify and classify document elements, including widget areas.
  - Output: Structured layout data with bbox coordinates.

### 3. Data Integration and Refinement
- **Merge OCR and Layout Data**
  - Process: Combine OCR and layoutparser outputs, aligning text with layout elements.
  - Output: Integrated data structure.

- **Custom Post-Processing for Widgets**
  - Input: Integrated data with focus on widget areas.
  - Process: Apply custom scripts to refine OCR outputs for widgets.
  - Output: Refined data structure.

### 4. GPT-4 Processing
- **Semantic Summarization and Contextualization**
  - Input: Refined data structure.
  - Process: Use GPT-4 to interpret and summarize document content, focusing on bbox and widget challenges.
  - Output: Semantic summaries and contextualized content.

### 5. Label Synthesis and Structuring
- **Structured Label Generation**
  - Input: GPT-4 semantic summaries.
  - Process: Use GPT-4 to synthesize structured labels for document elements, including widgets.
  - Output: Structured document with refined labels.

### 6. Post-Processing and Validation
- **Validation and Correction**
  - Process: Review GPT-4 output, validate against original data, and correct discrepancies.
  - Output: Validated and corrected structured document data.

### 7. Output Generation
- **Final Structured Document Creation**
  - Process: Convert validated data into the desired output format (e.g., JSON).
  - Output: Structured document ready for downstream applications.

## Conclusion
This comprehensive pipeline is designed to effectively address the complexities of document processing, including bbox allocation and form widget recognition, by leveraging a combination of advanced OCR, layout analysis, and AI capabilities.


# Hierarchical Document and Form Comprehension Strategy

## Hierarchical Structure

### Document Level
- **Type**: Form, letter, invoice, report, etc.
- **Metadata**: Title, author, date, document ID.

Deep Learning-based Image Classification

- **Convolutional Neural Networks (CNNs)**:
  - Utilize CNNs to capture visual features from document images.
  - Ideal for classifying different types of documents.

- **Transfer Learning**:
  - Implement pre-trained models like ResNet or VGGNet.
  - Fine-tune on a specific dataset for various document types.

  
### Section Level
- **Major Sections**: Header, footer, main content, sidebars.
- **Subsections**: Introduction, conclusion, abstract, etc.

Natural Language Processing and Segmentation

- **Text Segmentation Algorithms**:
  - Use NLP techniques to segment the text into sections.
  - Algorithms like TextTiling or C99 for unsupervised segmentation.

- **Named Entity Recognition (NER)**:
  - Implement NER to identify and categorize section titles and headings.

- **Machine Learning Classification**:
  - Train classifiers like SVM or Random Forest on labeled data to identify specific section types.


### Content Level
- **Textual Elements**: Paragraphs, headings, subheadings.
- **Lists**: Bullet points, numbered lists.
- **Tables**: Headers, rows, columns.
- **Form Elements**: TextRuns, Widgets, Text Fields, Choice Groups.
- **Visual Elements**: Images, figures, graphs.

Deep Learning and Text Analysis

- **Entity and Pattern Recognition**:
  - Use NLP to identify entities (like dates, names) and patterns (bullet points, numbering in lists).

- **Deep Learning for Structure Recognition**:
  - Implement CNN or RNN models to recognize and classify content elements like paragraphs, lists, tables.

- **OCR Post-Processing**:
  - Apply algorithms to refine OCR text, identifying content boundaries and structures.


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

# Algorithms for OCR Output Processing in JSON Format

## Confidence Score Selection
- **Algorithm**: Choose text with the highest OCR confidence scores.
- **Python Libraries**: `json` for loading data, `pandas` or `numpy` for data analysis.

## Cross-Tool Validation
- **Algorithm**: Compare and validate OCR results from different tools.
- **Python Libraries**: `python-levenshtein` for measuring text similarity.

## Majority Voting
- **Algorithm**: Select the most common OCR result from multiple outputs.
- **Python Libraries**: Use `collections.Counter` for result tallying.

# Strategy for Calculating a Unified OCR Confidence Metric

1. **Character-Level Confidence Calculation**:
   - Calculate the average confidence score for each structural element (paragraph, table, etc.).
   - Use weighted averaging if confidence scores are available at different granularities (character, word, line).

2. **Error Rate Estimation**:
   - Periodically test OCR output against a validation set.
   - Adjust the overall confidence score based on the observed error rate.

3. **Consistency Check Across Tools**:
   - Compare OCR outputs from different tools for each structural element.
   - Adjust confidence scores based on the level of agreement.

4. **Post-Processing Corrections Tracking**:
   - Monitor the frequency and extent of manual corrections post-OCR.
   - Factor in the correction rate to adjust the element-wise confidence score.

5. **Final Confidence Metric**:
   - Combine the above metrics into a single confidence score for each structural element.
   - This can be a weighted sum or an algorithmically determined score considering all factors.



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
