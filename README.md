### Project Background

This project evaluates national well-being data from the OECD "How's Life?" database to assist public policy decision-makers and well-being budgeting units (such as New Zealand's Wellbeing Budget team and the OECD WISE Centre) in managing resources during systemic crises. From the perspective of a Data Analyst working alongside government policy units, the objective is to determine whether pre-crisis drivers of population well-being remain stable during major disruptions (such as the COVID-19 pandemic) or if public spending priorities must pivot toward entirely new metrics.

The analysis evaluates statistical models across three distinct outcomes—Cognitive Evaluative (Life Satisfaction), Hedonic Emotional (Negative Affect), and Behavioral Pathology (Deaths of Despair)—by comparing empirical data-driven screening against a theory-driven framework based on Maslow's hierarchy of needs.   Insights and recommendations are provided on the following key areas:
- Category 1: Model Performance & Strategy (Data-Driven vs. Theoretical Frameworks)
- Category 2: Structural Coefficient Stability During Crisis
- Category 3: Outcome-Specific Well-Being Drivers
- Category 4: Diagnostic Residuals & Anomalous Country Outliers

### Data Structure & Initial Checks

The underlying dataset was constructed from two primary dataflows extracted from the OECD Well-being Data Portal: Current Well-Being (CWB) and Future Well-Being (FWB). The data encompasses 149,124 records across 15 domains and up to 48 countries spanning 2004–2026.
A description of each core data component is as follows:
- Current Well-Being (CWB Dataflow): 111,266 records covering 68 measures across 11 domains (e.g., Income & Wealth, Work & Job Quality, Health, Social Connections, Subjective Well-being) for 47 countries. Contains survey and administrative lived-experience indicators.
- Future Well-Being (FWB Dataflow): 37,858 records covering 35 measures across 4 capital domains (Economic, Natural, Human, Social) for 48 countries.
- Core Analytic Panel (Screening & Evaluation Split): 33 countries filtered for consistent total demographic representation across two explicit time windows: Pre-Pandemic Screen Window (2013 & 2018 means) and Pandemic Fit Window (2021 & 2022 means).
- SDMX Quality Flags: Quality checks confirmed ~90% observations marked as A (Normal), ~7% as D (Definition differs), ~1% as B (Time-series break), with retained analytical observations containing ≤2% B or D flags

<img width="500" height="300" alt="graph1" src="https://github.com/user-attachments/assets/29208964-e443-4c51-b54c-0664095388c8" />

### Executive Summary

#### Overview of Findings

An empirical evaluation of OECD well-being data before (2013–2018) and during (2021–2022) the COVID-19 pandemic reveals that the fundamental drivers of population well-being do not change during a crisis; statistical tests show zero detectable shift in relationship coefficients across time. However, no single measurement framework covers all well-being dimensions: data-driven indicators selected specifically per outcome systematically outperform general theoretical sets (such as Maslow’s hierarchy), achieving an adjusted $R^2$ of 0.85 on life satisfaction compared to 0.29 for theory. Crucially, while relational trust and perceived adequacy dictate life satisfaction, economic participation anchors daily affect, and educational/human capital determinants govern behavioral deaths of despair. 

<img width="500" height="300" alt="pic2" src="https://github.com/user-attachments/assets/c9c281cf-bc30-479c-8bfd-8a6f43ea40cf" />

### Insights DeepDive
#### Category 1: Model Performance & Strategy (Data-Driven vs. Theoretical Frameworks)
- Data-driven screening decisively outperforms theoretical frameworks across all outcomes. In predicting cognitive life satisfaction during the pandemic, the data-driven model achieved an adjusted $R^2$ of 0.8596 ($N=27$), whereas the general Maslow theoretical framework achieved an adjusted $R^2$ of 0.2883 ($N=33$), yielding a performance gap of 0.56.
- Theoretical models show competitive strength only when outcome measures closely align with specific constructs. On hedonic negative affect balance, the Maslow model reached an adjusted $R^2$ of 0.5278 ($N=33$) compared to the data-driven screen's 0.6292 ($N=28$). This narrow 0.10 gap is heavily driven by the single indicator shared by both models: the national employment rate.
- Behavioral outcome modeling requires domain-tailored metrics over general well-being frameworks. For log deaths of despair (suicide, alcohol, and drug abuse mortality), the data-driven screen achieved an adjusted $R^2$ of 0.4017 ($N=23$), doubling the performance of the general Maslow set at an adjusted $R^2$ of 0.2116 ($N=30$).
- The data-driven screening approach maintained strong cross-window generalization. Moving from the pre-pandemic screen window (2013–2018) to the pandemic fit window (2021–2022), the life satisfaction model drop in adjusted $R^2$ was minimal ($0.87 \rightarrow 0.85$), proving that pre-crisis screening yields robust predictive models during crisis conditions.  

<img width="500" height="300" alt="pic3" src="https://github.com/user-attachments/assets/b9221f94-e893-45d6-b7e1-615f3aa018d1" />

#### Category 2: Structural Coefficient Stability During Crisis
- Pooled Chow-style interaction tests confirm structural coefficient stability under systemic shock. Across all six estimated regression models (3 outcome-specific data-driven models and 3 Maslow models), joint interaction $p$-values between predictors and the pandemic-era dummy variable were statistically insignificant.
- Life satisfaction drivers remained statistically unchanged between 2013–2018 and 2021–2022 ($p = 0.41$). Pre-pandemic predictor coefficients mapped directly into the pandemic window without re-ranking.
- Negative affect balance ($p = 0.56$) and log deaths of despair ($p = 0.86$) displayed absolute structural stability. Despite severe macroeconomic and social disruptions during 2021–2022, the underlying relationship between external conditions and well-being outcomes remained stable.
- Crisis impacts shifted national outcome levels rather than altering the core structural relationships. While specific countries experienced shifts in absolute satisfaction or affect scores, the unit-change impact of key drivers (such as relational trust or employment) remained invariant.  

<img width="500" height="300" alt="pic4" src="https://github.com/user-attachments/assets/6b2b9b60-bece-418d-92f8-c2301d13588a" />


#### Category 3: Outcome-Specific Well-Being Drivers
- Social capital and relational stability dominate cognitive life satisfaction. "Satisfaction with personal relationships" was the strongest predictor of pandemic life satisfaction ($\beta = 0.293, p = 0.004$), followed by "Trust in others" ($\beta = 0.153, p = 0.023$). Adding the social/relational block to material indicators increased adjusted $R^2$ from 0.53 to 0.85 ($F = 17.8, p < 0.001$).
- Economic participation directly anchors hedonic emotional states. National employment rate was the primary statistically significant mitigator of negative affect balance ($\beta = -2.557, p = 0.020$), accompanied by "Satisfaction with time use" ($\beta = -2.544, p = 0.051$).
- Structural human capital determinants drive behavioral pathology over short-term financial transfers. For log deaths of despair, "Student science skills" (a proxy for broader educational infrastructure) served as the primary predictor ($\beta = 0.189, p = 0.052$), whereas direct disposable income per capita showed virtually zero effect ($\beta = -0.020, p = 0.849$).
- No single indicator spans all three well-being domains. The data-driven screens selected almost entirely distinct sets: relational perception metrics for cognitive evaluation, economic participation for emotional state, and educational/health capital for behavioral outcomes.

+---------------------------------------------------------------------------------------------------+
|                        DOMINANT STATISTICAL DRIVERS BY WELL-BEING OUTCOME                         |
+----------------------------------+--------------------------------------+---------------+---------+
| Outcome                          | Primary Predictor                    | Coefficient β | p-value |
+----------------------------------+--------------------------------------+---------------+---------+
| Cognitive Life Satisfaction      | Satisfaction with relationships     | +0.293        | 0.004   |
| Cognitive Life Satisfaction      | Trust in others                      | +0.153        | 0.023   |
| Hedonic Negative Affect Balance  | Employment rate                      | -2.557        | 0.020   |
| Hedonic Negative Affect Balance  | Satisfaction with time use           | -2.544        | 0.051   |
| Behavioral Deaths of Despair     | Student science skills               | +0.189        | 0.052   |
+----------------------------------+--------------------------------------+---------------+---------+

#### Category 4: Diagnostic Residuals & Anomalous Country Outliers
- Latvia represents a statistically significant response outlier. In the life satisfaction model, Latvia exhibited a studentized residual of -3.8 (Bonferroni adjusted $p = 0.03$) with low leverage (0.10). While Latvia's measured trust and time-use satisfaction were ordinary, reported life satisfaction was far below prediction (residual -0.66).
- Perceived health accounts for 40% of Latvia's negative well-being miss. Latvia recorded the lowest positive perceived health in the sample (50% vs. 68% sample mean). Including perceived health in an added-variable test absorbed a substantial portion of the miss (residual reduced from -0.66 to -0.38, $\beta = +0.13, p = 0.015$), with the remainder aligning with established post-transition life satisfaction gaps in ex-Soviet economies.
- Greece is a high-leverage structural point rather than a response outlier. Greece demonstrated extreme leverage (0.76) and Cook's $D = 3.3$, driven by severe economic strain (71% reporting difficulty making ends meet, nearly 4 SDs above the sample mean).
- Removing Greece resolves regression coefficient distortion. Deleting Greece via a leave-one-out refit shifted the "Difficulty making ends meet" coefficient from a non-significant +0.05 ($p = 0.53$) to a theoretically expected -0.14 ($p = 0.06$), confirming that the positive coefficient in the headline model was a high-leverage extrapolation artifact.  

+---------------------------------------------------------------------------------------------------+
|                          DIAGNOSTIC OUTLIER ANALYSIS SUMMARY (MODEL 1)                             |
+---------+--------------------+----------+-----------+---------------------------------------------+
| Country | Studentized Resid. | Leverage | Cook's D  | Diagnosis & Strategic Finding               |
+---------+--------------------+----------+-----------+---------------------------------------------+
| Latvia  | -3.8 (p = 0.03)    | 0.10     | Low       | True Response Outlier. Driven by low        |
|         |                    |          |           | perceived health & post-transition gap.     |
| Greece  | Non-sig (p = 0.22) | 0.76     | 3.3       | High-Leverage Point. Extreme economic       |
|         |                    |          |           | strain distorts income adequacy slope.      |
+---------+--------------------+----------+-----------+---------------------------------------------+

#### Recommendations
Based on the insights and findings above, we recommend government policy units and well-being budgeting teams consider the following:
- Pre-crisis statistical relationships remain completely valid during acute shocks ($p > 0.40$). Maintain established baseline well-being dashboards during crises rather than creating new, unvetted crisis metrics.
- Social connections and trust provide the largest explanatory boost for cognitive well-being ($F = 17.8, p < 0.001$). Prioritize funding for social infrastructure and community connection initiatives alongside direct financial relief.
- Employment rate is the primary mitigator of daily negative affect ($\beta = -2.557, p = 0.020$). Design economic intervention programs that preserve active labor market participation to safeguard emotional stability.
- Evaluative metrics like life satisfaction do not track behavioral pathologies like deaths of despair (Maslow adjusted $R^2 = 0.21$). Establish dedicated public health surveillance systems focused on structural educational and health indicators.
- Perceived material adequacy (e.g., ability to keep home warm) outperforms raw macro-income figures in tracking well-being. Target welfare transfers toward specific material deprivation bottlenecks rather than broad macroeconomic stimulus.

#### Assumptions and Caveats
Throughout the analysis, key assumptions and methodological constraints were managed as follows:
- Sample Limitation & Geographic Scope: The core analytical panel was constrained to 23–33 OECD countries (predominantly European) due to complete-case availability across both time windows. Findings generalize to developed economies rather than developing nations.
- Common-Source Variance: Life satisfaction and several top-performing screened predictors share the Gallup World Poll origin, introducing potential common-method variance that inflates relative performance over register-based indicators.
- Ecological Fallacy: Analysis was conducted on country-level aggregate means ($N \approx 27–33$), meaning cross-sectional relationships cannot be directly inferred as individual-level causal effects.
- Demographic Deduplication Filtering: Raw OECD data files contain overlapping rows for total, male, female, and age-disaggregated groups; explicit joint filtering to Total was required to prevent population mixing.
- Non-Independence in Stability Testing: Pooled Chow-style stability tests stack country observations across two time windows, introducing minor temporal autocorrelation; $p$-values are interpreted as heuristic indicators of stability rather than exact tests. 


