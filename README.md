# How Do Keyboard Type, Background Music, and Text Format Affect Typing Speed?

**STAT 430 – Experimental Design | University of Waterloo | 2026**

**Project Team:** Yiqi Xiang, Chang Sun, Elsie Wang

## Project Overview

This project investigates how keyboard type, background music, and text format influence typing speed through a controlled factorial experiment.

Using a **2³ full factorial design with participant blocking**, we examined the individual and interaction effects of three experimental factors on typing performance. A total of 72 randomized typing trials were conducted, and Analysis of Variance (ANOVA) was used to evaluate the statistical significance of treatment effects.

The objective was to identify whether different typing conditions meaningfully affect performance while accounting for individual differences between participants.

## Experimental Design

### Factors and Response Variable

Three experimental factors were examined, each with two levels:

| Factor | Level 1 (-1) | Level 2 (+1) |
|---|---|---|
| Keyboard Type (A) | Mechanical Keyboard | Apple Keyboard |
| Background Music (B) | Silence | Instrumental Music |
| Text Format (C) | Random Words | Paragraph |

**Response Variable:** Typing speed, measured in words per minute (WPM).

**Blocking Factor:** Participant, to control for differences in baseline typing ability.

### Experimental Setup

A **2³ full factorial design** was implemented with the following structure:

- 3 experimental factors, each at 2 levels
- 8 unique treatment combinations
- 3 participants serving as blocks
- 3 replications of each treatment combination per participant
- 24 trials per participant, resulting in **72 total observations**

Treatment orders were randomized separately for each participant to reduce potential learning, fatigue, and order effects.

Each trial was conducted using Monkeytype with a duration of 30 seconds. Participants were required to correct typing errors to maintain 100% accuracy.

The experiment used consistent text preparation procedures and the same instrumental music under the music condition.

## Methodology

### 1. Exploratory Data Analysis

Initial exploratory analysis examined typing speed distributions across participants and treatment conditions.

Boxplots were constructed to visualize differences in typing speed by:

- Participant (blocking factor)
- Keyboard type
- Background music
- Text format

Substantial differences in baseline typing speed were observed among participants, supporting the decision to account for participant effects through blocking.

### 2. Factorial ANOVA and Model Selection

ANOVA models were fitted in R using the `aov()` function to examine main effects and interactions among the experimental factors.

**Full Model**

The initial model included participant effects, all three treatment factors, and their interactions:

`WPM ~ Block * A * B * C`

**Reduced Model**

A reduced model retained participant blocking effects and the full factorial structure among treatment factors while excluding interactions involving participants:

`WPM ~ Block + A * B * C`

A nested-model F-test was used to compare these models.

**Model Comparison:**

- F(14, 48) = 1.868
- p = 0.0552

At the 5% significance level, the full model did not provide a statistically significant improvement over the reduced model.

The reduced model was therefore selected for the remaining analysis.

### 3. Main Effects Analysis

The reduced factorial ANOVA identified keyboard type as the only statistically significant treatment main effect.

| Experimental Factor | F-statistic | p-value | Result |
|---|---:|---:|---|
| Keyboard Type | 24.087 | < 0.001 | Significant |
| Background Music | 0.075 | 0.785 | Not significant |
| Text Format | 0.008 | 0.928 | Not significant |

Participants typed approximately **7 WPM faster in median speed using the Apple keyboard** compared with the mechanical keyboard.

Neither background music nor text format showed statistically significant main effects on typing speed.

### 4. Interaction Effects

Two-way and three-way interactions among keyboard type, background music, and text format were examined using factorial ANOVA and interaction plots.

The analysis found no statistically significant treatment interaction effects (all p-values > 0.18).

These findings suggest that, within the experimental conditions studied, the effect of keyboard type did not substantially depend on background music or text format.

### 5. Model Diagnostics

Residual diagnostics were performed to assess the assumptions underlying the selected ANOVA model.

Diagnostic procedures included:

- Residual histogram to examine the error distribution
- Normal Q-Q plot to assess approximate normality
- Residuals versus fitted values to examine patterns and variance consistency

The residuals were approximately centered around zero without an obvious systematic pattern. The Q-Q plot showed some deviations in the tails, suggesting that borderline statistical conclusions should be interpreted cautiously.

### 6. Run Order Analysis

To investigate possible learning and fatigue effects, typing speed was plotted against run order separately for each participant.

Although individual trials exhibited variation, there was no clear or consistent upward or downward trend across the 24 trials completed by each participant.

This provided no strong visual evidence of systematic practice or fatigue effects during the experiment.

## Key Findings

**1. Keyboard type significantly affected typing speed.**

The Apple keyboard was associated with approximately 7 WPM higher median typing speed than the mechanical keyboard among the three participants. The keyboard main effect was statistically significant (p < 0.001).

**2. Background music did not demonstrate a significant effect.**

The analysis found no statistically significant difference between instrumental music and silence (p = 0.785).

**3. Text format did not significantly influence performance.**

Typing paragraphs and random words produced similar typing-speed distributions (p = 0.928).

**4. No significant treatment interactions were detected.**

The results did not indicate that the effects of keyboard type, music, and text format meaningfully depended on one another.

**5. Participant blocking was important.**

Substantial baseline typing-speed differences between participants demonstrated the value of blocking in controlling variation unrelated to the treatment factors.

## Technologies and Statistical Skills

**Programming and Tools:** R, R Markdown, RStudio, `ggplot2`, `tidyverse`, `BsMD`

**Statistical Methods:**

- Design of Experiments (DOE)
- 2³ Full Factorial Design
- Randomized Experimental Design
- Blocking and Replication
- Analysis of Variance (ANOVA)
- Main and Interaction Effects
- Nested-Model F-Tests
- Statistical Hypothesis Testing
- Residual Diagnostics
- Exploratory Data Analysis
- Model Selection

## Repository Contents

- `STAT 430 Project.Rmd` – R Markdown source containing the ANOVA models, visualizations, interaction analysis, and model diagnostics.
- `STAT 430 Group 7 Typing Speed.pdf` – Final project report containing the experimental methodology, statistical results, conclusions, and limitations.
- `README.md` – Project documentation.

## Reproducibility

The statistical analysis was conducted in R using `ggplot2`, `tidyverse`, and `BsMD`.

To reproduce the analysis:

1. Install the required R packages.
2. Obtain the experimental dataset (`TypingData.csv`) from the project team.
3. Update the file path in `STAT 430 Project.Rmd` to point to the local CSV file.
4. Run the R Markdown code in RStudio to reproduce the ANOVA tables and statistical visualizations.

The dataset contains experimental treatment indicators, participant identifiers, and observed typing speeds.

## Limitations and Future Improvements

Several limitations should be considered when interpreting the findings:

- **Small participant sample:** Only three participants were included, limiting the generalizability of the results.
- **Short trial duration:** Each test lasted 30 seconds, which may not reflect typing performance during longer tasks.
- **Limited music conditions:** Only one instrumental music track was tested.
- **Keyboard familiarity:** Differences in participant experience with each keyboard may have influenced the observed effects.

Future experiments could involve a larger and more diverse participant population, longer typing trials, and additional keyboard and background music conditions.

## Project Context

This project was completed as a group assignment for STAT 430 Experimental Design at the University of Waterloo.

The analysis demonstrates the application of factorial experimental design, blocking, ANOVA-based hypothesis testing, statistical model comparison, and diagnostic evaluation to a real-world productivity question.
