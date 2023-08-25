# rtalk

This repo provides code that accompanies the paper by Ash, Hills and Tuckwell, "The Political Economy of Religious Language: Evidence from the United States Congress"

To generate the data and results of the paper, run the following scripts (in order):

*make_term_frequencies.py*

This script reads in the corpus of congressional speeches and generates speech-level term frequencies (counts of bigrams), god dummies (whether the word "god" is in the speech) and metadata (including speaker characteristics, e.g. political party). As mentioned in Section 3.2 of the paper, we align our pre-processing steps with Gentzkow et al. (2019) as our measure of speech partisanship makes use of partisanship scores of bigrams generated by the authors of that paper. 

*make_speech_partisanship.py*

This script reads in the speech-level term frequencies (counts of bigrams) and partisanship scores of different congressional bigrams from Gentzkow et al. (2019) and generates a partisanship score for each speech by summing the partisanship scores of its bigrams (see formula in section 3.3.1 of the paper).

*combine_speech_level_data.py*

This script reads in the speech-level metadata, god dummies and partisanship scores and combines them into a Stata .dta file.

*analyse_speech_level_data.do*

This script reads the combined speech-level data, creates the time trends of speech partisanship in the "God" speeches and other speeches (Figure 1) and runs the panel regressions which compare speech partisanship with use of the word God (Table 1)).

*make_partisan_bigram_dummies.py*

This script reads in partisanship scores of different congressional bigrams from Gentzkow et al. (2020), identifies the 1000 most Republican and Democrat-leaning bigrams over the time-span of the sample and then generates speech-level dummies for each of these bigrams which will be used in Stata to estimate the probabilities (and their standard errors) of the bigrams being spoken in speeches where God has and has not been evoked (which will eventually be used in Figures 2/3).

*estimate_partisan_bigram_probs_using_dummies.do*

This script reads in speech-level dummies for the 1000 most Republican/Democrat-leaning bigrams and estimates the probabilities (as means of speech-level dummies) and standard errors of these bigrams being spoken by Republicans/Democrats in speeches that do and do not evoke God.

*identify_partisan_bigram_examples_by_topic.py*

This script reads in probabilities and standard errors for the 1000 most Republican/Democrat-leaning bigrams in speeches that do and do not evoke God, calculates
confidence intervals and then identifies examples of partisan bigrams that have a significantly higher probability of being spoken when God has been evoked and groups these into topics (for Figures 2 and 3).

*visualise_partisan_bigram_examples_by_topic.py*

This script reads in examples of highly-partisan bigrams that have a significantly higher probability of being spoken when God has been evoked, grouped by topic for each party, and generates bar graphs that compares these bigrams' probabilities / confidence intervals in God speeches and non-God speeches by Republicans (Figure 2) and Democrats (Figure 3).
