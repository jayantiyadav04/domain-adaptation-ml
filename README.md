# Domain adaptation in classical machine learning

Can unlabelled data from a new domain help a classifier trained under different conditions? This study compares source-only training, importance weighting and correlation alignment (CORAL) for Logistic Regression, linear SVM and Random Forest.

The experiments use gas sensor batches collected at different times, smartphone activity measurements from different volunteers, and Amazon reviews from different product categories. The outcomes are target accuracy, macro F1 and computational time.

[Open the project notebook in Google Colab](https://colab.research.google.com/github/jayantiyadav04/domain-adaptation-ml/blob/main/domain_adaption.ipynb). Use a hosted Python CPU runtime and save an editable copy in Google Drive. The notebook defines the research question, planned comparisons and outcome interpretation. The [scope summary](reports/scope.md) describes the proposed design; experimental results are pending.

The [literature review](reports/literature.md) compares ten primary papers and explains the study's bounded research gap, including differences in target supervision, data splits and representations.
