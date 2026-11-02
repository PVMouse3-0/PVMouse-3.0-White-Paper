# Architecture companion

[Home](README.md) · [Source white paper](PVMouse-3.0-White-Paper.pdf)

This summary follows Chapters 3–5. It describes a proposed design; implementation choices and predictive value remain subject to testing.

## Shared biological state

A biological state space brings molecular, cellular, tissue and functional observations into shared coordinates. Background conditions, perturbations and measurement conditions have distinct roles:

| Information | Examples | Role |
| --- | --- | --- |
| Biological background | Genetic background, sex, age, housing and relevant history | Condition state estimation and response prediction. |
| Perturbations | Target gene, construct, affected tissues/cells, onset and persistence | Describe the intervention and its continuing influence. |
| Measurement context | Anatomical sampling area, platform, processing and batch | Relate latent states to measured observations. |
| Observations | RNA expression, spatial data, blood biochemistry, physiology and pathology | Constrain states and provide measurable training and evaluation targets. |

State-transition models describe how states change over time under specified conditions. Modality-specific observation models connect those states to readouts with their own aggregation, noise and missingness properties (Section 5.1, pp. 39–40).

## Four connected layers

| Layer | Inputs and representations | Intended outputs |
| --- | --- | --- |
| 1. Molecular priors | Consistent mouse gene identifiers; typed regulatory, interaction and pathway relationships; evidence and version metadata | Gene/pathway features and contextual constraints for cell representations. |
| 2. Cell-state reference | Single-cell or single-nucleus transcriptomes; adapted foundation-model representations; age, sex and tissue context | Cell-state features and uncertainty that support organ modeling. |
| 3. Spatial virtual organs | Cell states, composition, anatomical regions, neighborhoods, spatial observations and bulk data | Regional and organ states; molecular and functional observation readouts. |
| 4. Joint multi-organ system | Organ states, same-animal paired observations, background, perturbations and time | Joint states, response predictions, functional readouts and candidate temporal trajectories. |

The initial organs are brain, heart, liver, skeletal muscle and spleen. Tissue aggregation must match the actual sampling region and account for cell abundances, RNA contributions and measurement conditions.

Gene knowledge and cell references are expected to evolve. The cells–regions–organs organization and joint-state/response/time interfaces provide longer-term frameworks. These interfaces do not prescribe one fixed algorithm: hierarchical graphs, set models, state-space models and continuous-time models are options to compare, rather than mandatory released components.

## Training and inference

Development proceeds through layer-specific learning and validation, followed by constrained cross-layer adaptation. Same-animal tissue pairing is retained in joint training. Missing measurements are excluded from their corresponding loss terms while missingness information is preserved.

At inference, a query specifies background, available observations, intervention conditions and target time/readouts. Genetic effects already present at the starting point belong in the initial state; the genetic condition remains active during subsequent prediction. Starting from a normal state is not required for every query.

Outputs are intended to include expression and functional predictions, uncertainty, scope of applicability and interpretable intermediate results. Suggested cell populations or propagation relationships are hypotheses for follow-up experiments. Poorly supported conditions require reduced confidence or abstention.

## Validation principles

Chapter 5.8 (pp. 48–49) defines the evaluation approach:

- Separate missing-observation estimation from intervention-outcome prediction.
- Compare information sources by adding/removing molecular, cellular, spatial and cross-organ information.
- Compare simple and complex models using the same available inputs and data splits.
- Group all tissues, repeated observations and related sections from one animal/sample; account for litter, cage or kinship where relevant.
- Specify whether the goal is generalization to new animals, studies, ages, constructs or target genes; distinguish age interpolation from extrapolation.
- Flag public data potentially included in foundation-model pretraining and reserve a locked external challenge set.
- Compare temporal predictions with age-conditioned static and simple temporal baselines.
- Evaluate uncertainty coverage, interval width, calibration and retained prediction error when abstaining.

Cross-sectional age distributions provide population references. Repeated functional measurements and independent experiments are needed to test individual temporal predictions. Observational associations and model-generated explanations alone do not establish causal mechanisms.
