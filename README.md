# Domain adaptation in classical machine learning

Can unlabelled data from a new domain help a classifier trained under different conditions? This study compares source-only training, importance weighting and correlation alignment (CORAL) for Logistic Regression, linear SVM and Random Forest.

The experiments use gas sensor batches collected at different times, smartphone activity measurements from different volunteers, and Amazon reviews from different product categories. The outcomes are target accuracy, macro F1 and computational time.

[Open the project notebook in Google Colab](https://colab.research.google.com/github/jayantiyadav04/domain-adaptation-ml/blob/main/domain_adaption.ipynb). Use a hosted Python CPU runtime and save an editable copy in Google Drive. The notebook defines the research question, planned comparisons and outcome interpretation. The [scope summary](reports/scope.md) describes the proposed design; experimental results are pending.

The [literature review](reports/literature.md) compares ten primary papers and explains the study's bounded research gap, including differences in target supervision, data splits and representations.

The runtime and persistent-storage setup was verified from student-run Colab outputs. The [environment record](reports/environment.json) contains the observed CPU, Python/package versions, seeds, thread settings and verification results. These values describe the observed sessions.

The [dataset-source manifest](reports/data_sources.json) records the three original archives, retrieval times, observed sizes and SHA-256 fingerprints, required file groups, citations and reuse terms. Student-reported Colab outputs verify reuse of all three archives without new dataset HTTP requests, followed by an independent cache check and Drive synchronization. The first acquisition output was not retained; the returned manifest preserves the retrieval metadata. Row counts, feature schemas and duplicate audits remain to be checked.

## Runtime and durable storage

1. Save an editable notebook as `MyDrive/Topic40/domain_adaption.ipynb` and select a Google-hosted Python CPU runtime with hardware accelerator None.
2. Run `runtime-environment`, then `drive-storage`. Retain the printed BEFORE fingerprint and kernel ID, and save the notebook. The storage cell synchronizes and unmounts Drive after writing its setup metadata.
3. Disconnect and delete the runtime, reopen the same saved Drive notebook, and reconnect to hosted CPU. Run `runtime-environment` again, then `verify-drive-persistence`, entering the saved fingerprint. Skip `drive-storage` during this read-only proof. Matching marker bytes, a different kernel ID, the saved-notebook path and a PASS result establish the recorded checks.

Use this manual sequence instead of Run all. `notebook-location-audit` is an optional read-only troubleshooting cell for a failed notebook-path check; skip it during normal setup and the persistence proof. Keep archives, splits, evaluation keys, markers and per-run artifacts in the persistent project folders on Drive.

For archive acquisition after setup, run `runtime-environment`, then `acquisition-definitions`, `acquire-archives` twice and `verify-archive-cache`. The second acquisition run must reuse all three verified archives. The final check writes the compact manifest to the project's reports folder and synchronizes/unmounts Drive. Raw archives, detailed inventories and attempt logs stay private in the project's raw folder. No extraction or dataset-row parsing is performed by these cells.
