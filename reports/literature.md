# Related work and research gap

## Related work: evidence matrix

The ten papers below cover weighting foundations, domain-adaptation theory, classical CORAL, transfer evaluation and the three application areas. Each evidence statement refers to its cited paper and original protocol; it is not an outcome of the present study. Section, table and figure locations support checking the paraphrases.

| ID | Reference | Theme |
|---|---|---|
| R1 | [Shimodaira (2000)](https://stat.sys.i.kyoto-u.ac.jp/wp-content/uploads/2017/07/1998-Shimodaira-rm712-covariate-shift.pdf) | Weighted likelihood |
| R2 | [Sugiyama et al. (2007)](https://www.jmlr.org/papers/volume8/sugiyama07a/sugiyama07a.pdf) | Weighted validation |
| R3 | [Huang et al. (2007)](https://www.cs.cmu.edu/~arthurg/papers/HuaSmoGreBorSch07.pdf) | Kernel mean matching |
| R4 | [Bickel et al. (2009)](https://www.jmlr.org/papers/volume10/bickel09a/bickel09a.pdf) | Domain weighting |
| R5 | [Ben-David et al. (2010)](https://doi.org/10.1007/s10994-009-5152-4) | Adaptation theory |
| R6 | [Saenko et al. (2010)](https://doi.org/10.1007/978-3-642-15561-1_16) | Visual transfer |
| R7 | [Sun et al. (2016)](https://doi.org/10.1609/aaai.v30i1.10306) | Classical CORAL |
| R8 | [Blitzer et al. (2007)](https://aclanthology.org/P07-1056.pdf) | Review sentiment |
| R9 | [Anguita et al. (2013)](https://www.esann.org/sites/default/files/proceedings/legacy/es2013-84.pdf) | Smartphone HAR |
| R10 | [Liu and Tang (2013)](https://www.mdpi.com/1424-8220/13/7/9160) | Gas sensor drift |

The detailed records below preserve every field of the evidence matrix.

### R1 - Shimodaira (2000)

H. Shimodaira (2000), [Improving predictive inference under covariate shift by weighting the log-likelihood function](https://doi.org/10.1016/S0378-3758(00)00115-4); [author's 1998 preprint](https://stat.sys.i.kyoto-u.ac.jp/wp-content/uploads/2017/07/1998-Shimodaira-rm712-covariate-shift.pdf)

**Task and original data assignment:** Polynomial regression with source covariates from N(0.5, 0.5²), future covariates from N(0, 0.3²), and the same noisy cubic response.

**Method:** Density-ratio weighted likelihood / least squares.

**Published evidence and location:** Preprint §2/Fig. 1 and §3 address future-distribution loss under misspecification; §4/Lemma 4 favors uniform weighting asymptotically under correct specification.

**Limitation for this study:** Evidence locations refer to the accessible 1998 preprint, not the paywalled journal text. Regression results with known distributions do not establish classification gains here.

### R2 - Sugiyama et al. (2007)

M. Sugiyama, M. Krauledat, K.-R. Müller (2007), [Covariate Shift Adaptation by Importance Weighted Cross Validation](https://www.jmlr.org/papers/volume8/sugiyama07a/sugiyama07a.pdf)

**Task and original data assignment:** EEG binary classification: 14 datasets from five subjects; earlier-session labelled training, later-session unlabelled first half and evaluated second half.

**Method:** Importance-weighted cross-validation (IWCV) selects adaptive weighted LDA.

**Published evidence and location:** §5, Tables 1–2, pp. 997–998: IWCV-selected models improve over ordinary LDA in five cases and worsen in one.

**Limitation for this study:** Oracle OPT results are separate. Density-ratio assumptions and model-selection variance matter; our tuning is source-only and classifiers differ.

### R3 - Huang et al. (2007)

J. Huang, A. J. Smola, A. Gretton, K. M. Borgwardt, B. Schölkopf (2007 proceedings; NIPS 2006), [Correcting Sample Selection Bias by Unlabeled Data](https://www.cs.cmu.edu/~arthurg/papers/HuaSmoGreBorSch07.pdf)

**Task and original data assignment:** Toy regression and biased classification samples; source task labels and unlabelled target covariates supply the fit. §4.1 uses 100 source and 100 target observations.

**Method:** Kernel mean matching (KMM) estimates weights through constrained feature-mean matching.

**Published evidence and location:** §3.2/Lemma 4: the sampling bound worsens with the upper density-ratio bound, even with correct population weights.

**Limitation for this study:** The bound concerns feature means, not macro F1. KMM is not our logistic domain classifier; weight constraints motivate diagnostics without validating our cap of 10.

### R4 - Bickel et al. (2009)

S. Bickel, M. Brückner, T. Scheffer (2009), [Discriminative Learning Under Covariate Shift](https://www.jmlr.org/papers/volume10/bickel09a/bickel09a.pdf)

**Task and original data assignment:** Spam, Cora text and landmine classification. Cora has 812 pre-1996 source papers and 1,285 later target papers; source years provide tuning data.

**Method:** Domain-probability weighting, with integrated and two-stage discriminative models.

**Published evidence and location:** §10/Fig. 1 reports 15% relative reduction in Cora's 1−AUC risk for integrated models at 1,024 target examples.

**Limitation for this study:** This is not accuracy-point gain or a result for our two-stage implementation. Published tuning/metrics differ; our out-of-fold probabilities, normalization and cap are declared choices.

### R5 - Ben-David et al. (2010)

S. Ben-David, J. Blitzer, K. Crammer, A. Kulesza, F. Pereira, J. W. Vaughan (2010), [A theory of learning from different domains](https://doi.org/10.1007/s10994-009-5152-4); [full paper](https://escholarship.org/content/qt2nv1j9sc/qt2nv1j9sc.pdf)

**Task and original data assignment:** Classification theory for labelled source and unlabelled target samples; additional settings consider limited target labels.

**Method:** Generalization bounds involving hypothesis-class domain divergence.

**Published evidence and location:** Theorem 2, pp. 157–158: target error also depends on source error, sample complexity and ideal joint-hypothesis error.

**Limitation for this study:** Reducing marginal divergence alone cannot guarantee good target classification. This is not a macro-F1 guarantee or an empirical validation on our datasets.

### R6 - Saenko et al. (2010)

K. Saenko, B. Kulis, M. Fritz, T. Darrell (2010), [Adapting Visual Category Models to New Domains](https://doi.org/10.1007/978-3-642-15561-1_16); [full paper](https://people.bu.edu/bkulis/pubs/saenko_eccv_2010.pdf)

**Task and original data assignment:** Object recognition across Amazon product photographs, DSLR and webcam images; the same-category experiment uses three labelled target examples per category.

**Method:** Supervised cross-domain metric learning.

**Published evidence and location:** §5/Table 1 reports improved cross-domain recognition with learned transformations, with results differing by direction and method.

**Limitation for this study:** Target supervision and visual features differ from our unlabelled adaptation setting. Here “Amazon” denotes product images, not sentiment reviews.

### R7 - Sun et al. (2016)

B. Sun, J. Feng, K. Saenko (2016), [Return of Frustratingly Easy Domain Adaptation](https://doi.org/10.1609/aaai.v30i1.10306); [full paper](https://cdn.aaai.org/ojs/10306/10306-13-13834-1-2-20201228.pdf)

**Task and original data assignment:** Object and review classification with labelled source/unlabelled target data. The Office protocol adapts using target test features (§4.1).

**Method:** Classical CORAL whitens/recolors source features; source-validated linear SVM.

**Published evidence and location:** Table 5, p. 2064: Books→Electronics accuracy is 76.3% with CORAL versus 74.7% without adaptation.

**Limitation for this study:** Top-400-word features and 20 splits differ from ours. Algorithm 1 uses ridge 1; our ridge 1e-3, explicit mean alignment and disjoint target roles are implementation differences.

### R8 - Blitzer et al. (2007)

J. Blitzer, M. Dredze, F. Pereira (2007), [Biographies, Bollywood, Boom-boxes and Blenders: Domain Adaptation for Sentiment Classification](https://aclanthology.org/P07-1056.pdf)

**Task and original data assignment:** Books, DVDs, Electronics and Kitchen sentiment; 1,600 labelled training and 400 test reviews per domain, plus unlabelled data.

**Method:** Structural correspondence learning with mutual-information pivots (SCL-MI), linear Huber-loss classifier.

**Published evidence and location:** §4/Fig. 1, pp. 442–443: DVDs→Books accuracy rises from 72.8% for baseline to 79.7% for SCL-MI.

**Limitation for this study:** Different method and split. The 46% transfer-error reduction in §5/Table 3 includes 50 labelled target examples; it must not be attributed to label-free adaptation.

### R9 - Anguita et al. (2013)

D. Anguita, A. Ghio, L. Oneto, X. Parra, J. L. Reyes-Ortiz (2013), [A Public Domain Dataset for Human Activity Recognition Using Smartphones](https://www.esann.org/sites/default/files/proceedings/legacy/es2013-84.pdf)

**Task and original data assignment:** Six activities from 30 volunteers with 561 features; published 70%/30% volunteer train/test partition.

**Method:** Gaussian-kernel one-versus-all SVM with ten-fold hyperparameter validation.

**Published evidence and location:** §3/Table 4, pp. 440–441: 96% overall accuracy on 2,947 test patterns.

**Limitation for this study:** A dataset/baseline result, not an adaptation gain. Our linear SVM and four/five target-participant roles differ; published accuracy is not an expected score for this study.

### R10 - Liu and Tang (2013)

H. Liu, Z. Tang (2013), [Metal Oxide Gas Sensor Drift Compensation Using a Dynamic Classifier Ensemble Based on Fitting](https://www.mdpi.com/1424-8220/13/7/9160)

**Task and original data assignment:** Ten chronological gas batches; five analytes after excluding toluene. Fig. 3 trains on batches 1–5, 1–6, 1–7 or 1–8, then tests later batches.

**Method:** RBF-SVM ensembles with time-dependent classifier weights fitted from labelled early batches.

**Published evidence and location:** §4/Fig. 3 reports DWF outperforming the tested alternatives while performance still deteriorates over time.

**Limitation for this study:** Multiple labelled batches exceed our batch-1 source budget. These are classifier weights, not source-example importance weights. §5 notes slow weight search and fitting-function sensitivity.

This matrix contains **10 paper entries**. The [official HAR record](https://archive.ics.uci.edu/dataset/240/human+activity+recognition+using+smartphones) confirms participant-based roles, and the [Amazon authors' release notes](https://www.cs.jhu.edu/~mdredze/datasets/sentiment/) warn that released positive/negative files need not reproduce the paper's splits. These dataset records are supporting provenance, not additional paper entries.

## Research gap and study contribution

The reviewed evidence supports conditional adaptation benefits. Weighting depends on the source–target relation and estimation stability (R1–R4); domain-adaptation theory also retains a joint-prediction-error term (R5). Thus a smaller feature mismatch does not by itself establish better target macro F1. These are published theoretical or empirical observations, not results from the present study.

Prior evaluations use different data budgets, representations and outcomes. Supervised visual transfer uses target labels (R6); classical CORAL includes an Office setting that adapts on target test features and a review experiment with a different representation (R7). Sentiment, smartphone and gas studies use their own splits, classifiers and label budgets (R8–R10). Their numerical scores cannot be used as direct baselines for the protocol registered here.

**Specific research gap and contribution.** Within this reviewed set, there is no single evaluation of the registered combination: Logistic Regression, linear SVM and Random Forest × source-only, importance weighting and classical CORAL across nine Gas batch transfers, one HAR participant-transfer design and Books→Electronics, with disjoint adaptation/evaluation roles, matched target IDs and shared source-fitted representations. This is a bounded comparison gap inferred from these ten papers, not an exhaustive novelty claim about all literature.

Holding classifiers, source-only tuning, metrics and data access consistent makes it possible to examine whether an adaptation effect changes with classifier and shift type. The study will report paired target macro-F1 changes, accuracy and staged CPU cost across five seeds, a separate source-majority control, weight/overlap diagnostics and an uncapped-weight ablation. Per-transfer reporting and the registered uncertainty procedure keep improvements, losses and inconclusive effects visible.

The hypotheses remain **H1: importance weighting improves paired target macro F1** and **H2: CORAL improves paired target macro F1**, assessed separately by classifier and transfer pair. Positive published results motivate these tests; they do not verify them. Source-only tuning is a deliberate fairness constraint and a limitation, rather than a replication of every paper's model-selection procedure. The implementation uses classical CORAL with the declared mean alignment and ridge setting, not a neural-network CORAL loss. No target score has been observed or used to revise the design.
