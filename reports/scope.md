# Research scope: domain adaptation in classical machine learning

Scope specification `scope-01-r1`. Proposed study design; no experimental results are reported.

For Logistic Regression, linear SVM and Random Forest, when does importance weighting or correlation alignment (CORAL) improve or worsen held-out target macro F1 relative to source-only training under changes in gas sensor collection batch, smartphone participants and product review category, and what accuracy and computation-time trade-offs accompany these changes?

For each transfer pair and classifier, H1 predicts positive macro-F1 change from importance weighting and H2 predicts positive change from CORAL. Zero and negative effects remain reportable. Compare matched test IDs with seeds **11, 23, 37, 53, 71**.

**Time: Gas Sensor Array Drift:** Batch 1 → each batch 2–10 (nine pairs). **Adaptation / evaluation:** Seeded ID shuffle within each target batch; floor(N/2) adaptation rows, remainder evaluation

**People: smartphone HAR:** 21 official training participants → official test participants. **Adaptation / evaluation:** Four whole target participants for adaptation, five others for evaluation

**Category: Amazon sentiment:** Books → Electronics. **Adaptation / evaluation:** Released unlabelled Electronics reviews for adaptation, positive/negative Electronics reviews for evaluation

Three classifiers × source-only, importance weighting and CORAL give **nine main configurations**. Across 11 pairs and five seeds, plan **495 main rows**. A separate source-majority control contributes **one row per pair/seed, 55 total**; ties use sorted class ID. Removing the importance-weight cap contributes **165 separate ablation rows**, compared as uncapped minus capped. Exclude pilot, tuning and retry records from final totals.

All branches share source-fitted representations and source-only three-fold tuning, grouped by participant for HAR. Reuse selected classifier settings across branches. Weighting and CORAL additionally fit on unlabelled adaptation features; only weighting uses domain-classifier labels. No adaptation task labels are used. Test features are transformation/prediction inputs only; final target labels remain sealed until main and ablation predictions are frozen. Amazon sentiment fields and domain/file metadata cannot enter predictors; apply the registered duplicate audit before freezing roles.

Primary outcome: target macro F1 over classes with positive true test support. Secondary outcomes: accuracy and CPU wall-clock preprocessing, adaptation, classifier-fit and prediction seconds. Charge reused stage costs to every branch; exclude downloads, I/O, tuning, scoring and bootstrapping. Compare adapted minus matching source-only scores per pair/classifier/seed, reporting five-seed mean ± sample SD and paired effects without pooling away transfer direction.

For seed 11, use 2,000 paired percentile bootstrap draws with resampling seed 2026 and the original supported label set: whole HAR participants, unique retained Amazon reviews or measurements within each Gas batch. Descriptively, a 95% interval entirely above zero supports gain, entirely below zero supports loss, and containing/touching zero is inconclusive. Apply the same rule to ablation effects. No practical threshold or multiplicity adjustment is prespecified. These intervals do not estimate uncertainty in the five-seed mean; disclose any sign disagreement. HAR has only five evaluation clusters, Gas inference is conditional on batch with an independence approximation, and repeated splits are dependent.

The [research notebook](../domain_adaption.ipynb) records the full comparison matrix, settings, safeguards and outcome definitions. Source datasets and methods are those specified in the project design; acquisition provenance and literature verification are separate study stages.
