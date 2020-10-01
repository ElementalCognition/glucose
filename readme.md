# GLUCOSE
GLUCOSE: GeneraLized and COntextualized Story Explanations, is a novel conceptual framework and dataset for commonsense reasoning. Given a short story and a sentence X in the story, GLUCOSE captures ten dimensions of causal explanation related to X. These dimensions, inspired by human cognitive psychology, cover often-implicit causes and effects of X, including events, location, possession, and other attributes. 

This repository contains links to the full GLUCOSE data and GLUCOSE-trained models, as outlined in the main GLUCOSE paper. The dataset and models are released under [Creative Commons Attribution-NonCommercial 4.0 International Public License](https://creativecommons.org/licenses/by-nc/4.0/legalcode)


# Models Pretrained on the GLUCOSE Data
This repository contains links to the top best performing models, outlined in the paper. Click on the links in the table below to download our pre-trained models or go to their respective directories for scripts and data to replicate our results on the test set.

|Model Type | Pre-trained Models Only | Uses | Scripts | Data | 
|:----------|:---------:|:------:|:-----------:|:-------:|
| Enc-Dec   |   [GLUCOSE-trained T5](https://comoltd.sharepoint.com/:u:/s/Glucose/Ef2aqIM5YEdFr4aRFDZ-HR0BkMSpNiAHxu6Nz3TnDavHAA?e=9Bbdgg)        | [T5](https://github.com/ElementalCognition/text-to-text-transfer-transformer) | [T5 Scripts](https://github.com/ElementalCognition/glucose/tree/master/t5_scripts) | [T5 Data](https://github.com/ElementalCognition/glucose/tree/master/t5_data) | 
|Full-LM    |   [GLUCOSE-trained GPT-2](https://comoltd.sharepoint.com/:u:/s/Glucose/EXeUKKWpZ01Cor0N41AmVsgB9mVGlUXhYCMbbNhJNdcYTw?e=sbg8zo)       | [GPT-2](https://github.com/openai/gpt-2) |  | [GPT-2 Data](https://github.com/ElementalCognition/glucose/tree/master/gpt2_data) |

The Enc-Dec model finetunes the pretrained T5 model of Raffel et al. 2019 (under Apache 2.0 license) on the GLUCOSE dataset. We provide a link to our fork of the T5 repository in order to provide a state of the project that is compatible with our scripts.

The Full-LM finetunes the pretrained [GPT-2](https://openai.com/blog/better-language-models/) model (under the Modified MIT License). 

The evaluation results for each of the GLUCOSE models can be found below. For details on the evaluation please refer to the paper. 

Human scores were on a scale from 0-3 where a rating of 0 = Incorrect, 1 = Mostly incorrect, 2 = Mostly correct, 3 = Correct. Workers rated the output of the modesl on each dimension as well as the output of other workers on the Mturk task.

|Model |Level | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10|
|:-------|:---|:---:|:---:|:---:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|
|Full-LM | Spec | 1.8 | 2.0 | 1.7 | 2.1 | 1.6 | 2.0 | 2.2 | 2.0 | 2.2 | 2.1 |
|Full-LM |  Gen | 1.6 | 1.8 | 1.8 | 1.9 | 1.1 | 1.6 | 2.1 | 1.9 | 2.1 | 1.5 |
|Enc-Dec | Spec | **2.7** | **2.6** | **2.5** | **2.7** | **2.2** | **2.7** | **2.7** | **2.6** | **2.8** | **2.5** |
|Enc-Dec | Gen | **2.3** | **2.4** | **2.3** | **2.5** | **1.9** | **2.3** | **2.5** | **2.4** | **2.7** | **1.7** |
|Human|Spec| 2.8 | 2.7 | 2.8 | 2.9 | 2.5 | 2.8 | 2.8 | 2.8  | 2.9 | 3.0 |
|Human|Gen| 2.5 | 2.6 | 2.4 | 2.6 | 2.4 | 2.6 | 2.6 | 2.6 | 2.6 | 2.7 | 

## BLEU Scores (out of 100)

|Model |Level | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10|
|:-------|:---|:---:|:---:|:---:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|
|Full-LM | Spec | 54.7 | 51.0 | 50.5 | 66.2 | 32.7 | 55.3 | 64.4 | 58.8 | 73.4 | 67.0 |
|Full-LM | Gen | 56.4 | 57.5 | 59.6 | 65.8 | 53.7 | 55.8 | 62.7 | 59.0 | 67.7 | 56.2 |
|Enc-Dec | Spec |**72.5** | **73.8** | **70.5** | **81.1** | **71.7** | **73.9** | **79.3** | **80.2** | **86.6** | **66.9** |
|Enc-Dec | Gen | **66.4** | **68.5** | **69.8** | **76.8** | **68.6** | **67.6** | **73.0** | **77.0** | **86.8** | **57.5** |

## Replicating Model Results
To replicate the results in the tables above using our pretraied models, data, and scripts, go to the folder linked under _scripts_ above and follow the instructions. 

# The GLUCOSE Data 
The GLUCOSE dataset can be downloaded [here](https://comoltd.sharepoint.com/:u:/s/Glucose/Ebdnei4W83NFhOVMLF0KmBEB7gUOiAd3n8YHVtI4wPlK1A?e=dg3Kqw). This download contains the crowd worker responses to the annotation task, as outlined in the main paper. This dataset can be used for any training and validation purposes. Note that you should download the zipped file rather than opening the folder and downloading all individual csv files, to make sure the download has been successful.

## Data Format
The data is in the form of a csv file with 71,979 rows and 47 columns.   
There are a total of 337,636 pair of GLUCOSE rules annotated. 

Each rule is described by a quality rating, which is based on the worker's performance on the row of responses. We assume about 10% errors on the rating numbers. 

All the data, regardless of quality rating, were collected from workers who passed challenging qualification tasks and were subsequently trained for improved quality on the task.
For details on how the ratings were created and determined, see the [data quality management document](https://github.com/ElementalCognition/glucose/blob/master/data_collection_quality.pdf).

The quality ratings are:
3 = Highest quality. Rules display an accurate level of generalization in the general rules. Rules make sense and are appropriate for the sentence, given the context. 
2 = Mid-quality raing. These are still very good rules that have a good balance of generality, but a higher percetage in this set may be overly specific, use attribute clauses less proficiently, or not be as conceptually concise
3 = Lower-quality rating. These rules are still useable, but a higher percentage of them have, in addition to the issues in the 2-level ratings, highly specific general rules and some misunderstanding of how to use attribute clauses. 

Each csv file has 13 columns. The data in the columns is described below. The column label is given, along with its index, the the header for that column, a description of the column contents, and example of what occurs in the column. Columns J-M say "escaped" when the annotator did not supply a response. 

A; header: unique_id; description: a randomly generated alphanumeric sequence for a given story with the sentence index appended at the end after two underscores; example: cbee2b5a-f2f9-4bca-9630-6825b1e36c13__0

B; header: story_id; description: a randomly generated alphanumeric sequence for a given story; example: e56c7c3e-4660-40fb-80d0-052d566d676a

C; header: assignment_id; description: a ramdomly generated alphnumeric sequence for a given assignment; example: e56c7c3e-4660-40fb-80d0-052d566d676a

D; header: worker_id; description: each worker has a unique identificaiton number (de-identified from actual AMT worker ids); example: 1

E; header: submission_time_normalized: The data of submission for an assignment YYYYMMDD; example: 20190930

F; header: worker_quality_assessment; description: rating for the worker on the assignment in the row; example: 2

G; header: selected_sentence_index; description: the index of a given sentence in a story; example: 0

H; header: story; description: contains the full text of the ROC story that was used for the HIT. Each sentence is separated by "\*\*\*"; example: The school football game was last weekend.\*\*\*\*The team has been very good this year.\*\*\*\*They have won a lot of games.\*\*\*\*A lot of people showed up to watch.\*\*\*\*They won by a ton of points.

I; selected_sentence; description: text of the sentence that the HIT was about.; example: The school football game was last weekend.

J; header: (dimension n)\_specificNL; description: A specific statement about the story in natural language format; example: The school  has  a football team  >Causes/Enables> The football game  was last weekend

K; header: (dimension n)\_specificStructured; description: A specific statement about the story in a structured format; example: \{The school \}\_\[subject\] \{has \}\_\[verb\] \{a football team \}\_\[object1\] >Causes/Enables> \{The football game \}\_\[subject\] \{was last weekend \}\_\[verb\]

L; header: (dimension n)\_generalNL; description: A general rule derived from the specific statement in natural langauge format; example: Somewhere\_A (that is a school ) has  Something\_A (that is a sports team ) >Causes/Enables> The game  was last weekend

M; header: (dimension n)\_generalStructured: A general rule derived from the specific statement in a structured format; example: {Somewhere\_A \|\|that is a school \|\|\}\_\[subject\] \{has \}\_\[verb\] \{Something\_A \|\|that is a sports team \|\|\}\_\[object1\] >Causes/Enables> \{The game \}\_\[subject\] \{was last weekend \}\_\[verb\]

# Citation
For any uses please cite the main GLUCOSE [paper](https://arxiv.org/abs/2009.07758).
```
@misc{mostafazadeh2020glucose,
      title={GLUCOSE: GeneraLized and COntextualized Story Explanations}, 
      author={Nasrin Mostafazadeh and Aditya Kalyanpur and Lori Moon and David Buchanan and Lauren Berkowitz and Or Biran and Jennifer Chu-Carroll},
      year={2020},
      eprint={2009.07758},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

# Any Issues?
For any questions or issues about this repository, please write to glucose@elementalcognition.com
