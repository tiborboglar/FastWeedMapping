# Weed AI

The project pipeline worked as following:


### 1. Training resnet models

First we have to train the models on some good GPU since the smallest model (2-4 filter) already takes few hours on an NVIDIA Titan X .

Models are constructed by calling `models.py`

After training, they are saved as **.h5**

### 2. Generating benchmarks with NVIDIA Jetson

All inference files are saved in their respective folders "./WeedAI_Inference/Inferences/..."

Use script `from_h5_to_frozen_graph.py` to load the **.h5** model and further convert it into **flex_model**

All converted frozen graphs are going to be saved within "./Models/Frozen_graphs/*"

**Important Remark:** The vanilla resnet is converted to **flex model** here. Thus, the exported frozen graph is already a **flex model** on full-precision mode (FP32)

Call `predict_on_full_images.py` to generate annotations, inference times and confusion matrices. You can give the command line argument `-p FP16` to use half-precision or `-p FP32` for full-precision. All results generated at this stage are saved within "./Results/seeds/*"
