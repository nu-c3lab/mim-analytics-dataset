# Mim Analytics Dataset

This is a repository containing the data and evaluation scripts for the Mim Analytics Dataset. This open-domain question answering dataset
consists of 432 questions requiring 8 distinct types of reasoning: addition, subtraction, comparison, Boolean equality, existence, 
set intersection, set difference, and multi-hop retrieval. 

For more details, please see our paper: [Generation of Compositional Programs for Open-Domain Question Answering]().

### Requirements

This repository requires Python 3 and the Num_Parse library. You can install necessary libraries using
the `requirements.txt` file in this repository:

```commandline
pip install -r requirements.txt
```

### JSON Data Format
The top level data structure is a list which consists of multiple question entries. Each entry is a dict containing the following properties:
- `id`: A unique identifier for the entry
- `question`: The question string 
- `answer`: A list of valid answer strings
- `answer_type`: The ontological type of the answer. Can be one of `numeric`, `boolean`, `date`,`entity`
- `domain`: The domain this question belongs to. Can be one of `science`, `literature`, `film`, `music`, `history`, `sports`, `technology`, `politics`, `geography`
- `wiki_urls`: A list of Wikipedia urls that were used to derive the answer for this question
- `support_n`: A supporting answer needed to derive the final answer to the question. Note `n` can have the value 1-4, depending on how many supporting values were needed to answer the question.
- `ent_support_n`: The entity associated with the `support_n` value. Again, `n` can have the value 1-4, depending on how many supporting values were needed to answer the question.
- `num_hops`: The number of reasoning hops required to answer this question. Only used for `bridge` questions.

### Prediction Format

Predictions are expected to be in JSON format, where the top level data structure is a dict. This dict should have
an `answers` key that maps to a dict where the keys are question ids and the corresponding value is the answer string for that question.

An example is provided in `example_preds.json`

### Evaluation

To run the evaluation, you can use the following command:

```commandline
python score_answers.py path/to/mim_analytics_dataset.json /path/to/preds.json <threshold>
```

where `<threshold>` is a float denoting how tight the threshold match score should be.

### Citation

If you use this dataset as part of your research, please consider citing our paper:
<final citation TBD>

### License
This file is part of Mim.
Mim is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software Foundation,
either version 3 of the License, or (at your option) any later version.
Mim is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY;
without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details.
You should have received a copy of the GNU General Public License along with Mim.
If not, see <https://www.gnu.org/licenses/>.
