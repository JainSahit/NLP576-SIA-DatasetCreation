				Synthetic Dataset Creation

Dataset:
The columns in my dataset includes:
a.	Question_Id
b.	Question_stem
c.	Question_text (There are 4 text for each choice)
d.	Fact
e.	humanScore
f.	clarity
g.	turkIdAnonymized
h.	answerKey

After preprocessing the data in jsonl format, the following are the columns present in my dataset:
a.	Sentence_1: Question in the dataset
b.	Sentence_2: Facts corresponding to the question
c.	Score: SIA score between Sentence_1 and Sentence_2

The dataset I’m working is OpenBookQA dataset.
The dataset QA is provided by Allen AI has a collection of labeled pairs of Question Answers. The data is encoded in JSON lines format.

There are total of 4957 questions in the dataset. Each question has 4 choices associated with it. Each question has an exact answer and a fact which is helpful in answering the question. The dataset also has corpus which is named as crowdcorpus.txt from which I extracted the text with BM25 Model. 

For Example, sample data is of this form:

{"id": "7-980", "question": {"stem": "The sun is responsible for", "choices": 
[{"text": "puppies learning new tricks", "label": "A"},
 {"text": "children growing up and getting old", "label": "B"},
  	 {"text": "flowers wilting in a vase", "label": "C"}, 
 	 {"text": "plants sprouting, blooming and wilting", "label": "D"}]},
   	"fact1": "the sun is the source of energy for physical cycles on Earth",
"humanScore": "1.00", "clarity": "2.00", "turkIdAnonymized": "b356d338b7", "answerKey": "D"
}

Description: 
In order to generate SIA scores between 0-4, I used BM25 to generate text from corpus.
First thing to do is create an instance of the BM25 class, which reads in a corpus of text and does some indexing on it. We can give it the text of each choice and see which documents are the most relevant. In this manner I generated top2 relevant choices for each question in the dataset by mapping with the corpus. I formatted all the data from questions and BM25 generated facts such that each question will have 9 facts associated with it. Top 2 facts for each choice in the question with BM25 model with including the fact given in the question with the dataset.

I used WebBertSimilarity Model (a pretrained model) which is pretrained with the STS-B dataset to generate the SIA scores. I passed Question + Exact Answer choice as Sentence_1 and Fact for each question as Sentence_2 combined in a dataframe as an input to the model. The model then generate SIA score for each Question + Answer pair.


Instructions to run the code: 

The code to the dataset generation is included in the repo here:
https://colab.research.google.com/drive/1lL0s8TeG2IWSrG22cIA46vjBnXFIPb_s?authuser=1#scrollTo=ueJkcg1fYaYv

The first section consists of all necessary libraries required to run the code.
In the second section I performed the data preprocessing taking the jsonl format of the questions and got the data in the format of ‘Sentence_1, Sentence_2’. 
In the last section I used Web Bert Model and passed the data to generate the SIA scores.

Also I tried with Roberta-Model and BERT-Model which are included in the next sections.The link to these models are present here.
https://drive.google.com/drive/u/1/folders/1-ECcrDRqkziVcq_JiyQXB5ETRTXvdSWD
https://drive.google.com/drive/u/1/folders/1-1bwDIK2rZ0BERCLIGJ1VbsrZxY5-xdI



The combined dataset is at https://github.com/JainSahit/NLP576-SIA
