# Target Type Identification for Entity-Bearing Queries

This repository provides resources developed within the following paper:

> D. Garigliotti, F. Hasibi and K. Balog. Target Type Identification for Entity-Bearing Queries, In SIGIR'17, August 2017.

These resources allow to reproduce the results presented in the Target Type Identification paper.

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


## Contact

Should you have any questions, please contact Darío Garigliotti at dario.garigliotti[AT]uis.no (with [AT] replaced by @).
