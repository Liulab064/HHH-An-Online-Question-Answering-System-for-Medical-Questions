# HHH-An-Online-Question-Answering-System-for-Medical-Questions
## System description
The system can be divided into two parts. The first part is the knowledge graph question answering and the second part is if the 
knowledge graph cannot find the answer of the user inputted question, the second part will help to retrieve the top k most related answers by computing the medical question similarity from a medical question answer pair dataset.

Here are some useful reference links.
## Knowledge graph establishment refer the following link
https://github.com/liuhuanyong/QASystemOnMedicalKG

## Google English words pre-train model: GoogleNews-vectors-negative300.bin.gz
The pre-train model will be used to load word embedding before training the BiLSTM+Attention model and HBAM model.

https://drive.google.com/file/d/0B7XkCwpI5KDYNlNUTTlSS21pQmM/edit?usp=sharing

## Datasets
### Medical knowledge dataset collected from the following medical website
https://www.medicinenet.com/medterms-medical-dictionary/article.htm

https://www.nhsinform.scot/illnesses-and-conditions/a-to-z

### Model train_dev_test dataset are filter out the medical related questions from Quora question pair dataset.
https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs

### Medical question and answer pair dataset is referred from the following link.
https://github.com/LasseRegin/medical-question-answer-data

### The scale of knowledge graph about 700 diseases. For each disease, there exists symptom, accompany_disease, prevent_way, cure_way and totally 6 entities.
<img src="./Medical_knowledge_graph_establishment/System_screenshot/Figure_3.png" width="800" />

## System architecture
<img src="./Medical_knowledge_graph_establishment/System_screenshot/system_architecture.png" width="800" />

### Disease symptom entity extraction & User intention recognition
<img src="./Medical_knowledge_graph_establishment/System_screenshot/disease_symptom_entity_extraction_user_intention_recognition.png" width="800" />

### Knowledge graph answer selection
<img src="./Medical_knowledge_graph_establishment/System_screenshot/knowledge_graph_answer_selection.png" width="800" />

### Question_answer_pair_answer_selection
<img src="./Medical_knowledge_graph_establishment/System_screenshot/question_answer_pair_answer_selection.png" width="800" />

### Web GUI manager
<img src="./Medical_knowledge_graph_establishment/System_screenshot/web_gui_manager.png" width="800" />

Medical Knowledge Graph Establish, GUI and website
The main code is based on the following link. You need to run the build_medicalgraph.py to establish the knowledge graph before you use it. Then you may run GUI.py to run the GUI interface. You can also run chatbot_graph.py which will allow you to chat in command. You can also run server.py to start the website and chat.
https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/Medical_knowledge_graph_establishment/MedicalKBQA

## Models
### BERT
https://github.com/google-research/bert

### BiLSTM+Attention
https://github.com/likejazz/Siamese-LSTM

https://github.com/LuJunru/Sentences_Pair_Similarity_Calculation_Siamese_LSTM

### Siamese Hierarchical BiLSTM Word Attention Manhattan Distance model
<img src="./Medical_knowledge_graph_establishment/System_screenshot/Siamese_Hierarchical_BiLSTM_Attention_Manhattan_Distance_model.png" width="800" />

### AttentionLayer is referred from the following link
https://github.com/uhauha2929/examples/blob/master/Hierarchical%20Attention%20Networks%20.ipynb

## Experiment Results
### Model eval-accuracy comparison 
The total number of medical related data from Quora dataset is nearly `70000`, but we randomly pick the `10000` as the (train/dev/test) dataset.

The number distribution of `train: dev: test = 6:2:2`

|Model|Average Eval_accuracy by three times|Range of change|
|:---|:---|:---|
|BERT baseline model|0.7686|(-0.0073, +0.0057)|
|HBAM model|**0.8146**|(-0.0082, +0.0098)|
|Bi-LSTM + Attention model|0.8043|(-0.0103, +0.0062)|

## Code and data for the Medical Sentence Similarity Calculation Model
#### Our HBAM [[Code](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/HBAM)] [[Data](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/Data/Model_train_dev_test_dataset/Other_model_train_dev_test_dataset)]

#### Bi-LSTM+Attention [[Code](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/BiLSTM%2BAttention)] [[Data](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/Data/Model_train_dev_test_dataset/Other_model_train_dev_test_dataset)]

#### MaLSTM [[Code](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/MaLSTM)] [[Data]( https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/Data/Model_train_dev_test_dataset/Other_model_train_dev_test_dataset)]

#### Finetuning BERT [[Code](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/BERT_fine_tuning)] [[Data](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/master/Data/Model_train_dev_test_dataset/BERT_train_dev_test_dataset)]

## Installation
~~~bash
conda create -n hhh python=3.6
conda activate hhh
git clone https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions.git
cd HHH-An-Online-Question-Answering-System-for-Medical-Questions
pip install -r requirements.txt
~~~

## Updates
[08/03/2023] We rewrite code for `HBAM` and `MaLSTM` using tensorflow 2.0+ and add `tensorboard` sentence embedding visualization under branch [`origin/tensorflow2`](https://github.com/14H034160212/HHH-An-Online-Question-Answering-System-for-Medical-Questions/tree/tensorflow2).

## Reference papers
[Hierarchical attention networks for document classification](https://www.aclweb.org/anthology/N16-1174)

[Siamese Recurrent Architectures for Learning Sentence Similarity](https://ojs.aaai.org/index.php/AAAI/article/view/10350)

## Paper link
[HHH: An Online Medical Chatbot System based on Knowledge Graph and Hierarchical Bi-Directional Attention](https://arxiv.org/pdf/2002.03140.pdf)

If you want more details about this project, watch our [presentation recording](https://youtu.be/zTK3zZtxHs4), [HHH Chatbot web and GUI](https://youtu.be/qHUuB4eIsBo), [HHH web manager backend platform](https://youtu.be/ryj5ClrV6EE) on YouTube. 

## Citation
```
@inproceedings{bao2020hhh,
  title={HHH: An Online Medical Chatbot System based on Knowledge Graph and Hierarchical Bi-Directional Attention},
  author={Bao, Qiming and Ni, Lin and Liu, Jiamou},
  booktitle={Proceedings of the Australasian Computer Science Week Multiconference},
  pages={1--10},
  year={2020}
}
```

## Acknowledgement
This research was supported by summer scholarship funding from the Precision Driven Health research partnership.

## Other links
[MANDY: Towards a Smart Primary Care Chatbot Application](https://link.springer.com/chapter/10.1007/978-981-10-6989-5_4)
