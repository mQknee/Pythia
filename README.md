# Pythia
Pythia App: 
The goal of the app is to extract information from documents containing text and images using spaCy to generate weak multimodal labels that are then used for annotation in the spaCy developed annotation tool Prodigy. 

The ideal use case is circular: a user comes to the Streamlit web app to upload documents, results are returned from the pipeline and visualized in the web app. Based on the quality of results from the pipeline the user will look to improve the NER and similarity by annotating the documents uploaded. 

Tools: spaCy, gloVe, fasttext, Prodigy Annotation, Streamlit, Github
spaCy Nightly Release: https://nightly.spacy.io/usage/linguistic-features

Here are the key activities the pipeline needs to deliver against:
Upload documents
Pretrained spaCy nightly pipeline returns:
	NER - pretrained
New classes: Technical/Non-technical document labels, PII, Highlights/Non-highlights
	Similarity via spaCy Sense2vec
Results are available for download
Option to annotate data that was uploaded
Prodigy Annotation 
Select model to annotate/teach: NER, Text Classification, Sense2Vec
After annotation is completed, model is retrained
User goes back to the Streamlit web application to repeat the process of uploading documents

Sitemap:
Home- User selects Information Extraction (visualize text/generate data) or Annotation (teach models/improve results)
	L1: List/Visualize document results in a single page 
		Provide link to annotation page 
		Export/Download results 
	L1: Prodigy annotation
		User selects which model to teach
Sense2vec recipe
			NER
Text classification recipe
			

User Flow: 
Input: User navigates to the Streamlit web application and either copy/paste text or uploads document then manually initiates the knowledge extraction. Similar to the upload experience here: https://discuss.streamlit.io/t/brain-tumor-classifier-app/8427
User Action: Copy/paste text 
User Action: Upload (can contain text+images)
Microsoft Word document
PDF
JSON
Uploaded text/docs hit the pre-made Spacy component pipeline: transformer, parser, tagger, ner, attribute ruler, lemmetizer, similarity.

Component Pipeline:
Pipeline:https://nightly.spacy.io/models/en#en_core_web_trf
Pipeline Github: https://github.com/explosion/spacy-models/releases/tag/en_core_web_trf-3.0.0a0
Requirement: Additional pipeline component: Sense2Vec
Github: https://github.com/explosion/sense2vec

Visualize Output/Download: User views, interacts and downloads NER and similarity outputs from the  streamlit application
Spacy-Streamlit premade tempate for NER, POS and dependency: https://github.com/explosion/spacy-streamlit

User selects a model to annotate via Prodigy Recipes 
Prodigy Annotation Recipes
Sense2vec Prodigy Recipes: https://github.com/explosion/sense2vec#-prodigy-recipes
Optional: Prodigy-Streamlit: https://gist.github.com/ines/0adc578bffff78de32e706ef987bddde
NER: https://prodi.gy/docs/named-entity-recognition#transformers-tokenizers
Text classification: https://prodi.gy/docs/text-classification
Must be setup for active learning
A/B Evaluations: https://prodi.gy/features/ab-evaluation
2 use cases: Sense2vec recipes + Concept testing


Nice to have: Train custom vector space using a pre trained spaCy model, raw text and GloVe or Word2Vec via fastText (details). 
DBPedia word vectors: https://fasttext.cc/docs/en/supervised-models.html#content
Fasttext pretrained word vectors: https://fasttext.cc/docs/en/pretrained-vectors.html
GLOVE: https://github.com/stanfordnlp/GloVe
2019 Reddit training data:https://files.pushshift.io/reddit/comments/
DBPedia word vectors: https://fasttext.cc/docs/en/supervised-models.html#content
Fasttext pretrained word vectors: https://fasttext.cc/docs/en/pretrained-vectors.html
GLOVE: https://github.com/stanfordnlp/GloVe
2019 Reddit training data:https://files.pushshift.io/reddit/comments/

