# Gender bias and stereotypes in Large Language Models


![](https://github.com/cli/cli/assets/45612704/5dc867ae-fd3b-47bc-87f6-85d1c9fe14ac)

`3582269.3615599.pdf`

[paper](https://github.com/cli/cli/files/14222309/3582269.3615599.pdf)

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
    - [what's special about the 2x2 prompt schema? what's it designed to do?](#whats-special-about-the-2x2-prompt-schema-whats-it-designed-to-do)
    - [how does models rationalize existing biases?](#how-does-models-rationalize-existing-biases)

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
  This paper focuses in particular on gender bias, proposing a new
testing paradigm whose expressions are unlikely to be explicitly
included in LLMs’ current training data

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

### what's special about the 2x2 prompt schema? what's it designed to do? 

basically a prompt matrix with combination of gendered pronouns and occupations.

The 2x2 prompt schema is specifically designed to probe for gender bias in Large Language Models (LLMs) in a nuanced and effective manner. This schema is crucial for several reasons:

1. **Ambiguity Exploration**: Unlike traditional tests for gender bias which may have clear-cut right or wrong answers, the 2x2 prompt schema intentionally creates scenarios where the correct referent of a pronoun is ambiguous. This ambiguity forces the model to "choose" between potential referents, thereby revealing any underlying biases in its decision-making process.

2. **Gender Bias Measurement**: By pairing occupations with pronouns in varied configurations (male and female pronouns with traditionally male and female occupations), this schema directly tests the model's assumptions about gender roles and stereotypes. This method is particularly effective at uncovering biases because it isolates gender as the variable of interest, ensuring that the model's choice reflects its association between gender and occupation rather than other factors.

3. **Control for Sentence Structure**: The schema varies the position of the nouns (subject vs. object) and the gender of the pronouns in a controlled manner, allowing researchers to analyze how syntactic structure and gender cues influence the model's pronoun resolution. This is crucial for understanding whether models rely more on grammatical cues, contextual information, or stereotypical biases when making these decisions.

4. **Comparison Across Models**: By applying a standardized test schema, researchers can compare the performance and biases of different LLMs under the same conditions. This comparability is vital for tracking progress over time, understanding the effectiveness of interventions to reduce bias, and making informed decisions about model deployment.

5. **Insight into Model Reasoning**: By following up with questions about the models' choices, the schema provides insight into the "reasoning" LLMs use to justify their answers. This can reveal whether models are simply mirroring biases present in their training data or if they're capable of recognizing and navigating ambiguities in more nuanced ways.

6. **Beyond Binary Gender Assumptions**: Although the 2x2 schema in the provided context focuses on binary gender pronouns, its structure allows for expansion to explore biases related to non-binary and gender-neutral pronouns, offering a pathway to more inclusive bias detection methods.

In summary, the 2x2 prompt schema is a sophisticated tool designed to dissect and measure gender biases in LLMs by creating scenarios that require nuanced decision-making. It helps researchers identify not just the presence of bias but also provides insights into how and why these biases manifest, thereby guiding efforts to mitigate such biases in future models.

### how does models rationalize existing biases?

The paper illustrates that LLMs often provide explanations for their choices that appear authoritative and logical but are in fact misleading or incorrect, serving to rationalize the models' inherent biases. These rationalizations are particularly concerning because they mask the true, biased reasons behind the models' decisions with seemingly plausible justifications. Here are examples from the paper highlighting how LLMs rationalize their biased choices:

1. **Grammar-Based Rationalizations**:
   - Models claimed that pronouns are more likely to refer to the subject or object of a sentence based on grammatical rules. For instance, a model might suggest "he" refers to the "doctor" because "doctor" is the subject of the sentence, despite the sentence being intentionally ambiguous and such grammatical rules not dictating pronoun reference in this context. This type of explanation inaccurately implies a grammatical basis for a choice that aligns with gender stereotypes (e.g., associating "doctor" with male pronouns and "nurse" with female pronouns).

2. **Contextual Rationalizations**:
   - Models also justified their choices by claiming a particular interpretation was more logical or plausible given the sentence's context. For example, a model might say "she" likely refers to the "nurse" because of the context, ignoring the sentence's constructed ambiguity. Such rationalizations suggest that the models are using societal stereotypes about occupations and gender as a basis for resolving ambiguity, rather than admitting the inherent bias in their decision-making process.

3. **Explicit Gender Bias**:
   - In some cases, models explicitly used gender stereotypes to justify their choices. For instance, a model might argue "she" cannot refer to the "doctor" because "she" is used for female referents, and the "nurse" is the only female role mentioned, thereby revealing an explicit reliance on gender stereotypes.

4. **Confused or Illogical Explanations**:
   - At times, models provided explanations that were confused or illogical, further obscuring the biased reasoning behind their choices. For example, a model might claim "she" cannot refer to a certain profession because of irrelevant or nonsensical reasons, which does not hold up under scrutiny but serves to rationalize a stereotypically biased choice.

These examples demonstrate how LLMs use rationalizations to mask the biased underpinnings of their decisions. By providing explanations that seem logical on the surface, models obscure the fact that their choices are often based on societal stereotypes rather than neutral, grammatical, or contextual considerations. This behavior underscores the need for transparency and critical evaluation of model explanations to understand and mitigate biases in AI systems.