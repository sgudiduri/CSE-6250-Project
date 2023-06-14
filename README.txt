### Knowledge-aware Assessment of Severity of Suicide Risk for Early Intervention Code Implementation 

The research paper "Knowledge-aware Assessment of Severity of Suicide Risk for Early 
Intervention" introduces a novel approach to identifying suicidal tendencies by analyzing
Reddit data. Traditional methods for identifying suicidal behavior or ideation rely on surveys,
questionnaires or patients sharing their mental health struggle and are typically not sufficient for
quantitative analysis. This paper incorporates domain specific knowledge into prediction of
suicide risk. The paper provides an annotated dataset of 500 Reddit users that contains post
content from mental health subreddits and the respective label (suicidal ideation, behavior,
attempt). A suicide risk severity lexicon is developed for each label using medical knowledge
bases and suicide ontology to detect suicidal thoughts, behavior and action. The feature set is
embellished with the addition of external features such as AFINN, Language Assessment by
Mechanical Turk, etc. The paper discusses how CNNs emerge as the superior model for suicide
risk prediction over rule based and SVM-linear models based on 4 evaluation metrics, namely -
Graded recall, Confusion matrix, Ordinal error and Perceived risk measure.

#### Dependencies

csv 1.0
datetime (Python built-in module)
gensim 4.3.1
keras 2.12.0
nltk 3.8.1 (Note: You need to download the 'punkt' resource from nltk)
numpy 1.22.4
pandas 1.4.4
Python 3.9.16
sklearn 1.2.2
spaCy 3.5.1
string (Python built-in module)
tensorflow 2.12.0

#### Download Instruction for Data

The data/ folder contains the following files - 

1. 500_Reddit_users_posts_labels.csv - Annotated Reddit Post data
2. AFINN-en-165.txt - Dataset contains words along with their AFINN score (ranging from -5 to 5)
3. labMT - Language Assessment by Mechanical Turk - Dataset contains words, their
average happiness score (polarity), standard deviations, and rankings (Twitter, Google,
NYT, Lyrics).

Download the ConceptNet term vectors ("English-only") 
from [https://github.com/commonsense/conceptnet-numberbatch] - numberbatch-en-19.08.txt.gz
Unzip numberbatch-en-19.08.txt.gz to obtain numberbatch-en.txt. Place numberbatch-en.txt in 
the data/folder. 

4. numberbatch-en.txt - A set of semantic vectors (word embeddings) 
5. External_Features.csv - Dataset contains users along with AFINN score, labMT scores,
First Person Pronouns Ratio, Height of the dependency parse tree and other characteristic features. 

#### Functionality of Scripts

1. create_external_features.ipynb - A Jupyter notebook used to generate External_Features.csv. This file
has already been run and the resulting output External_Features.csv is present in the data/ folder. 
2. 5_Label_Classification.ipynb - A Jupyter notebook that performs 5 label classification - Supportive, 
Indicator, Ideation, Behavior and Attempt. 
3. 4_Label_Classificaation.ipynb - A Jupyter notebook that performs 4 label classification - Supportive 
class is removed to focus on clinically relevant classes. 
4. 3+1_Label_Classification.ipynb - A Jupyter notebook that performs 3+1 label classification - Supportive
and Indicator classes are combined to form one control group class - No Risk class. 

#### Instruction to Run the Code

1. Download the code repository - Can be downloaded either as a ZIP file or using the command 
$ git clone https://github.gatech.edu/Sgudiduri3/CSE-6250-Project.git. If using Google Colab, 
please upload to your Google Drive, if running locally, make sure the necessary dependencies 
are installed. 

2. Download the ConceptNet term vectors ("English-only") 
from [https://github.com/commonsense/conceptnet-numberbatch] - numberbatch-en-19.08.txt.gz
Unzip numberbatch-en-19.08.txt.gz to obtain numberbatch-en.txt. Place numberbatch-en.txt in 
the data/folder. 

3. External_Features.csv is already present in the data/ folder. However, create_external_features.ipynb 
can also be run in order to generate External_Features.csv. 

4. Run the 3+1_Label_Classification.ipynb Jupyter notebook. Under the Hyperparameters section, please feel 
free to change the Hyperparameters. By default, the model runs a TF+CF scenario. To run only TF features, 
please comment out the lines 

tmp_feat.extend(list(train_ext_feat[index]))
tmp_feat.extend(list(test_ext_feat[index]))

5. Run the 4_Label_Classification.ipynb Jupyter notebook. Under the Hyperparameters section, please feel 
free to change the Hyperparameters. By default, the model runs a TF+CF scenario. To run only TF features, 
please comment out the lines 

tmp_feat.extend(list(train_ext_feat[index]))
tmp_feat.extend(list(test_ext_feat[index]))

6. Run the 5_Label_Classification.ipynb Jupyter notebook. Under the Hyperparameters section, please feel 
free to change the Hyperparameters. By default, the model runs a TF+CF scenario. To run only TF features, 
please comment out the lines 

tmp_feat.extend(list(train_ext_feat[index]))
tmp_feat.extend(list(test_ext_feat[index]))
