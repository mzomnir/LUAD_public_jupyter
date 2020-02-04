# Introduction (copied from notebook)

We aim to predict tumor mutational burden (TMB) from the mutation profiles of a selected small set of genes for lung cancer patients. TMB is important in determining prognosis and treatment for patients. Standard practice is to compute it via whole exome sequencing, which costs a great deal of money and time. If TMB could be reliably inferred from the mutation profiles of a small subset of genes, sequencing could be run for that panel only, for significantly less money and time than whole exome sequencing. In this notebook, we probe the predictiveness of one such gene subset.

We are given a csv file, with one row per case, containing columns with mutation counts for each of those genes, along with a label column (overall TMB) and a some bookkeeping columns that will not be used for prediction. The data is from patients who have come through MGH and is fully de-identified (and we provide only a limited sample of it in this notebook). We begin with some exploratory analysis of our dataset and perform cleaning, interpolation, etc. as necessary. Then we proceed to model selection via cross-validation and eventually to training up our final models.

We carry out both classification and regression. The labels in our input dataset are integers, corresponding to tumor mutation counts (i.e. TMB). While we are interested in predicting those counts, we are also interested in the coarser task of predicting whether TMB will be high or low (based on a pathologist-defined TMB threshold of 35 mutations per megabase).

Once we train final classification and regression models, we evaluate the on validation sets provided by MGH. 
