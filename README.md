# Target Type Identification for Entity-Bearing Queries

This repository provides resources developed within the following paper:

> D. Garigliotti, F. Hasibi and K. Balog. Target Type Identification for Entity-Bearing Queries, In: Proceedings of the 40th International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR '17). ACM. Tokyo, Japan. August 2017. [DOI: 10.1145/3077136.3080659](https://doi.org/10.1145/3077136.3080659)

**You can get the author version of the article [here](https://arxiv.org/abs/1705.06056).**

### Abstract

> *Identifying the target types of entity-bearing queries can help improve retrieval performance as well as the overall search experience. In this work, we address the problem of automatically detecting the target types of a query with respect to a type taxonomy. We propose a supervised learning approach with a rich variety of features. Using a purpose-built test collection, we show that our approach outperforms existing methods by a remarkable margin.* 


### Structure

The repository is structured as follows:

- `data/test_collection/`: TSV-formatted dataset with our test collection, built from crowdsourcing annotations;
- `data/qrels/`: TSV file used for evaluating the rankings. It was obtained by post-processing the test collection (details in the paper);
- `data/ml/`: TSV-formatted machine learning dataset with all the pre-computed features;
- `lib/trec_eval/`: TREC evaluation file (see its Readme);
- `output/`:  all the final TSV run files, containing target types ranked by baseline methods and our proposed approach.


## Test collection

This TSV dataset contains the test collection built through a crowdsourcing annotation experiment (details in the paper).

A special `<dbo:NONETYPE>` label represents a NIL-type annotation.

The columns of this TSV file are self-descriptive.


## Precomputed features for learning to rank target types

Each instance of this TSV-formatted dataset is structured as follows:

- The first and second columns correspond to the query and type;
- The third column is the target to predict;
- The rest of the columns corresponds to the 25 features, in the same order as presented in Table 1 of the paper.


## Results

Results presented in the paper can be obtained by running the TREC evaluation script, indicating the metrics of interest.
E.g., placed on `sigir2017-query_types` directory, the following
```
$ /path/to/trec_eval -c -m ndcg_cut.1,5 data/qrels/qrels-tti-CF-filtered_by_NIL+merged.tsv output/ltr/scores-tti-ltr-rf-n_1000-m_3.tsv
```
evaluates our proposed Learning-to-rank method with the NDCG@1 and NDCG@5 metrics.


## Citation

If you use the resources presented in this repository, please cite:

```
@inproceedings{Garigliotti:2017:TTI,
 author =     {Garigliotti, Dar\'{\i}o and Hasibi, Faegheh and Balog, Krisztian},
 title =      {Target Type Identification for Entity-Bearing Queries},
 booktitle =  {Proceedings of the 40th International ACM SIGIR Conference on Research and Development in Information Retrieval},
 series =     {SIGIR '17},
 year =       {2017},
 pages =      {845--848},
 doi =        {10.1145/3077136.3080659},
 publisher =  {ACM},
}
```


## Contact

Should you have any questions, please contact Darío Garigliotti at dario.garigliotti[AT]uis.no (with [AT] replaced by @).
