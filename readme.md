# GLUCOSE
GLUCOSE: GeneraLized and COntextualized Story Explanations, is a novel conceptual framework and dataset for commonsense reasoning. 

This work is available under [Creative Commons Attribution-NonCommercial 4.0 International Public License](https://creativecommons.org/licenses/by-nc/4.0/legalcode)

Any use must cite this [paper](https://arxiv.org/abs/2009.07758).

For questions about GLUCOSE or using this repository, please write to glucose@elementalcognition.com


## Models Pretrained on GLUCOSE Data
Click on the links in the table below to download our pre-trained models or go to their respective directories for scripts and data to replicate our results on the test set.

|Model Type | Pre-trained Models Only | Uses | Scripts | Data | 
|:----------|:---------:|:------:|:-----------:|:-------:|
| Enc-Dec   |   [GLUCOSE-trained T5](https://comoltd.sharepoint.com/:u:/s/Glucose/Ef2aqIM5YEdFr4aRFDZ-HR0BkMSpNiAHxu6Nz3TnDavHAA?e=9Bbdgg)        | [T5](https://github.com/ElementalCognition/text-to-text-transfer-transformer) | [T5 Scripts](https://github.com/ElementalCognition/glucose/tree/master/t5_scripts) | [T5 Data](https://github.com/ElementalCognition/glucose/tree/master/t5_data) | 
|Full-LM    |   [GLUCOSE-trained GPT-2](https://comoltd.sharepoint.com/:u:/s/Glucose/EXeUKKWpZ01Cor0N41AmVsgB9mVGlUXhYCMbbNhJNdcYTw?e=sbg8zo)       | [GPT-2](https://github.com/openai/gpt-2) |  | [GPT-2 Data](https://github.com/ElementalCognition/glucose/tree/master/gpt2_data) |

The Enc-Dec model uses the T5 model of Raffel et al. 2019 (Colin Raffel, Noam Shazeer, Adam Roberts, Katherine
Lee, Sharan Narang, Michael Matena, Yanqi Zhou,Wei Li, and Peter J. Liu. 2019.  Exploring the limits
of transfer learning with a unified text-to-text transformer. arXiv e-prints), used under Apache 2.0 license. Our pretrained model adds GLUCOSE data to the T5 models. We provide a link to our fork of the T5 repository in order to provide a state of the project that is compatible with our scripts.

The Full-LM uses [GPT-2](https://openai.com/blog/better-language-models/), under the Modified MIT License. We add GLUCOSE data to the GPT-2 model. 

The evaluation results for each of the GLUCOSE models is below. We tested the models that were enhanced with GLUCOSE training data. 

Human scores were on a scale from 0-3 where a rating of 0 = Incorrect, 1 = Mostly incorrect, 2 = Mostly correct, 3 = Correct. Workers rated the output of the modesl on each dimension as well as the output of other workers on the Mturk task.

|Model |Level | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10|
|:-------|:---|:---:|:---:|:---:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|
|Full-LM | Spec | 1.8 | 2.0 | 1.7 | 2.1 | 1.6 | 2.0 | 2.2 | 2.0 | 2.2 | 2.1 |
|Full-LM |  Gen | 1.6 | 1.8 | 1.8 | 1.9 | 1.1 | 1.6 | 2.1 | 1.9 | 2.1 | 1.5 |
|Enc-Dec | Spec | **2.7** | **2.6** | **2.5** | **2.7** | **2.2** | **2.7** | **2.7** | **2.6** | **2.8** | **2.5** |
|Enc-Dec | Gen | **2.3** | **2.4** | **2.3** | **2.5** | **1.9** | **2.3** | **2.5** | **2.4** | **2.7** | **1.7** |
|Human|Spec| 2.8 | 2.7 | 2.8 | 2.9 | 2.5 | 2.8 | 2.8 | 2.8  | 2.9 | 3.0 |
|Human|Gen| 2.5 | 2.6 | 2.4 | 2.6 | 2.4 | 2.6 | 2.6 | 2.6 | 2.6 | 2.7 | 

### BLEU Scores (out of 100)

|Model |Level | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10|
|:-------|:---|:---:|:---:|:---:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|
|Full-LM | Spec | 54.7 | 51.0 | 50.5 | 66.2 | 32.7 | 55.3 | 64.4 | 58.8 | 73.4 | 67.0 |
|Full-LM | Gen | 56.4 | 57.5 | 59.6 | 65.8 | 53.7 | 55.8 | 62.7 | 59.0 | 67.7 | 56.2 |
|Enc-Dec | Spec |**72.5** | **73.8** | **70.5** | **81.1** | **71.7** | **73.9** | **79.3** | **80.2** | **86.6** | **66.9** |
|Enc-Dec | Gen | **66.4** | **68.5** | **69.8** | **76.8** | **68.6** | **67.6** | **73.0** | **77.0** | **86.8** | **57.5** |

## Replicating Results
To replicate the results in the tables above using our pretraied models, data, and scripts, go to the folder linked under _scripts_ above and follow the instructions. 

## GLUCOSE Data Only
The structured data from crowd workers is available [here](https://comoltd.sharepoint.com/:u:/s/Glucose/EU0IJE1sT9JCgOe7YU60x-0BI24M7E9BFfknfSq-GwAnHA?e=LhGsp9)

This download contains the crowd worker responses to the GLUCOSE task. These data can be used to train you own models for learning common sense reasoning about stories.

The data is in the form of a csv file with 71,979 rows and 47 columns.   

There are 337,636 rules filled in, each being a mini-theory with both a specific statment and a general rule.

Each rule is described by a quality rating, which is based on the worker's performance on the row of responses. We assume about 10% errors on the rating numbers. 

All the data, regardless of quality rating, were collected from workers who passed challenging qualification tasks and were subsequently trained for improved quality on the task.
For details on how the ratings were created and determined, see the [data quality management document](https://github.com/ElementalCognition/glucose/blob/master/data_collection_quality.pdf).

The quality ratings are:
3 = Highest quality. Rules display an accurate level of generalization in the general rules. Rules make sense and are appropriate for the sentence, given the context. 
2 = Mid-quality raing. These are still very good rules that have a good balance of generality, but a higher percetage in this set may be overly specific, use attribute clauses less proficiently, or not be as conceptually concise
3 = Lower-quality rating. These rules are still useable, but a higher percentage of them have, in addition to the issues in the 2-level ratings, highly specific general rules and some misunderstanding of how to use attribute clauses. 

### Data Format in GLUCOSE Crowd Worker Data
The data in the csv has 47 columns. The data in the columns is described below. The column label is given, along with its index, the the header for that column, a description of the column contents, and example of what occurs in the column, and an example of how the data can be used. 

A; header: unique_id; description: a randomly generated alphanumeric sequence for a given story with the sentence index appended at the end after two underscores; example: cbee2b5a-f2f9-4bca-9630-6825b1e36c13__0; uses: find all user responses to a particular sentence in a given story

B; header: selected_sentence_index; description: the index of a given sentence in a story; example: 0; uses: how users respond to the first sentence versus the last, which index of a story contains the most conceptual information (all ROC stories are the same length)

C; header: worker_id; description: each worker has a unique identificaiton number; example: 1; uses: filter data by worker

D; header: worker_quality_assessment; description: rating for the worker on the assignment in the row; example: 2; uses: divide data by work quality

E; header: story; description: contains the full text of the ROC story that was used for the HIT. Each sentence is separated by "\*\*\*"; example: The school football game was last weekend.\*\*\*\*The team has been very good this year.\*\*\*\*They have won a lot of games.\*\*\*\*A lot of people showed up to watch.\*\*\*\*They won by a ton of points.; uses: stories can be used to filter based on vocabulary or topics

F-AS; header: 1_specificNL - 10_generalStructured; description: For each of the ten dimensions, there are four columns. The columns occur in this order "n_specificNL, n_specificStructured, n_generalNL, n_generalStructured", where n is in 1-10. The specific columns give the specific statements from the story. The general statements give the corresponding generalization. The NL columns are formated in natural language, whereas the structured columns contain indications of the slots used to fill in the data.; example: The school  has  a football team  >Causes/Enables> The football game  was last weekend 	\{The school \}\_\[subject\] \{has \}\_\[verb\] \{a football team \}\_\[object1\] >Causes/Enables> \{The football game \}\_\[subject\] \{was last weekend \}\_\[verb\]	Somewhere\_A (that is a school ) has  Something\_A (that is a sports team ) >Causes/Enables> The game  was last weekend 	{Somewhere\_A \|\|that is a school \|\|\}\_\[subject\] \{has \}\_\[verb\] \{Something\_A \|\|that is a sports team \|\|\}\_\[object1\] >Causes/Enables> \{The game \}\_\[subject\] \{was last weekend \}\_\[verb\]; uses: This is the primary data collected. It provides the common sense knowledge about the related stories and those general rules about the world derived from the specific statements

AT; header: number_filled_in; description: the number of dimensions that the worker filled in. Each set of general and specific, structured and unstructured, counts as one.; example: 3; uses: averaging how many dimensions workers supplied

AU; selected_sentence; description: text of the sentence that the HIT was about.; example: The school football game was last weekend.; uses: analysis of the text of particular sentences (e.g., relative to the containing story)
