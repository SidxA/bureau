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
nope its python 3.10

-aim
create database of pdf's
test OCR pdf to txt conversion
set up a database pipeline for this conversion
put this into a function

24/04/09

-decided to just try DSPy with EXL2 mixtral model on tabbyAPI
-

-todo
motherboard fan settings, maybe just put full fans when above 35°
gpu power downplay to about 250W
bios check pcie slots configuration (nvtop says theyre only 1@16x)

PCIe Configuration: Navigate to the "Advanced" tab or similar. Look for settings related to PCIe/PCI Configuration. Ensure PCIe slots are set to operate at the maximum supported generation (e.g., Gen 4 or Gen 5 for your RTX 3090s). If you see options like "PCIe Slot Configuration," set it to "Gen4" or "Gen5" according to your GPUs' capabilities.
Above 4G Decoding/C.A.M.: Ensure "Above 4G Decoding" or "4G Decoding" and "Resizable BAR Support" are enabled. These settings allow your system to fully utilize the capabilities of your hardware, especially in configurations with high-end GPUs.
Multi-GPU Configuration: If available, check the settings related to multi-GPU or SLI/CrossFireX configuration to ensure your motherboard is configured to support dual GPUs optimally.

24/04/17
dspy

-set up server anew
-cuda keyring authentification still yields unknown apt source
-tabbyAPI install works with the manual pip build (saying 12-1 cuda when 12-4 is installed)
-downloading some deekseep v1.5 exl2 quant coder instruct
-huggingface-hub works for the model downloads
-tabbyAPI gradio loader can access the local tabbyAPI server
-the chat completions doent work yet, and neither does a dspy loader

24/04/18

-now it works with a custom loader class, dspy chain of thought
-need to keep in mind: max tokens and temperature
-now we want to have an overview table with general purpose and coding models
(templates + ctxt length)