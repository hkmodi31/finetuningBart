**ProjectReport**

Harshkumar Modi

**Aim:** Use SAMsum dataset to compare different text summarization models and fine-tune a model to compare improvements

**Dataset:** Here we visualize the dataset we will be using to fine-tune the model. We can see the lengths of our input data vs the length of summaries. Upon rough estimation, we can see that the mean ratio of summaries to input data is 29%.



![Picture1](https://github.com/hkmodi31/finetuningBart/assets/47323046/31b31de0-dd8d-4780-9a98-a464fe4499a4)


![Picture2](https://github.com/hkmodi31/finetuningBart/assets/47323046/6024ce10-f354-407a-92c9-2bc543e3b362)


**Results:** For our comparison, I choose three text-summarization models from hugging face. My choices were based on size and popularity of models. One of the most downloaded models I found was the FalconAI’s Text Summarization model. Another model that I chose was Google’s t5-large model and Facebook’s Bart model.

All these models have their own set achievements. When tested on the same sample input, I did observe that FalconAI’s model didn’t summarize any of the text. Faceboo’s Bart model clipped the important snippets from the input to give only relevant parts of the conversation. However, Google’s t5 model was able to generate summaries of the text which resembling to the expected output. The reason for such varied results could be because of the training dataset used in preparing these models. Conversation is something that is new to all these databases and hence their outputs vary. The models are trained for certain use cases and summarizing a conversation might not be one of those. If we prepare the data according to a paragraph instead of the conversation, we will use the semantics as the dataset will not capture who spoke which line in the conversation.

Further, to use the weights and determine how fine-tuning a model trained on a huge dataset can help get preferred outputs of a custom use-case, conversation summarizing in this case, I choose the Facebook’s Bart model. The process of finetuning was carried out using the trainer packages from the transformer’s library. The steps involved pre-processing the dataset and using the weights from the Seq2SeqLM model (Bart). Training it on AWS Sage Maker, we achieved a good training and validation loss.

To compare the performances of the model, we use the rouge evaluation parameter on our test dataset. We subset 250 random samples from our test set and used it to determine rouge scores of each model.

Rouge scores vary from 0 to 1, where 0 defines a bad score and 1 defines a perfect score. The results achieved are as follows:

<img width="468" alt="Picture3" src="https://github.com/hkmodi31/finetuningBart/assets/47323046/7a97a881-b4cd-4954-8f61-6e6dea749601">


As observed, we were able to use Bart model which initially was performing poorly to beat the Google’s t5 model which happen to be working better than any other pretrained model without any tuning.
