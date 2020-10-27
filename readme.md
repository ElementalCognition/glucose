# GLUCOSE
GLUCOSE: GeneraLized and COntextualized Story Explanations, is a novel conceptual framework and dataset for commonsense reasoning. Given a short story and a sentence X in the story, GLUCOSE captures ten dimensions of causal explanation related to X. These dimensions, inspired by human cognitive psychology, cover often-implicit causes and effects of X, including events, location, possession, and other attributes. 

This repository contains links to the full GLUCOSE data and GLUCOSE-trained models, as outlined in the main GLUCOSE paper. The dataset and models are released under [Creative Commons Attribution-NonCommercial 4.0 International Public License](https://creativecommons.org/licenses/by-nc/4.0/legalcode)


# Models Pretrained on the GLUCOSE Data
This repository contains links to the best performing models, as outlined in the paper. Click on the links in the table below to download our pre-trained models or go to their respective directories for scripts and data to replicate our results on the test set.

|Model Name | Fine-tuned Model | Pre-trained Model | Scripts | Data | 
|:----------|:---------:|:------:|:-----------:|:-------:|
| Enc-Dec   |   [GLUCOSE-trained T5](https://comoltd.sharepoint.com/:u:/s/Glucose/Ef2aqIM5YEdFr4aRFDZ-HR0BkMSpNiAHxu6Nz3TnDavHAA?e=9Bbdgg)        | [T5](https://github.com/ElementalCognition/text-to-text-transfer-transformer) | [T5 Scripts](https://github.com/ElementalCognition/glucose/tree/master/t5_scripts) | [T5 Data](https://github.com/ElementalCognition/glucose/tree/master/t5_data) | 
|Full-LM    |   [GLUCOSE-trained GPT-2](https://comoltd.sharepoint.com/:u:/s/Glucose/EXeUKKWpZ01Cor0N41AmVsgB9mVGlUXhYCMbbNhJNdcYTw?e=sbg8zo)       | [GPT-2](https://github.com/openai/gpt-2) |  | [GPT-2 Data](https://github.com/ElementalCognition/glucose/tree/master/gpt2_data) |

Note that the Enc-Dec model finetunes the pretrained T5 model of Raffel et al. 2019 (under Apache 2.0 license) on the GLUCOSE dataset. We provide a link to our fork of the T5 repository in order to provide a state of the project that is compatible with our scripts. The Full-LM finetunes the pretrained [GPT-2](https://openai.com/blog/better-language-models/) model (under the Modified MIT License). 

The evaluation results for each of the GLUCOSE models, as presented in the paper, can be found below. For details on the evaluation and metrics please refer to the paper. 

## Human Evaluation
Human scores were on a scale from 0-3 where a rating of 0 = Incorrect, 1 = Mostly incorrect, 2 = Mostly correct, 3 = Correct. 

|Model |Level | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10|
|:-------|:---|:---:|:---:|:---:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|
|Full-LM | Spec | 1.8 | 2.0 | 1.7 | 2.1 | 1.6 | 2.0 | 2.2 | 2.0 | 2.2 | 2.1 |
|Full-LM |  Gen | 1.6 | 1.8 | 1.8 | 1.9 | 1.1 | 1.6 | 2.1 | 1.9 | 2.1 | 1.5 |
|Enc-Dec | Spec | **2.7** | **2.6** | **2.5** | **2.7** | **2.2** | **2.7** | **2.7** | **2.6** | **2.8** | **2.5** |
|Enc-Dec | Gen | **2.3** | **2.4** | **2.3** | **2.5** | **1.9** | **2.3** | **2.5** | **2.4** | **2.7** | **1.7** |
|Human|Spec| 2.8 | 2.7 | 2.8 | 2.9 | 2.5 | 2.8 | 2.8 | 2.8  | 2.9 | 3.0 |
|Human|Gen| 2.5 | 2.6 | 2.4 | 2.6 | 2.4 | 2.6 | 2.6 | 2.6 | 2.6 | 2.7 | 

## Automatic Evaluation
BLEU Scores (out of 100)
|Model |Level | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10|
|:-------|:---|:---:|:---:|:---:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|
|Full-LM | Spec | 54.7 | 51.0 | 50.5 | 66.2 | 32.7 | 55.3 | 64.4 | 58.8 | 73.4 | 67.0 |
|Full-LM | Gen | 56.4 | 57.5 | 59.6 | 65.8 | 53.7 | 55.8 | 62.7 | 59.0 | 67.7 | 56.2 |
|Enc-Dec | Spec |**72.5** | **73.8** | **70.5** | **81.1** | **71.7** | **73.9** | **79.3** | **80.2** | **86.6** | **66.9** |
|Enc-Dec | Gen | **66.4** | **68.5** | **69.8** | **76.8** | **68.6** | **67.6** | **73.0** | **77.0** | **86.8** | **57.5** |


# The GLUCOSE Data 
The GLUCOSE dataset can be downloaded [here](https://tinyurl.com/yyeo92pt). This download contains the crowd worker responses to the annotation task, as outlined in the main paper. This dataset can be used for any training and validation purposes. Note that you should download the zipped file rather than opening the folder and downloading all individual csv files, to make sure the download has been successful.

## Data Format
The data is in the form of a csv file with 65,521 rows and 49 columns. There are more than 670K (335K pair) of GLUCOSE annotations in the dataset. 

### Rows
Each annotation in the dataset comes with a quality rating, which is based on the worker's performance on the corresponding row of response. We recommend using the quality rating per row for filtering the dataset to be more approporiate for your various training or validation purposes. We assume about 10% errors on the calculation of the quality ratings. Note that all the data, regardless of quality rating, were collected from workers who passed challenging qualification tasks and were subsequently trained for improved quality on the task. For details on how the ratings were created and determined, see the [data quality management document](https://github.com/ElementalCognition/glucose/blob/master/data_collection_quality.pdf).

The quality ratings are as follows:
3 = Highest quality. General rules display an accurate level of generalization in the general rules. Rules make sense and are appropriate for the sentence, given the context. 
2 = Mid-quality raing. These are still very good general rules that have a good balance of generality, but a higher percetage in this set may be overly specific, use attribute clauses less proficiently, or not be as conceptually concise
1 = Lower-quality rating. These general rules are still useable, but a higher percentage of them have, in addition to the issues in the 2-level ratings, highly specific general rules and some misunderstanding of how to use attribute clauses. 

Note that the quality of the specific statements has been high on average, hence, the decision on the quality rating has been mainly based on the performance of the worker in generating the general rules in the row.

### Columns
Below, you can see a column label, along with its index, the the header for that column, a description of the column contents, and example of what occurs in the column, and an example of how the data can be used. 

A; header: experiment_id; description: a randomly generated alphanumeric sequence for a given story with the sentence index appended at the end after two underscores; example: cbee2b5a-f2f9-4bca-9630-6825b1e36c13__0

B; header: story_id; description: a random alphanumeric identifier for the story; example: e56c7c3e-4660-40fb-80d0-052d566d676a

C; header: worker_id; description: each worker has a unique identificaiton number; example: 21

D; header; submission_time_normalized: the time of submission in the format YYYYMMDD; example: 20200115

E; header: worker_quality_assessment; description: rating for the worker on the assignment in the row; example: 2

F; header: selected_sentence_index; description: the index of a given sentence in a story; example: 0

G; header: story; description: contains the full text of the ROC story that was used for the HIT. example: It was bedtime at our house. Two of the three kids hit the pillow and fall asleep. The third is a trouble maker. For two hours he continues to get out of bed and want to play. Finally he becomes tired and falls asleep.

H; header: selected_sentence; description: the sentence from the story that is being annotated; example: It was bedtime at our house.

I-AV; header: 1_specificNL - 10_generalStructured; description: For each of the ten dimensions, there are four columns. The columns occur in this order "n_specificNL, n_specificStructured, n_generalNL, n_generalStructured", where n is in 1-10. The specific columns give the specific statements from the story. The general statements give the corresponding generalization. The NL columns are formated in natural language, whereas the structured columns contain indications of the slots used to fill in the data.; example: The school  has  a football team  >Causes/Enables> The football game  was last weekend 	\{The school \}\_\[subject\] \{has \}\_\[verb\] \{a football team \}\_\[object1\] >Causes/Enables> \{The football game \}\_\[subject\] \{was last weekend \}\_\[verb\]	Somewhere\_A (that is a school ) has  Something\_A (that is a sports team ) >Causes/Enables> The game  was last weekend 	{Somewhere\_A \|\|that is a school \|\|\}\_\[subject\] \{has \}\_\[verb\] \{Something\_A \|\|that is a sports team \|\|\}\_\[object1\] >Causes/Enables> \{The game \}\_\[subject\] \{was last weekend \}\_\[verb\]; uses: This is the primary data collected. It provides the common sense knowledge about the related stories and those general rules about the world derived from the specific statements

AW; header: number_filled_in; description: number of dimensions filled in for the assignment; example: 4

# Citation
For any uses please cite the main GLUCOSE [paper](https://arxiv.org/abs/2009.07758).
```
@inproceedings{mostafazadeh2020glucose,
      title={GLUCOSE: GeneraLized and COntextualized Story Explanations}, 
      author={Nasrin Mostafazadeh and Aditya Kalyanpur and Lori Moon and David Buchanan and Lauren Berkowitz and Or Biran and Jennifer Chu-Carroll},
      year={2020},
      booktitle={The Conference on Empirical Methods in Natural Language Processing},
      publisher={Association for Computational Linguistics}
}
```

# Any Issues?
For any questions or issues about this repository, please write to glucose@elementalcognition.com
