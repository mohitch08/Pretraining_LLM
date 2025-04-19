# Pretraining_LLM


## 📦 Datasets

We work with two types of datasets:

1. **Instruction/QA-Based Dataset**  
   Download an existing dataset from [Hugging Face](https://huggingface.co/datasets) with structured question-answer or instruction-response pairs.

2. **Code-Based Dataset**  
   Build a custom dataset of Python scripts scraped from GitHub to evaluate model performance on code-specific tasks.

---

## 🔧 Pretraining Model Initialization Strategies

We explore four methods to initialize model weights before training:

### 1. Random Weight Initialization
Start from scratch by initializing model weights randomly.

### 2. Continued Pretraining
Use weights from an existing model as a starting point and continue pretraining with a new dataset.

### 3. Downscaling a Model
Use a larger model and trim its layers to create a smaller architecture.  
**Example:** Downscale `tinySolar-248m-4k` from 12 layers → 10 layers.

### 4. Upscaling a Model
Extend a smaller model by adding layers and selectively reusing pretrained weights.  
**Example:** Upscale `tinySolar-248m-4k` from 12 layers → 16 layers.

#### Upscaling Steps:
1. Configure a 16-layer model with random weights.
2. Load the pretrained 12-layer `tinySolar-248m-4k` model.
3. Copy the bottom 8 and top 8 layers from the 12-layer model to replace the corresponding layers in the new 16-layer model.
4. Transfer embedding and classification layers to the new model.


## 📊 Evaluation: Open LLM Leaderboard Benchmark

Evaluate our model using popular LLM benchmarks. Here's a helper function and task configuration like MMLU, hellaswag, GSM8K, winogrande, arc_challenge, truthfulqa_mc2


