# Development path

[Home](README.md) · [Source white paper](PVMouse-3.0-White-Paper.pdf)

This companion summarizes Chapter 8 (pp. 64–72). Stages describe dependencies and intended capabilities; they are not a dated delivery schedule or a declaration of completed milestones.

## Status reported in the white paper

Some algorithmic components have been built. Collected data are being cleaned, and knockout-related resources continue to be organized. The overall system remains to be completed and validated.

The reported bulk RNA-seq collections, dated October 25, 2026, contain 4,741 C57BL/6J reference tissue samples spanning 1–116 weeks and another 2,511 tissue samples from genetic or other perturbations on that background. A 775-sample brain subset within those collections supports planning for the first spatial prototype. Counts are tissue samples, not animals. Dataset files and model components are not included in this publication repository.

## Staged development

| Stage | Main work and dependencies | Intended capability and evidence |
| --- | --- | --- |
| 1. Consistent data and reference coordinates | Align gene, animal, tissue, condition and time identifiers; organize molecular priors and cellular references. | Reusable reference components and traceable condition/observation interfaces. |
| 2. Brain spatial prototype | Connect cell atlases, anatomical/spatial references and region-matched bulk measurements; establish regional and organ aggregation. | Predict regional/organ expression and associated readouts; test against independent observations. |
| 3. Other organ modules | Reuse interfaces for heart, liver, skeletal muscle and spleen, with organ-specific composition and structure. | Compatible states and readouts across five organs, at resolutions supported by available evidence. |
| 4. Normal joint five-organ states | Combine same-animal tissue expression with physiological, biochemical and pathological observations. | Age-conditioned joint references and tests of cross-organ estimation value. |
| 5. Genetic responses and time | Incorporate knockout constructs, matched controls and observations at defined ages or times after perturbation. | Complete MVP objective: predict five-organ expression responses and associated phenotypes over a defined period. |

Functional readouts may contribute at any stage where corresponding data are available. Model selection and module retention depend on predictive improvement over alternatives.

## Key MVP tests

1. Do cellular and spatial information improve organ-level molecular and functional predictions?
2. Does pairing organs from the same animal improve estimates beyond independent organ models and simple regression?
3. Are knockout-associated changes in direction and magnitude reproduced across organs relative to matched controls?
4. Do state updates improve predictions at held-out times compared with static and simple temporal models?
5. Are uncertainty estimates useful under new ages, genetic conditions and incomplete observations?

Testing a selected knockout at new times and generalizing to unseen constructs or genes are separate evaluation goals. Errors and competing interpretations should inform additional experiments and model revision.

## Extensions and dependencies

| Direction | Additional requirements |
| --- | --- |
| Drug responses and schedules | Treatment-response data, compound identifiers, dose, route, timing and exposure information where available. |
| Diet and environmental interventions | Recorded intensity, duration, context and exposure history, with suitable controls. |
| Additional organs and genetic backgrounds | Matched references, joint observations and relevant perturbation data. |
| New molecular/observation modalities | Suitable models and paired observations to align them with the state interfaces. |
| Finer temporal resolution | Defined initial conditions, appropriate sampling intervals and longitudinal validation. |
| Human and cross-species research | Corresponding human data, explicit cross-species alignment and task-specific validation. |

These extensions are research directions. Reuse of an interface does not establish predictive transfer to a new biological context.
