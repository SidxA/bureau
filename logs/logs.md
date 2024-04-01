24/04/01

-upgraded to 2x3090 workstation
-the main idea has shifted away from app development (too large for myself) to iterative creation of digital assistant
-main tasks for assistant should be based on a function calling model
-there is the prebuilt polymind project which might be a start
-regarding DSPy, the modular LLM flow needs no optimisation yet, but it would be good to adopt modular syntax when starting LLM chaining
-use external code generation for now, while semi-autonomous code creation is surely a far-future goal
-first use case of function calling is around pdf-digestion
-the clearest approach to this is using the existing strong os OCR tools easyOCR and suryaOCR
-with the aim of converting pdf to txt representatives (database style)
-decided to do without containerization so far, but to keep track of everything
-if something breaks, or major modularity update, then do fresh setup

-software
go with recent python 3.11 and CUDA 12.1 and therefore relatively new pytorch

-aim
create database of pdf's
test OCR pdf to txt conversion
set up a database pipeline for this conversion
put this into a function