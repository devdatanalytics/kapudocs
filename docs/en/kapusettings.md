# Developers Corner

### Development of KaPU Edu
KaPU Edu consists of two Retrieval-Augmented Generation (RAG) applications, an English and Kiswahili chatbots.
Each is a chatbot that assists farmers by answering questions related to poultry diseases in English and Kiswahili language.
The KaPU Edu chatbot leverages a custome prompt, a large language model (LLM), and an API to provide accurate and context-specific responses.

Both the Englisth RAG and Kiswahili RAG combine retrieval-based and generative AI techniques to provide accurate and context-aware responses. RAG apps use a predefined knowledge base on poultry diseases and poultry farm management practices in English and Kiswahili languages. Custom prompts ensure the chatbots respond only to relevant queries.

Key Features:

* English and Kiswahili language support for farmers
* Focused on poultry diseases and poultry farm management related queries
* Integration with the Sarufi API for conversational AI
* Customizable prompt to ensure relevance and accuracy

#### Development Process
__1. Data Collection and Pre-processing__

We compiled a validated knowledge-base on poultry diseases and poultry farm management practices.
Next, we formated the knowledge-base into a structured document in English and Kiswahili languages. Then we preprocessed the document using text extraction techniques and stored in a vector database for efficient retrieval.

__2. Selecting the LLM Model__

The KaPU Edu apps use __LLama3-70B-8192 model__, a state of the art large language model. It is a large-scale transformer model with __70 billion parameters__ and a context window of __8192 tokens__, that ensure of high-quality and context-aware responses. The LLama3 model has the ability to handle complex queries and generates high-quality, context-aware responses. We configured the LLaMa3 model with the following:

* Number of tokens:

The token limit defines the maximum number of tokens (words, subwords, or characters depending on the language model) that can be used in generating a response. Here, the token limit is `512`, meaning the model will generate responses up to this limit.

* Temperature:

A parameter that controls the randomness of the model responses. A higher value makes the responses more creative, while a lower value makes them more deterministic. In this case, Temperature = 1, meaning the model balances creativity and coherence in its responses.


__3. Defining the Custom Prompts__

The custom prompts ensure the chatbot adheres to its purpose and scope. 

The prompt used for English language is:

*`“You are a farmer assistant using English language to answer the farmer questions based on the document provided about poultry diseases. You don't need to answer any question not related to the knowledge on the document provided."`*

The prompt used for Kiswahili language is:

*`"Wewe ni msaidizi wa mkulima ukitumia lugha ya Kiswahili kujibu maswali ya mkulima kulingana na hati iliyotolewa kuhusu magonjwa ya kuku. Huna haja ya kujibu maswali yasiyohusiana na yaliyomo kwenye hati iliyotolewa"`*

This prompt ensures:

* The chatbot responds only to poultry disease-related questions
* Answers are generated in English or Kiswahili
* Irrelevant queries are ignored


__4. Retrieval-Augmented Generation (RAG) Implementation__

a.	Document Indexing: The knowledge base was tokenized and stored in a vector search engine.

b.	Query Processing:When a user submits a question, the query is embedded and matched with the most relevant document sections.

c.	Response Generation: The retrieved information is passed to the LLM, which generates a response either in Kiswahili English adhering to the provided prompt constraints.

__5. Deployment__

The two RAG apps are deployed as an API-integrated solution using the <a href=https://www.sarufi.io/ target="_blank">Sarufi platform</a>, allowing seamless integration into web and mobile applications. The deployment process covered the following:

a.	Setting up the API endpoint from the Sarufi Platform

b.	Configuring authentication and headers

c.	Embedding the API in the target application (web or mobile)

### Development of KaPU Detect 

KaPU Detect model was developed using Object detection, a Computer vision task that predicts the region where the objects are present and classify all objects in the image. We used a YOLOv8 object detection model to train the chicken droppings images for five (5) classes. The classes are Coccidiosis (cocci), Newcastle disease (ncd), Salmonella (salmo), healthy and other.
KaPU Detect model aims to support poultry health management through early diseases diagnostics.

__1. Training Methodology__ 

1.1. Model Architecture

* Model: YOLOv8s (small variant) for Mobile phone inference
* Description: A single-stage object detector balancing speed and accuracy, ideal for near real-time applications.

1.2. Dataset

* Classes: 5 (cocci, healthy, ncd, other, salmo) + background
* Dataset Split:
    * Training: 5129 images
    * Validation: 1449 images
* Source: defined in `data.yaml`
  > * <a href="https://zenodo.org/records/4628934#.Y4duFLJBzvU" target="_blank">Machine Learning Dataset for Poultry Diseases Diagnostics</a>
  > * <a href="https://zenodo.org/records/5801834" target="_blank">Machine Learning Dataset for Poultry Diseases Diagnostics - PCR Annotated </a>

1.3. Training Parameters

* Pre-trained Weights: `yolov8s.pt`
* Epochs: 500 (early stopping patience: 50)
* Batch Size: 16
* Image Size: 800x800 pixels
* Optimizer: SGD (lr=0.01, momentum=0.9)
* Data Augmentation: Default settings (augment=False)
* Loss Functions:
  > * Box Loss: 7.5
  > * Classification Loss: 0.5
  > * Distribution Focal Loss (DFL): 1.5

1.4. Training Environment

* Hardware: NVIDIA A10G GPU (22,516 MiB)
* Software:
  > * Ultralytics YOLOv8.0.196 o Python 3.11.4
  > * PyTorch 2.0.1+cu118
  > * CUDA 11.8

__2. Evaluation Metrics and Results__

2.1 Normalized Confusion Matrix:
<figure>
    <img src ="/kapudocs/assets/cmatrix.png" alt="matrix" style="width:50%">
    <figcaption>Confusion Matrix</figcaption>
</figure>
* Precision: cocci (74%), healthy (70%), ncd (79%), other (85%), salmo (83%)
* Misclassification Patterns: Background often confused with cocci (22%), healthy (25%), and ncd (21%)

2.2 Precision-Recall Curves
<figure>
    <img src ="/kapudocs/assets/curve.png" alt="curve" style="width:50%">
    <figcaption>Precision-Recall Curves</figcaption>
</figure>
* Class-wise AP:
  > * cocci: 0.737
  > * healthy: 0.693 
  > * ncd: 0.757
  > * other: 0.764
  > * salmo: 0.781
* mAP@0.5: 0.746

2.3 Predictions

<figure>
    <img src ="/kapudocs/assets/predict.png" alt="predict" style="width:50%">
    <figcaption>Example predictions</figcaption>
</figure>
* It is observed from the example predictions that there is accurate detections for cocci and healthy classes; with occasional overlapping boxes and misalignment in dense regions.
* Confidence Scores: High scores correlate with accuracy; lower scores (e.g., 0.3) indicate uncertainty.