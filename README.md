Sentence Transformer Model
===================== 

- #all-mpnet-base-v2 

This is a sentence-transformers model: It maps sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.

Model Specifications
=====================
This model is aim to train sentence embedding models on very large sentence level datasets using a self-supervised contrastive learning objective. 
It used the pretrained microsoft/mpnet-base model and fine-tuned in on a 1B sentence pairs dataset. 
It uses a contrastive learning objective: given a sentence from the pair, the model should predict which out of a set of randomly sampled other sentences, was actually paired with it in the given dataset.

Pre-training
===============
pretrained microsoft/mpnet-base model.

Fine-tuning
=============
Fine-tuned the model using a contrastive objective. 
First, it computes the cosine similarity from each possible sentence pairs from the batch. Then apply the cross entropy loss by comparing with true pairs.

Use cases
=========
Model is intented to be used as a sentence and short paragraph encoder. 
Given an input text, it ouptuts a vector which captures the semantic information. 
The sentence vector may be used for information retrieval, clustering or sentence similarity tasks.

Hyper parameters
=================
Trained ou model on a Tensor Processing Units TPU v3-8. Trained the model during 100k steps using a batch size of 1024 (128 per TPU core). 
Learning rate warm up of 500. The sequence length was limited to 128 tokens. And used the AdamW optimizer with a 2e-5 learning rate.
