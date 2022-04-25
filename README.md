
# Sentiment Analysis with Google's AutoML Natural Language

This code shows you how to connect to gcp natural language AutoML and do the sentiment analysis 
and save the results in an excel file on your local. we will also be getting the sample texts from a bucket in gcp.
gcp buckets are simply containers that hold our data. Basicaly everything you store in the cloud should be contained in a bucket. 
For using automl, we have to provide the dataset ourselves, however training our model is all google's responsibility. 



## Appendix

**Google AutoML Natural Language:**

AutoML is a Google Cloud Service (still in beta) that enables the user to create customized machine learning models. In contrast to the Natural Language API, the AutoML models will be trained on the user’s data and therefore fit a specific task.
Custom machine learning models for classifying content are useful when the predefined categories that are available from the Natural Language API are too generic or not applicable to the specific use case or knowledge domain.
The AutoML service requires a bit more effort for the user, mainly because you have to provide a dataset to train the model. However, the training and evaluation of the models is completely automated and no machine learning knowledge is required. The whole process can be done without writing any code by using the Google Cloud console.
The AutoML service covers three use cases. All of these use cases support solely the English language for now.

AutoML Text Classification:

While the text classifier of the Natural Language API is pre-trained and therefore has a fixed set of text categories, the AutoML text classification builds customized machine learning models, with the categories that you provide in your training dataset.

AutoML Sentiment Analysis:

As we have seen, the sentiment analysis of the Natural Language API works great in general use cases like movie reviews. Because the sentiment model is trained on a very general corpus, the performance can deteriorate for documents that use a lot of domain-specific language. In these situations, the AutoML Sentiment Analysis allows us to train a sentiment model that is customized to your domain.

AutoML Entity Extraction:

In many business contexts, there are domain specific entities (legal contracts, medical documents) that the Natural Language API will not be able to identify. If we have a dataset where the entities are marked, we can train a customized model entity extractor with AutoML. If the dataset is sufficiently big, the trained entity extraction model will also be able to detect previously unseen entities.

**How to Use AutoML Natural Language:**

Using the three AutoML is a four step process and is very similar for all three methodologies:
- Dataset Preparation
The dataset has to be in a specific format (CSV or JSON) and needs to be stored in a storage bucket. For classification and sentiment models, the datasets contain just two columns, the text and the label. For the entity extraction model, the dataset needs the text and the locations of all entities in the text.
- Model Training
The model training is completely automatic. If no instructions are given otherwise, then AutoML will split the training set automatically into train, test and validation sets. This split can also be decided by the user, but that is the only way to influence the model training. The rest of the training is completely automated in a black-box fashion.
- Evaluation
When the training is finished, AutoML will display precision and recall scores as well as a confusion matrix. Unfortunately, there is absolutely no information about the model itself, making it difficult to identify the reasons for bad performing models.
- Prediction
Once satisfied with the model's performance, the model can be conveniently deployed with a couple of clicks. The deployment process takes only a few minutes.

AutoML Natural Language **Disadvantages**:

The training process is quite slow, probably because the underlying models are very big. The main problem with Google’s AutoML is that Google did not publish any details about the models used therefore there is absolutely no information about how and why the model is performing the way it has being performing! And fine tuning is also impossible. 



## Environment Variables

To run this project, you will need to add the following environment variables to your file in order to authenticate yourself.

`PROJECT_ID = "YOUR_PROJECT_ID`

`MODEL_ID = "YOUR_MODEL_ID`

`GOOGLE_APPLICATION_CREDENTIALS = "KEY.jason"`

`BUCKET = "YOUR_BUCKET_NAME"`


