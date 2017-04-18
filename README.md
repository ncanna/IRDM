# Information Retrieval and Data Mining Coursework 2017
### Learning to Rank
##### Group 20 - Anna Aleksieva, Hugo Chu, Raluca Georgescu, Julija Bainiaksinaite

This project evaluates a range of Learning to Rank algorithms RankNet, LambdaMART and AdaRank, together with an implementation of ranking as a classification task and proposes an improved approach based on neural networks.

The following are instructions to run each algorithm proposed:

- RankNet

- LambdaMART

- AdaRank
  - Based on the implementation from RankLib, Lemur Project, the code has been run using the following rules from the command line. The user has to be in the same directory with the downloaded RankLib-2.1-patched.jar library file. And has to have access to the MSLR-WEB10K dataset, also from the same current folder.
  ```
  java -jar RankLib-2.1-patched.jar -train MSLR-WEB10K/Fold1/train.txt -test MSLR-WEB10K/Fold1/test.txt -validate MSLR-WEB10K/Fold1/vali.txt -ranker 6 -metric2t NDCG@10 -metric2T ERR@10 -save model_fold1_NDCG.txt -noeq -max 1
  ```
    ```
  java -jar RankLib-2.1-patched.jar -train MSLR-WEB10K/Fold1/train.txt -test MSLR-WEB10K/Fold1/test.txt -validate MSLR-WEB10K/Fold1/vali.txt -ranker 6 -metric2t MAP -metric2T ERR@10 -save model_fold1_MAP.txt -noeq -max 1
  ```
  - Examples refer only to Fold1, but they should be run for all 5 folds and then results would be averaged.
  - In order to obtain the ranking scores, the following command was run (again, command is repeated for all 5 folds and results are averaged):
  ```
  java -jar RankLib-2.1-patched.jar -rank MSLR-WEB10K/Fold1/test.txt -load model_fold1_NDCG.txt -score scores_NDCG.txt
  ```
  - The code for evaluating the rankings against the implemented NDCG@10 and MAP metrics is available in the [AdaRank/AdaRank_Evaluation](https://github.com/RalucaGeorgescu/IRDM/blob/master/AdaRank/AdaRank_Evaluation.ipynb) notebook.

- Ranking as Classification

- Neural Network
