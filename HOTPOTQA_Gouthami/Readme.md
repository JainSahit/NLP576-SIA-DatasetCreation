
Dataset:  HOTPOT QA Dataset

First Phase:
I  have  created  the following  dataframe from the HOTPOT QA dataset,
 
Question-id: unique id for each question
Passage-id: candidate passage id of  each question
Question: question+exact answer
Passage: candidate passage 
Sentence:  each sentence from candidate passage
Passage_length:  length of the candidate  passage, required for calculating the average SIA score for the  candidate  passage
Sia_score - sia score between question and each sentence of the candidate passage

Second phase:
I have computed the average SIA  score for each candidate passage by representing them in the following column format.

Question: question+exact answer
Sentence: candidate passage 
sia_score: average SIA score  of the candidate passage

Tasks Performed:
I have chosen HOTPOT QA, handled data preprocessing cleaning, data parsing, data preprocessing for HOTPOT QA.  Converted the  input json file to dataframe and from dataframe to .csv file. The details, step by step procedure is explained in Automated  Data  Creation Report available at 
https://github.com/JainSahit/NLP576-SIA/tree/main/HOTPOTQA_Gouthami


Consider the following sample data:

[{"supporting_facts": [["Arthur's Magazine", 0], ["First for Women", 0]], 
"level": "medium", 
"question": "Which magazine was started first Arthur's Magazine or First for Women?", 
"context": [   ["Radio City (Indian radio station)", ["Radio City is India's first private FM radio station and was started on 3 July 2001.", " It broadcasts on 91.1 (earlier 91.0 in most cities) megahertz from Mumbai (where it was started in 2004), Bengaluru (started first in 2001), Lucknow and New Delhi (since 2003).", " It plays Hindi, English and regional songs.", " It was launched in Hyderabad in March 2006, in Chennai on 7 July 2006 and in Visakhapatnam October 2007.", " Radio City recently forayed into New Media in May 2008 with the launch of a music portal - PlanetRadiocity.com that offers music related news, videos, songs, and other music-related features.", " The Radio station currently plays a mix of Hindi and Regional music.", " Abraham Thomas is the CEO of the company."]  ],
………………..
……………….
"answer": "Arthur's Magazine", 
"_id": "5a7a06935542990198eaf050", 
"type": "comparison"}

From this, I have extracted question, answer, set of candidate passages from the context, again from the context, i have extracted sentences and computed STS scores between <Q+A> and the every <sentence> of each candidate passage , finally   calculated the  average sia score for each  candidate passage in the context. 

Instructions to run the  code:

All the  executions are aligned sequentially  in jupyter  notebook
1.	Run the  Necessary Installations section
2.	Run the data preprocessing  section
3.	Run  the scores generation section
4.	 Run the  data  processing section
5.	Please ignore the  commented code
User Controls:
•	Look for the variable ‘FOLDER’, update the value to the main folder path where the input data .json file exists
•	Change the variables ‘start’ and ‘end’ to control data size
•	The output csv files will be generated in the same ‘FOLDER’


Analysis and  Experiments:

Models:
1) https://github.com/AndriyMulyar/semantic-text-similarity/tree/master/semantic_text_similarity 
2) 'Distilbert-base-nli-mean-tokens'  model
https://www.sbert.net/docs/usage/semantic_textual_similarity.html
https://github.com/UKPLab/sentence-transformers

3) Also uploaded train, test, dev data and  the  Bert, Roberta models used while experimenting and training is available at
https://drive.google.com/drive/folders/17jukmmppKi_9HhU8ehICbpbNPDkSL8Oc?usp=sharing

and the  experimental code is commented
The combined dataset is at https://github.com/JainSahit/NLP576-SIA

References for  HOTPOTQA
Kwiatkowski, Tom, Jennimaria Palomaki, Olivia Redfield, Michael Collins, Ankur Parikh, Chris Alberti, Danielle Epstein et al. "Natural questions: a benchmark for question answering research." Transactions of the Association for Computational Linguistics 7 (2019): 453-466.

 

















