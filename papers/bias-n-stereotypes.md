# Gender bias and stereotypes in Large Language Models

`3582269.3615599.pdf`

- [Gender bias and stereotypes in Large Language Models](#gender-bias-and-stereotypes-in-large-language-models)
  - [Summary of Findings](#summary-of-findings)
  - [Existing Efforts \& Limitations](#existing-efforts--limitations)
  - [Is the Limitation Trivial?](#is-the-limitation-trivial)
  - [Challenge of Non-trivial Limitation](#challenge-of-non-trivial-limitation)
  - [Proposed Solutions](#proposed-solutions)
  - [Questions](#questions)
    - [`many of the current benchmarks used to test for bias might already be included in the training data of these models`](#many-of-the-current-benchmarks-used-to-test-for-bias-might-already-be-included-in-the-training-data-of-these-models)
    - [the new testing paradigm](#the-new-testing-paradigm)
      - [Design Principles](#design-principles)
      - [Example of using ambiguous pronouns](#example-of-using-ambiguous-pronouns)

<details>
<summary>Longer version</summary>

Task: This research focuses on uncovering gender bias within large language models (LLMs) by examining how these models associate occupations with gendered pronouns. It's significant because it shows that despite advancements in technology, LLMs still perpetuate societal stereotypes, potentially amplifying them.

Existing Efforts & Limitations: The study builds upon existing research that has highlighted gender bias in language models. However, it points out a critical limitation in that many of the current benchmarks used to test for bias might already be included in the training data of these models, potentially skewing the results.

Is the Limitation Trivial?: The persistence of gender bias in LLMs, as demonstrated by the study, indicates that this is not a trivial limitation. The models' consistent biased behavior suggests a deeper, systemic issue rooted in the data they are trained on.

Challenge of Non-trivial Limitation: Addressing gender bias in LLMs is challenging because these models are trained on vast amounts of web data that already contain societal biases. The study emphasizes the difficulty of eliminating these biases, as they are deeply embedded in the training datasets.

Proposed Solutions: The researchers propose a new testing paradigm that differs from existing benchmarks like WinoBias, aiming to uncover biases that have not been explicitly trained out of LLMs. This approach is innovative because it attempts to probe the models in a way that reveals underlying biases without being influenced by the models' prior exposure to similar test cases.

</details>


## Summary of Findings

- **Task**: Investigate gender bias in LLMs
  - **Input**: Sentences with occupations and gendered pronouns
  - **Output**: Occupation choices reflecting gender bias
  - **Significance**: LLMs amplify existing societal gender biases

## Existing Efforts & Limitations

- **Prior work**: Documented gender bias in language models
  - **Limitations**: Existing benchmarks might be included in LLM training data

## Is the Limitation Trivial?

- **Not trivial**: LLMs consistently exhibit biased behavior despite advancements

## Challenge of Non-trivial Limitation

- **Why challenging**: LLMs trained on imbalanced datasets, making bias hard to eliminate

## Proposed Solutions

- **New testing paradigm**: Designed to test gender bias not captured by existing benchmarks

## Questions

### `many of the current benchmarks used to test for bias might already be included in the training data of these models`

Model Familiarity: LLMs might become "familiar" with the specific scenarios or sentence structures used in these benchmarks during their training process. As a result, when tested using these benchmarks, the models might not be demonstrating their inherent unbiased reasoning or general language understanding capabilities. Instead, they might be recalling patterns they've seen during training.

Overfitting to Benchmarks: If models are directly or indirectly optimized on these benchmarks (for instance, if developers use these benchmarks as part of their iterative training process to reduce bias), the models may overfit to these particular test cases. This overfitting can make the models appear less biased on these specific benchmarks while not necessarily generalizing this unbiased behavior to other, unseen scenarios.

Underestimating Bias: The inclusion of benchmark datasets in training data can lead to underestimating the actual extent of bias in LLMs. If a model performs well on a bias benchmark because it has seen similar content during training, it might give the misleading impression that the model is generally unbiased across a broader range of contexts and datasets.

### the new testing paradigm

#### Design Principles

Ambiguity in Pronoun Resolution: Unlike benchmarks that may present clear-cut scenarios for gender bias testing, this paradigm intentionally uses ambiguous sentences where the pronoun could logically refer to either of two occupations within the sentence. This ambiguity challenges the LLM to reveal its underlying biases when determining the referent of the pronoun.

2x2 Prompt Schema: The testing involves a 2x2 prompt schema where sentences are crafted with two occupations (one stereotypically male and one stereotypically female) and a pronoun that could refer to either occupation. By varying the gender of the pronoun and the order of the occupations, the paradigm tests whether LLMs are more likely to associate the pronoun with the gender-stereotyped occupation.

Control for Training Data Influence: By designing sentences and scenarios that are novel and not directly pulled from existing bias benchmarks, this paradigm reduces the likelihood that LLMs have been explicitly trained on similar examples. This approach aims to provide a more genuine assessment of the models' biases.

#### Example of using ambiguous pronouns

Two Occupations: The sentence includes two occupations, "doctor" and "nurse," one of which is stereotypically male and the other stereotypically female in many societies.
Ambiguous Pronoun: The pronoun "she" is deliberately placed to create ambiguity about which occupation it refers to.

Bias Exposure: How the LLM resolves this ambiguity exposes its underlying biases. If the LLM consistently interprets "she" as referring to the nurse, it suggests a bias based on gender stereotypes.