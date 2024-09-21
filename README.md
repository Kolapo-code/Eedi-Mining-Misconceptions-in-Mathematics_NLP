Overview
In this competition, you’ll develop an NLP model driven by ML to accurately predict the affinity between misconceptions and incorrect answers (distractors) in multiple-choice questions. This solution will suggest candidate misconceptions for distractors, making it easier for expert human teachers to tag distractors with misconceptions.

Start

9 days ago
Close
3 months to go
Merger & Entry
Description
A Diagnostic Question is a multiple-choice question with four options: one correct answer and three distractors (incorrect answers). Each distractor is carefully crafted to capture a specific misconception. For example:



If a student selects the distractor "13," they may have the misconception "Carries out operations from left to right regardless of priority order."

Tagging distractors with appropriate misconceptions is essential but time-consuming, and it is difficult to maintain consistency across multiple human labellers. Misconceptions vary significantly in terms of description granularity, and new misconceptions are often discovered as human labellers tag distractors in new topic areas.

Initial efforts to use pre-trained language models have not been successful, likely due to the complexity of the mathematical content in the questions. Therefore, a more efficient and consistent approach is needed to streamline the tagging process and enhance the overall quality.

This competition challenges you to develop a Natural Language Processing (NLP) model driven by Machine Learning (ML) that predicts the affinity between misconceptions and distractors. The goal is to create a model that not only aligns with known misconceptions but also generalizes to new, emerging misconceptions. Such a model would assist human labelers in accurately selecting suitable misconceptions from both existing and newly identified options.

Your work could help improve the understanding and management of misconceptions, enhancing the educational experience for both students and teachers.

Eedi, alongside Vanderbilt University, and together with ​The Learning Agency Lab, an independent nonprofit based in Arizona, have collaborated with Kaggle on this competition.

Acknowledgments
Eedi, Vanderbilt University and the Learning Agency Lab would like to thank the Bill & Melinda Gates Foundation, Schmidt Futures, and Chan Zuckerberg Initiative for their support in making this work possible.







Evaluation
Submissions are evaluated according to the Mean Average Precision @ 25 (MAP@25):

MAP@25=1U∑u=1U∑k=1min(n,25)P(k)×rel(k)
where U
 is the number of observations, P(k)
 is the precision at cutoff k
, n
 is the number predictions submitted per observation, and rel(k)
 is an indicator function equaling 1 if the item at rank k
 is a relevant (correct) label, zero otherwise.

Once a correct label has been scored for an observation, that label is no longer considered relevant for that observation, and additional predictions of that label are skipped in the calculation. For example, if the correct label is A for an observation, the following predictions all score an average precision of 1.0.

[A, B, C, D, E]
[A, A, A, A, A]
[A, B, A, C, A]
There is only one correct label per observation (hence no divisor term in front of the inner summation.)

Submission File
For each QuestionId_Answer row in the test set, you must predict the corresponding MisconceptionId. You can predict up to 25 MisconceptionId values per row, and these should be space-delimited. The file should contain a header and have the following format:

QuestionId_Answer,MisconceptionId
1869_A,1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
1869_B,1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
1869_C,1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
1870_B,1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
...
Timeline
September 12, 2024 - Start Date.

December 5, 2024 - Entry Deadline. You must accept the competition rules before this date in order to compete.

December 5, 2024 - Team Merger Deadline. This is the last day participants may join or merge teams.

December 12, 2024 - Final Submission Deadline.

All deadlines are at 11:59 PM UTC on the corresponding day unless otherwise noted. The competition organizers reserve the right to update the contest timeline if they deem it necessary.

Prizes
Leaderboard Prizes
1st Place - $ 12,000
2nd Place - $ 8,000
3rd Place - $ 5,000
4th Place - $ 5,000
Efficiency Prizes
1st Place - $ 12,000
2nd Place - $ 8,000
3rd Place - $ 5,000
Please see Efficiency Prize Evaluation for details on how the Efficiency Prize will be awarded. Winning a Leaderboard Prize does not preclude you from winning an Efficiency Prize.

Code Requirements


This is a Code Competition
Submissions to this competition must be made through Notebooks. In order for the "Submit" button to be active after a commit, the following conditions must be met:

CPU Notebook <= 9 hours run-time
GPU Notebook <= 9 hours run-time
Internet access disabled
Freely & publicly available external data is allowed, including pre-trained models
Submission file must be named submission.csv
Please see the Code Competition FAQ for more information on how to submit. And review the code debugging doc if you are encountering submission errors.

Efficiency Prize Evaluation
Efficiency Prize
We are hosting a second track that focuses on model efficiency, because highly accurate models are often computationally heavy. Such models have a stronger carbon footprint and frequently prove difficult to utilize in real-world educational contexts. We hope to use these models to help educational organizations, which have limited computational capabilities.

For the Efficiency Prize, we will evaluate submissions on both runtime and predictive performance.

To be eligible for an Efficiency Prize, a submission:

Must be among the submissions selected by a team for the Leaderboard Prize, or else among those submissions automatically selected under the conditions described in the My Submissions tab.
Must be ranked on the Private Leaderboard higher than the sample_submission.csv benchmark.
Must not have a GPU enabled. The Efficiency Prize is CPU Only.
All submissions meeting these conditions will be considered for the Efficiency Prize. A submission may be eligible for both the Leaderboard Prize and the Efficiency Prize.

An Efficiency Prize will be awarded to eligible submissions according to how they are ranked by the following evaluation metric on the private test data. See the Prizes tab for the prize awarded to each rank. More details may be posted via discussion forum updates.

Evaluation Metric
We compute a submission's efficiency score by:
Efficiency=MAP@25Base−maxMAP@25+RuntimeSeconds32400
where MAP@25
 is the submission's score on the main competition metric, Base
 is the score of the "baseline" submission with naive predictions, maxMAP@25
 is the maximum MAP@25
 of all submissions on the Private Leaderboard, and RuntimeSeconds
 is the number of seconds it takes for the submission to be evaluated. The objective is to minimize the efficiency score.

During the training period of the competition, you may see a leaderboard for the public test data in the following notebook, updated daily: Efficiency Leaderboard. After the competition ends and the leaderboard has been verified, we will update this leaderboard with efficiency scores on the private data. While the competition is active, this leaderboard will show only the rank of each team, but not the complete score.

Citation
Jules King, L Burleigh, Simon Woodhead, Panagiota Kon, Perpetual Baffour, Scott Crossley, Walter Reade, Maggie Demkin. (2024). Eedi - Mining Misconceptions in Mathematics. Kaggle. https://kaggle.com/competitions/eedi-mining-misconceptions-in-mathematics
