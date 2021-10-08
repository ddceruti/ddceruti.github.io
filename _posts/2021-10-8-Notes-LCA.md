---
layout: post
title: Basic concepts of life cycle analysis (LCA)
---

# A few notes on LCA

## LCA: Life Cycle Assessment/Analysis

[1] Intro from MIT: https://www.youtube.com/watch?v=gpuvUU0Nl4k

[2] Great LCA book:  Hauschild, M. Z., Rosenbaum, R. K., & Olsen, S. I. (2018). *Life cycle assessment* (Vol. 2018). Springer International Publishing, Cham. https://doi.org/10.1007/978-3-319-56475-3.

[3] Wikipedia article (checked with the book above): https://en.wikipedia.org/wiki/Life-cycle_assessment.

### Definition

Why: How to measure environmental impact of a given product or process

> LCA is a technique for assessing the environmental aspects and potential impacts associated with a product by:
>
> * Compiling <u>relevant</u> inputs and outputs
> * Evaluating the <u>potential</u> environmental impacts associated with those inputs and outputs
> * <u>Interpreting</u> the results of the inventory analysis and impact assessment phases in relation to the <u>objectives</u> of the study

[ISO 14040](https://www.iso.org/standard/37456.html) - From [1] slide 5

**!** Throughout the whole product/process life cycle: i.e. **"cradle-to-grave"**

## Steps of the methodology

4 stages

1. Goal and scope definition

   What to measure, what boundaries, where it is measured...

2. Inventory analysis

   All the relevant "streams"

3. Impact analysis

   What are the env. impacts for the goals of the step 2.

4. Interpretation



Notes from [2] and [3]:

### 1. Goal and scope

**Goal**

Must contain per ISO [wiki] following items: 

1. Intended application
2. Reasons for carrying out the study
3. Audience
4. "Whether the results will be used in a comparative assertions released publicly"

**Scope**

1. **Product system**: activities that transform inputs to outputs to produce the defined function and are within the system boundary.

2. Functional unit: definition of what is being studied. It enables comparison between functionally different systems (?? ex.: 1 m3 tank at standard conditions of methanol produced in the current year in Bavaria  with max. 1 wt% impurities ??). 

   ​	* Questions: what, how much, for how long/many times, where, how well.

3. **Reference flow:** amount of product or energy needed to realize the functional unit, i.e. to which al other input/outputs are related to. Ex: the X kg of methanol needed to fill the functional unit. This would be equivalent for several methanol production processes.

4. **System boundary**. Limits of inputs and outputs in accordance to goal.

   * Relevant concepts: technosphere (man-made) and ecosphere (the environment). Elementary flows go between both. These are the ideal boundaries.

   * Background and foreground system. Processes and products specific to product system vs not specific ones (ex.: electricity production of a given region)

5. **Assumptions and limitations**. 

6. **Data quality requirements**. Temporal, geographical and technological coverage (ex: energy mix depending on region!); precision, completeness and representativeness of the data (ex: imports are rounded to ...), consistency and reproducibility of the methods; sources (database accessible at european union db for primary electricity generation) ; uncertainty and data gaps (unknown other sources from imports).

7. **Allocation procedure**: a.k.a. multifunctionality of a product system i.e. the product system delivers other types of function in addition to the defined goal. There is a hierarchy of methods according to ISO 14044 [Hauschild]

   1. Avoid by Sub-division (divide into smaller processes to separate prod from co-prods)
   2.  Avoid by System Expansion (integrate the secondary function into the system boundaries, avoiding the impacts)
   3. Allocation using physical causality
   4. Allocation using representative physical parameter
   5. Allocation w/ other parameters (e.g. economic)

   1 is essentally increasing the resolution of the process model

   2 searches for substitutes of each one which provide the env flows for each function.

   3, 4 and 5 partition the environmental flows of primary and secondary and retain only the ones associated with the primery ones. 

8. **Impact  Assessment**: outline of the impact categories.

9. **Documentation of data**: Explicit documentation of IO

## 2. Life cycle inventory (LCI)

inventory of flows from and to ecosphere from the product system.  

Desired: primary source data collection. Alternative: secondary data from databases, literary sources and past studies. All documented ofc.

Three different LCI methods:

1. Process-based (we model the product system)
2. Economic IO (use info on elementary flows of associated with one unit of economic act.)
3. Hybrid (1 and 2)

## 3. LCI Assessment

Assessment of flows identified in LCI

Mandatory:

1. **Selection** of impact categories, indicators and characterization models (*which impacts do I need to assess??*). Relevant to region. In practice: LCIA method such as TRACI, ReCiPe, AWARE.
2. **Classification** of inventory results -> assign LCI results to impact categories of 1. Usage of LCA db and software.
3. **Characterization** quantify 1 and 2 with category indicators (*how much does each LCI results contribute*??)

Optional: normalization, weighting, grouping.

## 4. Interpretation

ISO 14043. Include:

1. Identification of issues of LCI and LCIA
2. Evaluation with completeness, sensitivity and consistency analyses
3. Conclusions, limitations and reccomendations

Here are included sensitvity and uncertainity evaluations (Hauschild Chapter 11).

#### Sensitvity and Uncertainity

Relevant topics:

* Precision vs accuracy
* Variability ()
* Sensitivity (extent to which the variation of an input influences the model results)
* Trade-off between simple and complex modeling  -> complex does not always lower uncertainity (https://doi.org/10.1007/BF02994186)

**Representation**: probability distribution (PDF - PD function). Basic concepts:

* std dev 
* average
* mode
* median
* percentiles
* confidence intervals

Many types available to use: in LCA generally log-normal. Useful to approximate unknown distribution and facilitates uncert. propagation methods. [Ch 11, p. 285-286]

**Types**: temporal, spatial, between objects variability, param uncertainty, model (structure) uncert., uncert. due to choices, ... 

**Influences:**

![image-20211008144453693](/home/dede/.config/Typora/typora-user-images/image-20211008144453693.png)

**Propagation methods:** 

1. Semiquantitative pedigree matrix (ecoinvent!) for uncert. of LCI data. ?Kind of expert based, but becoming less (more comparison between published data)?
2. **Monte Carlo (MC)** (SimaPro, openLCA). Needs sufficiently (waht is that anyway?) number of runs: Latin hypercube sampling (LHS) or simple random sampling (SRS)
   1. Generate random samples  of input vars
   2. Apply model and calculate LCA results 
   3. Analyze the model outputs
3. Taylor series expansion (CMLCA)

