# Movie Plot & Genre Generator

**Project Overview**
This milestone project builds a movie plot genre generation using the pretrained model (facebook/opt-125m) on a cleaned IMDB movie datset. Given a movie's plot description, the model will generate the correct multi-lable in the following format:

Input:  Plot: [description] -> Genre:

Output: Comedy, Drama, Romance

There are 3 Systems Being Compared:
* Base Model: opt-125m with no fine tuning.
* Full SFT: All 125 million parameters are trained through Supervised Fine Tuning.
* LORA: Only a specifc number of parameters (294,912) are trained through Parameter-Efficient Fine Tuning (PEFT).

**Key Findings**: LORA dramatically outperforms the full fine tuning on the small dataset, which avoids a collapse that was discovered in full SFT.

**Environment & Setup Instructions**
1) Click on "final_implementation_zharinna.ipynb" file in repository.
2) Click on Open in Colab" link at the top of the file to open the notebook in Google CoLab. 
3) Change the runtime type by going to the "Runtime" tab, then go to "Change runtime type", and switch to GPU (T4 GPU).
4) Upload the output_data.json file to the CoLab folder.
5) Install all the dependcies that are the first two cells at the top of the notebook. Only need to run them once to keep dependencies up to date.

**Run Training & Evaluation/Where to Produce the Demo**
Run ALL of the cells directly from top to bottom. See the "Table of Contents" for better navigation of the notebook.

Total Runtime is from 10 to 15 minutes on T4 GPU.

**Reproduce Plots and Tables**
* Learning Curves are generated and save in "results" folder under section "Learning + Loss Values Comparisons" cell .
* Comparison Tables are displayed under the section "Results Comparisons" cell, it uses pandas and shows the trainable parameters+percentage, validation and training loss, and generation quality across all three systems.
* Generation Output Tables are displayed when running the specific cells of "Baseline Model Generations", "Full Supervised Fine Tuning", and "LORA Supervised Fine Tuning".

**Where Outputs Are Saved**
* Learning Curve: results folder
* Full SFT Check points: movie_genre_outputs/full_ft
* LORA Training checkpoints: movie_genre_outputs/LORA_sft

**Hardware Assumptions & Resource Limitations**
* GPU Required: This notebook requires that the runtime is GPU, using CPU would result in the runtime becing extremely slow and is not recommanded.
* Recommanded Hardware: Google CoLab T4 GPU
* RAM: 12GB RAM is enough
* Limitations: Full SFT experiences a collapse due to the dataset size, LORA is the recommanded system to reprimand that.
