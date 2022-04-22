 [![Mailing list : test](http://img.shields.io/badge/Email-gray.svg?style=for-the-badge&logo=gmail)](mailto:ashutosh.dongare@gmail.com) [![License: CC BY-NC 4.0](https://img.shields.io/badge/License-GNU%20AGPL%203.0-lightgrey.svg?style=for-the-badge)](https://github.com/AshutoshDongare/convo/blob/main/LICENSE)


# Fine-tune a pretrained 🤗 model for SoftSkill NER

![header](https://user-images.githubusercontent.com/18417621/164710324-54f54dbc-797b-4419-823e-3706d60a011f.png)

This repo shows how to fine tune custom NER model for softskills using 🤗 Huggingface pretrained model [distilbert](thttps://huggingface.co/distilbert-base-uncased). 

We will Fine-tune the model for softskill NER using 🤗 Transformers [Trainer](https://huggingface.co/docs/transformers/main/en/main_classes/trainer#transformers.Trainer). This is the simplest way to fine-tune a 🤗 Transformer model. You can however choose to do this using pytorch and tensorflow way which gives you flexibility to write your own custom training loops.

The custom dataset has aroun 119 sentences tokenized and annotated the way required by huggingface model for finetuning. the trained model still provides decent performance with such low number of training samples, it is resilient enough to identify the soft skills which are not in the training data. 

For production usecases you would definately want to compile atleast a few hundred to thousands training samples.

sample dataset format is given below.

```
{"id":"101", 
 "ner_tags" :[0,0,0,0,0,0,0,1,0,0,0,0,0], 
 "tokens":["a","good","project","manager","is","able","to","prioritize","from","the","list","of","tasks"]
 }
 ```
this custom training data has some of the typical Softskills like  "positive attitude", "leadership", "customer focus" etc.

### Below is the metrics for this fine tuned models
![Metrics](https://user-images.githubusercontent.com/18417621/164762441-2c3103c3-7dfd-4386-add5-b0315ba336d2.png)


## Inference
The training script takes a sample sentence and runs inference on it to check whether the NER model is trained properly and it can perform softskill NER classification. Model is able to classify unseen softskills such as "composed" and "Professional". 

NER =  composed
NER =  confident
NER =  professional
NER =  leadership

## Citations

This repo is based on [Huggingface](https://huggingface.co/), compiled for Custom NER fine-tuning
