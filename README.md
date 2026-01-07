# PATTERN RECOGNITION OF ANTIBIOTIC RESISTANCE IN ESCHERICHIA COLI, SALMONELLA SPP., SHIGELLA SPP., AND VIBRIO CHOLERAE FROM WATER-FISH-HUMAN NEXUS

**An Undergraduate Thesis**

Presented to the Faculty of Department of Computer Science  
Mindanao State University - Marawi City Campus

In Partial Fulfillment of the Requirements for the Degree of  
**Bachelor of Science in Computer Science**

---

**Submitted by:**
- Al-Hanif A. Magomnang
- Reynaldo A. Pahay Jr.

**Adviser:** Prof. Janice F. Wade, MSCS

**Co-Adviser:** Mr. Llewelyn A. Elcana

**January 2026**

---

## Table of Contents

- [Chapter 1: Introduction](#chapter-1-introduction)
  - [Background of the Study](#background-of-the-study)
  - [Statement of the Problem](#statement-of-the-problem)
  - [Objectives of the Study](#objectives-of-the-study)
  - [Significance of the Study](#significance-of-the-study)
  - [Scope and Limitations](#scope-and-limitations)
- [Chapter 2: Review of Related Literature](#chapter-2-review-of-related-literature)
  - [Related Concepts](#related-concepts)
  - [Related Studies](#related-studies)
- [Chapter 3: Theoretical Framework](#chapter-3-theoretical-framework)
- [Chapter 4: Methodology](#chapter-4-methodology)
- [Chapter 5: Architectural Design](#chapter-5-architectural-design)
- [Chapter 6: Results and Discussion](#chapter-6-results-and-discussion)
- [Chapter 7: Conclusion and Recommendation](#chapter-7-conclusion-and-recommendation)
- [References](#references)

---

## Chapter 1: INTRODUCTION

### Background of the Study

Antimicrobial resistance (AMR) represents one of the most pressing global health challenges of the 21st century. The World Health Organization has declared AMR among the top ten threats to global health, with an estimated 1.27 million deaths directly attributable to bacterial AMR in 2019 alone [2]. Without coordinated intervention, AMRrelated mortality is projected to reach 10 million deaths annually by 2050, surpassing cancer as a leading cause of death worldwide [3].

The Philippines, as a rapidly developing archipelagic nation with extensive aquaculture industries and diverse healthcare systems, faces unique challenges in AMR surveillance and control. The country’s position within the Indo-Pacific region —a recognized hotspot for emerging infectious diseases—places it at elevated risk for resistance dissemination across human, animal, and environmental interfaces [4]. The Antimicrobial Resistance Surveillance Program (ARSP), established in 1988, has documented concerning trends including rising carbapenem-resistant Enterobacteriaceae and extended-spectrum β-lactamase (ESBL)-producing organisms in clinical settings [5].

Recent advances in machine learning (ML) offer promising opportunities to enhance AMR surveillance capabilities. Data-driven approaches including clustering algorithms, random forest classifiers, and neural networks have demonstrated utility in identifying resistance patterns, predicting phenotypes from genotypes, and stratifying patient risk [6], [7]. However, application of these methods to environmental and aquaculture-derived isolates remains limited, particularly in resource-constrained settings where phenotypic data predominate over genomic information.

The Integrated One Health Approach to AMR Containment (INOHAC) AMR Project Two, implemented across three Philippine regions—BARMM, Central Luzon, and Eastern Visayas—provides a unique dataset spanning the water-fish-human nexus [8]. This One Health framework recognizes that AMR emergence and transmission occur at the intersection of human health, animal health, and environmental contamination, requiring integrated surveillance strategies [9].

### Statement of the Problem

Existing antimicrobial resistance (AMR) surveillance frameworks rely on predefined categorical labels—such as species classifications, clinical breakpoints, and resistance prevalence summaries—that constrain how phenotypic antimicrobial susceptibility testing (AST) data are represented and analyzed, thereby limiting the ability of pattern recognition methods to discover latent resistance structure.

In heterogeneous datasets from the Water–Fish–Human nexus, such as the INOHAC–Project 2 AST data, resistance profiles are noisy and inconsistently encoded, and unsupervised clustering alone provides limited assurance that discovered patterns are coherent, discriminative, or robust.

The absence of an integrated, leakage-aware pattern recognition framework that combines data preprocessing, unsupervised structure discovery, supervised validation, and systematic evaluation restricts the effective application of machine learning for quantitative characterization of antimicrobial resistance patterns across interconnected environmental and human-associated reservoirs.

### Objectives of the Study

#### General Objective

To develop a pattern recognition system for antimicrobial resistance in the Water–Fish– Human nexus by preprocessing phenotypic AST data from the INOHAC–Project 2,

applying unsupervised clustering to discover latent resistance structures, and employing supervised machine learning algorithms to validate and interpret the discriminative capacity of identified resistance patterns.

#### Specific Objectives

Specifically, this study aims to:

- Preprocess and engineer features from the INOHAC–Project 2 phenotypic AST dataset, including data cleaning, resistance encoding, and computation of derived features, in order to create an analysis-ready dataset suitable for pattern recognition

in the Water–Fish–Human nexus.

- Apply unsupervised hierarchical clustering for resistance phenotype discovery and to evaluate multiple supervised machine learning algorithms for their capacity to discriminate and validate the identified resistance patterns derived from the processed

dataset.

- Design and develop an integrated pattern recognition framework that incorporates data-driven cluster selection, leakage-safe model training, and an interactive visualization dashboard for exploring resistance profiles, regional distributions, and co-

resistance relationships.

- Evaluate the pattern recognition system using appropriate quantitative metrics and to interpret the resulting resistance patterns within the context of the Water–Fish– Human nexus without inferring causality.

### Significance of the Study

This study significantly advances environmental AMR surveillance in the Philippines by validating a reproducible, unsupervised-supervised hybrid machine learning framework. By bridging phenotypic analysis with computational clustering, this research demonstrates the feasibility of high-resolution resistance profiling in resource-limited settings without relying on costly whole-genome sequencing. This methodological con-

tribution not only fills a critical academic gap but also provides a scalable, open-access analytical pipeline that enables researchers and public health authorities to replicate these techniques for real-time phenotype monitoring.

### Scope and Limitations

#### Scope

This study encompasses the following:

- Data Source: Antimicrobial susceptibility testing (AST) data from 491 bacterial isolates collected through the INOHAC AMR Project Two across three Philippine

regions: BARMM, Central Luzon (Region III), and Eastern Visayas (Region VIII).

- Organisms: Members of the family Enterobacteriaceae including Escherichia coli, Klebsiella pneumoniae, Enterobacter species, and Salmonella species isolated from

water, fish, and hospital sources.

- Antibiotics: A panel of 22 antibiotics spanning major classes including penicillins, cephalosporins, aminoglycosides, fluoroquinolones, tetracyclines, and carbapenems,

as tested according to Clinical and Laboratory Standards Institute (CLSI) guidelines.

- Analytical Methods: Hierarchical agglomerative clustering (Ward’s linkage, Euclidean distance), principal component analysis (PCA), Random Forest classifica-

tion, and Phi coefficient co-resistance analysis.

- Temporal Scope: Cross-sectional analysis of isolates collected during the INOHAC AMR Project Two sampling period.

#### Limitations

- Phenotypic Focus: This study analyzes phenotypic resistance profiles (susceptible/ intermediate/resistant) without genotypic characterization. Resistance mechanisms and mobile genetic elements are hypothesized but not directly confirmed.
- Retrospective Design: Analysis was conducted on historical AST data, precluding prospective validation or temporal trend analysis.
- Regional Representation: The three study regions may not be representative of all

Philippine provinces, limiting generalizability to unstudied areas.

- Missing Data: Some isolates lacked complete antibiotic panel coverage, potentially

affecting cluster assignments for partially tested specimens.

- Environmental Context: While One Health sampling captured water, fish, and hospital sources, additional environmental compartments (soil, wastewater, wildlife) were not included.

---

## Chapter 2: REVIEW OF RELATED LITERATURE

### Related Concepts

This section establishes the conceptual foundations underlying the analytical framework, situating unsupervised machine learning and co-resistance analysis within antimicrobial resistance (AMR) surveillance.

#### Unsupervised Learning for Biological Pattern Discovery

The fundamental challenge in environmental AMR surveillance lies in the absence of predefined phenotype labels. Unlike clinical settings where treatment outcomes may provide ground truth for supervised learning, environmental isolates from the waterfish-human nexus lack such annotations [10]. This constraint necessitates unsupervised approaches that discover structure directly from data without labeled examples [11].

### Hierarchical Agglomerative Clustering

Hierarchical clustering constructs a tree-like structure (dendrogram) that groups similar observations based on distance metrics, progressively merging clusters until a single root encompasses all data points [12]. Among linkage methods, Ward’s minimum variance approach minimizes within-cluster sum of squares at each merge step, producing compact, spherical clusters that often correspond to biologically meaningful groupings. The choice of distance metric fundamentally shapes cluster geometry. Euclidean distance remains standard for continuous data and is required for Ward’s method. While the ordinal nature of resistance encoding (Susceptible = 0, Intermediate = 1, Resistant = 2) introduces theoretical ambiguity, empirical evaluations demonstrate robust clustering performance with ordinal resistance data [13].

### Principal Component Analysis for Dimensionality Reduction

When analyzing resistance profiles across multiple antibiotics, visualization becomes impossible without dimensionality reduction. Principal Component Analysis (PCA) addresses this by projecting high-dimensional data onto orthogonal axes that maximize variance [14]. The first principal component captures the direction of greatest variability —often correlated with overall resistance burden—while subsequent components reveal

secondary patterns such as antibiotic class-specific resistance.

In AMR research, PCA serves dual purposes: enabling two-dimensional visualization of cluster separation and identifying resistance features that drive phenotypic differentiation [6]. When clusters identified through hierarchical methods display separation in PCA space, this provides independent validation that the groupings capture genuine phenotypic structure.

### Cluster Validation via Silhouette Analysis

Determining optimal cluster number remains a persistent challenge in unsupervised learning [11]. The silhouette coefficient addresses this by measuring the ratio of withincluster cohesion to between-cluster separation [15]. Values range from −1 to +1, where scores ≥ 0.25 indicate weak structure, scores ≥ 0.40 indicate moderate-to-strong structure suitable for biological phenotype analysis, and scores ≥ 0.70 suggest exceptionally well-defined groupings [16], [17].

This internal validation evaluates whether data genuinely contain clusterable structure at a given resolution. For AMR phenotyping, high silhouette scores indicate that isolates partition into distinct resistance archetypes rather than forming a continuous spectrum.

#### Supervised Validation of Unsupervised Clusters

A critical methodological innovation involves using supervised classification not for prediction, but for validation. Once unsupervised clustering assigns isolates to pheno-

typic groups, Random Forest classification [18] assesses whether these groupings are

sufficiently distinct to be discriminated by an independent learning algorithm.

This hybrid unsupervised-supervised framework addresses a fundamental epistemological concern: how can one validate clusters without ground truth labels? By training a classifier on cluster assignments (treating them as provisional labels) and evaluating discrimination via cross-validation, the approach tests whether clusters represent coherent structures rather than noise. High classification accuracy combined with high silhouette scores provides convergent evidence for phenotypic validity [7].

#### Spatial Considerations in Resistance Epidemiology

Antimicrobial resistance does not distribute randomly across geographic space. Isolates from proximate sampling sites often exhibit correlated resistance profiles due to shared selection pressures or horizontal gene transfer [19]. This phenomenon—spatial autocorrelation—has implications for surveillance design and statistical inference.

In multi-regional datasets spanning diverse geographic areas, isolates from the same sampling site share environmental and anthropogenic exposures. Geographic stratification of clustering results—examining whether resistance phenotypes distribute differently across regions—addresses this spatial dependence while revealing regional resistance signatures.

#### Co-Resistance Patterns

Co-resistance describes the phenomenon where resistance to one antibiotic is statistically associated with resistance to another [20]. Such associations may arise from genetic linkage, cross-resistance mechanisms, or shared selection pressure.

The clustering methods employed in this study implicitly capture co-resistance through phenotypic similarity. Isolates resistant to antibiotics A and B cluster together precisely because their joint resistance pattern differs from isolates resistant only to A or only to B. Visualizing cluster-specific resistance profiles as heatmaps reveals which antibiotic combinations define each phenotype [21].

#### The Multiple Antibiotic Resistance Index

The Multiple Antibiotic Resistance (MAR) index provides a scalar summary of resistance burden, calculated as the ratio of resistant antibiotics to total antibiotics tested [22]:

MAR = a/b, where *a* represents the number of antibiotics to which the isolate is resistant and *b* represents the total number of antibiotics tested. Krumperman’s original formulation established a threshold of 0.2, above which isolates likely originate from environments with significant antibiotic selection pressure. Clusters characterized by high mean MAR likely represent multidrug resistance (MDR) phenotypes with clinical relevance, providing external validation independent of the clustering algorithm.

#### Multidrug Resistance Classification

Multidrug resistance (MDR) is formally defined as acquired non-susceptibility to at least one agent in three or more antimicrobial categories [23]. This classification framework, established by an international expert proposal, provides standardized definitions for MDR, extensively drug-resistant (XDR), and pandrug-resistant (PDR) bacteria.

For Enterobacteriaceae such as Escherichia coli, Salmonella spp., and Shigella spp., MDR assessment considers resistance across antibiotic classes including penicillins, cephalosporins, carbapenems, aminoglycosides, fluoroquinolones, and folate pathway inhibitors. The MDR flag serves as an important clinical indicator of isolate pathogenic potential and treatment complexity.

### Related Studies

This section examines the evolution of computational approaches to antimicrobial resistance (AMR) analysis, tracing the trajectory from supervised prediction paradigms toward unsupervised pattern discovery.

#### The Supervised Learning Era: Achievements and Limitations

The period from 2020 to 2024 witnessed advances in machine learning applications for AMR prediction, with Random Forest emerging as the predominant algorithmic choice. A systematic review found that Random Forest achieved a mean Area Under the Receiver Operating Characteristic (AUROC) of 0.75 across 23 studies, consistently outperforming logistic regression for predicting resistance phenotypes [24]. Yet this success obscures a fundamental limitation: supervised models require labeled training data that environmental surveillance programs rarely possess.

The dependency on pre-existing labels creates an epistemological paradox. High accuracy models for predicting resistance in Mycobacterium tuberculosis and Escherichia coli using genomic features could only classify isolates into categories already defined in training data [24]. When confronted with novel resistance patterns not represented in historical datasets, supervised classifiers fail by design. This limitation proves especially problematic for environmental surveillance under the One Health framework, where resistance patterns in the water-fish-human nexus may differ from clinical reference datasets [10].

The class imbalance problem further constrains supervised methods. Multidrug resistance (MDR) prevalence in surveillance datasets typically ranges from 10-20%, creating minority class prediction challenges that bias models toward susceptible classifications [25]. While stratified cross-validation partially addresses this issue, the underlying problem—insufficient representation of diverse resistance phenotypes— cannot be solved algorithmically when labels themselves are incomplete.

#### Unsupervised Approaches: Emerging Alternatives

Recognition of supervised limitations has prompted methodological diversification toward unsupervised pattern discovery. Affinity Propagation clustering on antibiotic resistance genomic data achieved silhouette coefficients of 0.82, demonstrating that

meaningful phenotypic structure can be discovered algorithmically rather than assumed

from clinical categories [7].

These unsupervised approaches offer conceptual advantages beyond label independence. By clustering isolates based on resistance similarity rather than predefined categories, they can reveal “unknown unknowns”—resistance phenotypes that clinicians have not yet recognized as distinct entities. Hierarchical clustering with Ward’s linkage has been applied to characterize MDR patterns in bacteria from agricultural sources, identifying resistance archetypes that spanned conventional species boundaries [13]. Such cross-species patterns may indicate horizontal gene transfer—a phenomenon invisible to species-specific supervised classifiers.

Spatial epidemiological approaches have emerged concurrently. Spatial panel data analysis of E. coli resistance across 30 Chinese provinces demonstrated significant spatial autocorrelation in cephalosporin, carbapenem, and quinolone resistance [19]. This finding suggests that resistance patterns cluster geographically, potentially reflecting shared anthropogenic pressures.

#### Regional Context: Southeast Asian Surveillance

A comprehensive meta-analysis synthesized 137 studies from 2013-2023, revealing disparities in Enterobacterales resistance across ecological compartments: ceftriaxone resistance reached 49.3% in human, 37.1% in environmental, and 11.2% in animal

E. coli isolates [26]. These findings underscore the need for integrated One Health

surveillance.

Within the Philippines, national surveillance data report E. coli with 43% third-generation cephalosporin resistance and 46% fluoroquinolone resistance [5]. Environmental studies documented MDR E. coli in the Marikina River watershed [27]. Yet these studies employed conventional susceptibility categorization without clusteringbased phenotype discovery.

The Inter-Regional Network Through One Health Approach to Combat Antimicrobial Resistance (INOHAC) AMR Project Two represents the first multi-regional environmental surveillance effort covering Bangsamoro Autonomous Region in Muslim Mindanao (BARMM), Central Luzon, and Eastern Visayas simultaneously [8]. With isolates tested against multiple antibiotics across water, fish, and human sources, this dataset provides unprecedented phenotypic resolution. However, resistance patterns remain characterized only through conventional metrics (MDR prevalence, Multiple Antibiotic Resistance indices) rather than unsupervised phenotype identification—a gap the present study directly addresses.

#### Network and Co-Resistance Perspectives

Network-based approaches have illuminated the genetic architecture of resistance. Gene network analysis identified hub genes that mediate interconnected resistance phenotypes [20]. At the metagenomic scale, antimicrobial resistance gene (ARG) coabundance patterns across 214,095 datasets showed higher correlation in human and animal samples compared to environmental sources [21], suggesting that environmental samples may harbor distinct co-resistance architectures.

Ward’s linkage dendrograms with heatmaps have been employed to characterize pan-resistant healthcare infections, demonstrating that hierarchical visualization reveals antibiotic groupings consistent with pharmacological class [28]. The present study extends this visualization paradigm to environmental isolates.

### Synthesis: The Methodological Gap

The foregoing review reveals a critical methodological gap at the intersection of computational approaches and environmental AMR surveillance.

#### Comparative Summary of Related Studies

Table 1: Comparative Summary of Computational Approaches to AMR Analysis

The current study uniquely integrates unsupervised pattern discovery with supervised validation for multi-regional environmental surveillance.

Limitations of Existing Approaches. Supervised methods achieve high accuracy but cannot identify novel resistance patterns absent from training data. Unsupervised clustering, while effective in agricultural and clinical settings, has rarely been applied to multi-regional One Health surveillance. Spatial epidemiology operates on

aggregated metrics rather than phenotypic profiles. Philippine surveillance has relied on conventional MDR classification, leaving the INOHAC dataset’s pattern discovery potential unrealized.

The Present Study’s Contribution. This study addresses these gaps through a hybrid unsupervised-supervised framework for environmental AMR surveillance. Ward’s hierarchical clustering discovers resistance archetypes without predefined labels, while Random Forest classification validates whether clusters represent biologically coherent structures. Applying this methodology to isolates spanning multiple Philippine regions and ecological compartments (water, fish, human) enables characterization of resistance phenotypes specific to the One Health nexus. This integrated approach advances beyond purely supervised prediction or unsupervised clustering alone, offering a reproducible framework for future surveillance studies.

---

## Chapter 3: THEORETICAL FRAMEWORK

### Introduction

This chapter establishes the theoretical foundations underpinning the development of a pattern recognition system for antimicrobial resistance (AMR) within the Water–Fish– Human nexus. The theoretical framework draws from three interconnected domains: (1) computational pattern recognition theory, (2) public health surveillance epistemology, and (3) software systems design principles. Together, these foundations provide the intellectual scaffolding for addressing the methodological challenges identified in the Statement of the Problem and justify the design decisions implemented in the Architectural Design.

### Primary Theoretical Foundations

#### Pattern Recognition Theory

The primary theoretical foundation of this study is Pattern Recognition Theory, as formalized by Duda, Hart, and Stork [29] in their seminal work Pattern Classification. Pattern recognition is defined as the automatic discovery of regularities in data through the use of computational algorithms, with the aim of classifying or describing observations based on learned representations rather than explicit rules.

This theory is operationalized in the present study through the integration of

unsupervised and supervised learning paradigms:

Table 2: Learning Paradigms in Pattern Recognition

The theoretical justification for combining both paradigms derives from the cluster validation problem articulated by Jain and Dubes [30]: unsupervised methods alone cannot guarantee that discovered structures are meaningful, coherent, or reproducible. Supervised validation provides an external mechanism for assessing whether clusters represent genuinely separable phenotypic categories.

### Hierarchical Clustering Theory

Ward’s minimum variance method, employed in this study, is grounded in the theoretical principle of within-cluster homogeneity maximization [13]. The method iteratively merges clusters to minimize the total within-cluster sum of squares, producing dendrograms that reveal multi-scale structure in high-dimensional data. This approach is particularly appropriate for ordinal resistance data (S/I/R encoded as 0/1/2), where Euclidean distance preserves the progressive nature of resistance severity.

#### One Health Framework

The One Health Framework provides the domain-specific theoretical context for situating antimicrobial resistance within interconnected environmental, animal, and human health systems. Endorsed by the World Health Organization (WHO), Food and

Agriculture Organization (FAO), and World Organisation for Animal Health (WOAH),

One Health recognizes that:

““The health of people is closely connected to the health of animals and our

shared environment” [9].”

The Water–Fish–Human nexus examined in this study represents a concrete

instantiation of One Health principles, tracing antimicrobial resistance across:

- Water systems (drinking water, lake water, river water, effluent discharge)
- Aquaculture (fish species: Banak, Gusaw, Tilapia, Kaolang)
- Anthropogenic interfaces (treated/untreated effluent from healthcare facilities) The One Health Framework justifies the study’s focus on environmental reservoirs

as sites of AMR emergence and dissemination, while simultaneously constraining the study’s interpretive scope: the framework emphasizes interconnection and surveillance rather than causal attribution. This theoretical position aligns with the study’s commitment to associational rather than causal language.

### Supporting Theoretical Concepts

#### Information Leakage Theory in Machine Learning

A critical supporting concept is Information Leakage Theory, which addresses the methodological risk of inadvertently incorporating information from test data into model training, leading to overoptimistic performance estimates [32]. Leakage violates the fundamental assumption of independent and identically distributed (i.i.d.) training and evaluation sets.

The study operationalizes leakage prevention through two architectural constraints derived from this theory:

Table 3: Leakage Types and Architectural Mitigations

These constraints are not merely procedural but reflect the theoretical requirement that evaluation metrics must estimate generalization error on truly unseen data.

#### Ordinal Data Representation Theory

The encoding of antimicrobial susceptibility results (Susceptible/Intermediate/Resistant) as ordinal numerical values (0/1/2) is grounded in Ordinal Data Theory [33]. Ordinal variables possess natural ordering but lack equidistant intervals between categories.

The choice of Euclidean distance for clustering ordinal resistance data is justified by research demonstrating that, for low-dimensional ordinal spaces with consistent encoding, Euclidean distance approximates ordinal dissimilarity with acceptable distortion [34]. Alternative distance metrics (e.g., Gower distance, Manhattan distance) were considered; the study’s stability analysis using Adjusted Rand Index (ARI) across alternative configurations validates the robustness of the Euclidean-based solution.

#### Multi-Drug Resistance Classification Theory

The classification of isolates as multidrug-resistant (MDR) follows the standardized definition established by Magiorakos et al. [23]:

“An isolate is classified as MDR if it exhibits acquired non-susceptibility to at

least one agent in three or more antimicrobial categories.”

This definition provides a theoretically grounded, internationally recognized framework for categorizing resistance breadth. The study’s computation of MDR status as a derived feature operationalizes this definition, enabling downstream analysis of resistance pattern associations.

### The Variable Connection: From Data to Design

The relationship between research findings (independent variables) and design features (dependent variables) follows a structured derivation process grounded in the theoretical frameworks above.

#### Independent Variables (Research/Data)

The independent variables in this study comprise the phenotypic antimicrobial susceptibility testing (AST) data:

Table 4: Independent Variables

#### Dependent Variables (Design Features)

The dependent variables are the architectural design features implemented in the system:

Table 5: Dependent Variables (Design Features)

#### The Derivation Chain

The following derivation chain traces how theoretical principles translate into design decisions:

Table 6: Derivation Chain from Theory to Design

### Theoretical Justification

#### Why Pattern Recognition Theory?

Pattern Recognition Theory is the most appropriate primary lens for this study because the Statement of the Problem explicitly identifies the limitation of predefined categorical labels in constraining the discovery of latent resistance structures. Pattern recognition, by definition, seeks to discover regularities that are not explicitly encoded in the data representation. The unsupervised component (hierarchical clustering) allows resistance patterns to emerge from phenotypic similarity rather than being imposed by external classification schemes.

Furthermore, the integration of supervised validation addresses the acknowledged weakness of unsupervised methods: the lack of external criteria for evaluating cluster quality. The theoretical framework thus provides both the mechanism for discovery (unsupervised learning) and the mechanism for validation (supervised learning), directly responding to the dual challenges articulated in the SOP.

#### Why One Health Framework?

The One Health Framework is essential for situating the study within the broader public health discourse on antimicrobial resistance. The Water–Fish–Human nexus is not an arbitrary data structure but a theoretically motivated representation of interconnected reservoirs where resistance genes and resistant organisms circulate.

Critically, the One Health Framework also provides epistemic constraints: it emphasizes surveillance, monitoring, and characterization rather than causal inference. This aligns with the study’s commitment to associational language and its explicit avoidance of claims regarding resistance emergence mechanisms or transmission pathways. The theoretical framework thus serves both a constructive function (justifying the nexus perspective) and a regulatory function (constraining interpretive claims).

#### Why Information Leakage Theory?

The explicit incorporation of Information Leakage Theory distinguishes this study from naive applications of machine learning to biological data. The Statement of the Problem implicitly acknowledges the risk of methodological artifacts when it notes that unsupervised clustering alone provides “limited assurance” of coherent patterns. Information Leakage Theory provides the conceptual vocabulary for articulating these risks and the design principles for mitigating them.

The Split-Before-Transform protocol and Feature–Metadata Separation are not arbitrary design choices but theoretically mandated safeguards against a recognized class of methodological errors. By grounding these architectural decisions in established

theory, the study demonstrates awareness of machine learning pitfalls and implements principled solutions.

### Conceptual Framework

The conceptual framework synthesizes the theoretical foundations and supporting concepts into an integrated model that guides the study’s analytical design and implementation. This framework establishes the logical flow from abstract theoretical principles to concrete architectural decisions, ensuring methodological coherence throughout the research process.

Figure 1: Conceptual Framework Diagram: Integration of Theoretical Foundation, Conceptual Domain, Implementation Framework, and Research Outputs

Figure 1 illustrates four interconnected components that structure this study’s analytical

approach:

- Theoretical Foundation: Pattern Recognition Theory provides the computational paradigm for discovering latent resistance structures, while the One Health Frame-

work situates AMR within the Water-Fish-Human nexus.

- Conceptual Domain: Abstract principles are operationalized into methodological constraints—cluster validation, information leakage prevention through split-beforetransform protocols, ordinal S/I/R encoding (0/1/2), and standardized MDR classi-

fication following Magiorakos et al.

- Implementation Framework: A three-tier architecture (Data, Analysis, and Presentation Components) implements the validation pipeline: unsupervised discovery via Hierarchical Agglomerative Clustering with Ward’s method, supervised validation using Logistic Regression, Random Forest, and k-NN classifiers, and stability

assessment through Adjusted Rand Index and Silhouette scores.

- Research Outputs: Validated resistance profiles, regional surveillance insights, and

clinical workflow support.

The directional flow progresses from theoretical justification through operationalization to implementation, with outputs providing empirical validation that informs the theoretical understanding of AMR patterns.

### Chapter Summary

This chapter established the theoretical foundations for the AMR pattern recognition system developed in this study. The primary theoretical frameworks—Pattern Recognition Theory and One Health Framework—provide complementary lenses for addressing the computational and domain-specific challenges identified in the Statement of the Problem.

Supporting concepts including Information Leakage Theory, Ordinal Data Representation, and Supervised Validation Theory operationalize these frameworks

into specific methodological and architectural constraints. The derivation chain demonstrates how each design feature in the Architectural Design chapter traces back to established theoretical principles.

The theoretical framework ensures that the study’s contributions are grounded in recognized scholarly traditions while maintaining methodological rigor appropriate to machine learning applications in public health surveillance.

---

## Chapter 4: METHODOLOGY

### Research Design

This study adopts an exploratory, computational research design grounded in pattern recognition and machine learning to address the stated research objectives. The design is exploratory because it seeks to uncover latent antimicrobial resistance (AMR) structures that are not explicitly defined by existing categorical labels, rather than testing predefined hypotheses or establishing causal relationships. It is computational in nature because the primary contribution of the study lies in the design, implementation, and evaluation of a data-driven analytical framework for resistance pattern discovery and validation.

The research design integrates unsupervised learning for resistance structure discovery with supervised learning used exclusively as an external validation mechanism. Unsupervised methods are employed to identify resistance patterns based solely on phenotypic similarity in antimicrobial susceptibility testing (AST) data, without incorporating biological, environmental, or geographic labels during the discovery phase. Supervised learning is subsequently applied to assess the discriminative capacity and robustness of the discovered patterns, thereby addressing the limitations of unsupervised clustering when used in isolation.

The methodological strategy follows a staged, leakage-aware pipeline consisting of: (1) data preprocessing and feature engineering, (2) unsupervised resistance pattern discovery, (3) supervised validation, (4) integrated system design, and (5) quantitative evaluation. Throughout the study, strict separation is maintained between pattern discovery and interpretation to prevent information leakage and circular reasoning. The

study is associational and descriptive in scope; no biological mechanisms, epidemiological transmission pathways, or clinical outcomes are inferred.

### Data Source and Description

#### Dataset Origin

The dataset analyzed in this study was generated by the INOHAC AMR Project Two research team as part of an environmental antimicrobial resistance surveillance initiative. The present study does not involve primary sampling or laboratory experimentation. All analyses are conducted as a secondary analysis of phenotypic AST data collected by the source project. The dataset comprises AST results for bacterial isolates obtained from environmental and aquaculture-associated sources across three geographic regions in the Philippines: Eastern Visayas, Central Luzon, and the Bangsamoro Autonomous Region in Muslim Mindanao (BARMM).

#### Sample Source Categories

Isolates originate from environmental matrices representing the Water–Fish interface within the broader Water–Fish–Human nexus. These source categories capture exposure pathways relevant to environmental AMR dissemination and are used exclusively as contextual metadata during interpretation. Source categories are listed in Table 7.

Table 7: Sample Source Categories

Note: While direct human clinical isolates are not included, effluent water samples (EWU, EWT) represent the anthropogenic component of the nexus, capturing resistance patterns potentially influenced by human antibiotic use and healthcare facility discharge.

#### Isolate Identification Convention

Each isolate is assigned a structured alphanumeric identifier encoding species, geographic origin, source type, replicate number, and colony number using the format: [Species Prefix]_[Region][Site][Source][Replicate]C[Colony]

This convention enables systematic metadata parsing while preserving traceability

throughout the analytical pipeline.

#### Antimicrobial Panel

Phenotypic AST data consists of a panel of 22 antibiotics spanning 12 antimicrobial classes, including an ESBL screening indicator. The antimicrobial panel is summarized in Table 8.

Table 8: Antimicrobial Panel Composition

### Data Preprocessing and Feature Engineering

The objective of this phase is to transform heterogeneous raw antimicrobial susceptibility testing (AST) records into a structured numerical form that supports similaritybased analysis while preserving biologically meaningful resistance information. All preprocessing decisions are explicitly parameterized to ensure reproducibility and to prevent information leakage in downstream analyses.

#### Data Ingestion and Harmonization

Raw phenotypic AST data are consolidated from multiple source files provided by the INOHAC–Project 2. These files, supplied as comma-separated value (CSV) datasets corresponding to different collection sites, are integrated into a single unified dataset.

The ingestion process includes the following steps:

- Schema harmonization: Column names, data types, and value encodings are standardized across source files to ensure structural consistency.
- Metadata extraction: Structured isolate identifiers are parsed to extract contextual variables such as geographic region, local site, source category, replicate number, and colony number.
- Duplicate resolution: Duplicate isolate records are identified and removed to ensure

a one-to-one correspondence between isolates and resistance profiles.

This step ensures that all downstream analyses operate on a coherent and internally consistent dataset.

#### Data Quality Filtering

To ensure sufficient data completeness for reliable pattern recognition, threshold-based filtering criteria were applied at both the antibiotic and isolate levels.

- Antibiotic-level filtering: Antibiotics tested on fewer than 70% of isolates were excluded to ensure adequate representation across resistance profiles.
- Isolate-level filtering: Isolates with more than 30% missing susceptibility values

were removed to avoid excessive reliance on imputation.

These thresholds balance data retention with analytical reliability and are consistent with exploratory machine learning practices applied to high-dimensional biological data. All thresholds are established beforehand to avoid after-the-fact adjustments based on results. Antibiotics failing to meet the 70% coverage threshold are excluded from subsequent analysis.

#### Resistance Encoding

Phenotypic AST outcomes recorded as categorical values—Susceptible (S), Intermediate (I), and Resistant (R)—are converted into ordinal numerical representations to support quantitative analysis.

Table 9: Ordinal Encoding of Phenotypic AST Results

This ordinal encoding preserves the progressive nature of resistance severity while enabling distance-based computations.

#### Missing Value Imputation

Following threshold-based exclusion, remaining missing susceptibility values are imputed using median imputation, applied independently to each antibiotic feature:

x̂(i,j) = median({x(k,j) | x(k,j) is observed})

where x̂(i,j) is the imputed resistance value for isolate i and antibiotic j, and x(k,j) represents observed resistance values for antibiotic j.

Median imputation is robust to outliers and preserves the ordinal nature of resistance data. Alternative strategies such as mean or mode imputation are considered; however, the median provides a conservative central estimate suitable for exploratory pattern recognition.

#### Derived Resistance Feature Computation

To support downstream interpretation and epidemiological contextualization, several derived resistance descriptors are computed. These features are not included as inputs to unsupervised clustering to prevent bias during pattern discovery.

### Multiple Antibiotic Resistance (MAR) Index

The MAR index quantifies the proportion of antibiotics to which an isolate exhibits

resistance:

MAR = a/b, where *a* is the number of antibiotics for which resistance is observed (encoded value = 2), and *b* is the total number of antibiotics tested for the isolate.

### Interpretation:

- MAR ≤ 0.2: Low-risk source
- MAR > 0.2: High-risk source, indicative of antibiotic selection pressure

### Resistant Classes Count

The breadth of resistance across antimicrobial classes was computed as:

Resistant Classes = |{c | ∃a ∈ c, resistance(a) = true}|

where c denotes an antimicrobial class and a denotes an antibiotic belonging to that class.

This metric captures class-level resistance diversity rather than resistance to

individual agents.

### Multidrug Resistance (MDR) Classification

An isolate is classified as multidrug-resistant (MDR) if resistance is observed in three

or more antimicrobial classes, consistent with established definitions [23]:

MDR = 1 if Resistant Classes ≥ 3, otherwise 0

#### Feature–Metadata Separation

To prevent information leakage and circular reasoning, the analysis-ready dataset is explicitly partitioned into two components:

- Feature Matrix (X): Encoded resistance values for the 22 antibiotics, used exclusively for unsupervised clustering and supervised validation.
- Metadata Matrix (M): Contextual variables (e.g., region, site, species, source category, MDR status), reserved solely for post-discovery interpretation.

This separation ensures that resistance patterns are discovered strictly from phenotypic

similarity and are not influenced by external labels or contextual information.

#### Preprocessing Component Output

The output of the preprocessing component consists of:

- Analysis-ready resistance feature matrix with encoded susceptibility values
- Derived resistance indicators (MAR, Resistant Classes, MDR status)
- Separated metadata matrix for post-hoc interpretation
- Data quality documentation including filtering statistics

### Unsupervised Structure Discovery

The objective of this phase is to identify latent resistance structures based solely on phenotypic similarity in antimicrobial susceptibility profiles, without incorporating predefined biological, environmental, or geographic labels. All analyses in this section operate exclusively on the resistance feature matrix produced during preprocessing.

#### Clustering Algorithm Selection

Hierarchical Agglomerative Clustering (HAC) was selected as the primary unsupervised learning method due to the following properties:

- Exploratory suitability: Unlike partition-based methods (e.g., k-means) that require a priori specification of k, HAC constructs a complete hierarchical structure first, deferring cluster number selection to post-hoc analysis using data-driven validation metrics (silhouette coefficient, WCSS elbow analysis).
- Multi-scale structure discovery: The hierarchical representation enables examination of resistance patterns at multiple levels of granularity.
- Interpretability: Dendrograms provide transparent visualization of cluster formation and merge decisions.
- Minimal structural assumptions: HAC does not impose assumptions regarding

cluster shape or distribution.

These characteristics make HAC appropriate for exploratory pattern recognition in highdimensional resistance data.

#### Distance Metric

Euclidean distance is used as the primary measure of dissimilarity between resistance profiles:

d(x, y) = √Σ(i=1 to n)(xi - yi)²

where x and y are resistance vectors for two isolates and n is the number of antibiotics.

This metric is selected because it preserves proportional differences introduced by ordinal resistance encoding (S = 0, I = 1, R = 2) and is compatible with variance-based linkage methods such as Ward’s criterion. Given the 22-dimensional feature space— where the number of features is substantially smaller than the sample size—Euclidean distance remains effective without dimensionality reduction.

#### Linkage Method

Ward’s minimum variance linkage method is used to guide cluster merging:

Δ(A, B) = (nA × nB) / (nA + nB) × ||cA - cB||²

where:

- nA and nB denote the sizes of clusters A and B,
- cA and cB represent their respective centroids.

Ward’s method minimizes the increase in total within-cluster variance at each merge step, producing compact and relatively balanced clusters. This property is advantageous for identifying resistance phenotypes that are internally coherent and externally separable in feature space.

#### Determination of the Number of Clusters

The optimal number of clusters is determined using a data-driven, multi-criteria approach combining quantitative metrics with practical constraints, following established conventions for exploratory cluster analysis [35], [36].

### Silhouette Analysis

Cluster cohesion and separation were evaluated using the silhouette score [16]:

s(i) = (b(i) - a(i)) / max(a(i), b(i))

where:

- a(i) is the mean intra-cluster distance for isolate i,
- b(i) is the mean distance to the nearest neighboring cluster.

Higher silhouette values indicate better-defined cluster structure, with scores ≥ 0.40

representing moderate-to-strong structure [17]. The average silhouette score across all isolates is computed for cluster solutions ranging from k = 2 to k = 8, a range consistent with recommendations for systematic cluster validation [35].

### Within-Cluster Sum of Squares (WCSS)

Cluster compactness is assessed using the within-cluster sum of squares:

WCSS = Σ(k=1 to K) Σ(x∈Ck) ||x - μk||²

where Ck denotes cluster k and μk its centroid. The elbow method is used to identify diminishing returns in compactness as the number of clusters increased [36].

### Practical Constraints

To ensure reproducibility and meaningful biological interpretation, the following

methodological constraints guided cluster number selection:

- Sample size requirement: A minimum of 20 isolates per cluster was mandated to permit reliable estimation of cluster-level resistance profiles, consistent with recommendations for 20–30 samples per subgroup in clustering analysis [37], [38].
- Granularity control: Excessive partitioning was avoided to preserve phenotypically

coherent resistance groupings amenable to downstream interpretation.

Final cluster selection employs a multi-objective decision framework, prioritizing the elbow point when it satisfied both silhouette and stability criteria, with parsimony as a secondary consideration when multiple solutions were statistically valid [17].

#### Cluster-Level Profile Characterization

For each identified cluster, a resistance profile was computed summarizing the dominant phenotypic characteristics:

- Mean resistance score per antibiotic (0–2 scale)
- Resistance prevalence (proportion of isolates with R classification per antibiotic)
- Class-level resistance summary aggregating across antimicrobial categories

These profiles enable qualitative characterization of each cluster’s resistance signature.

#### Unsupervised Discovery Output

The output of this phase consists of:

- Final cluster assignments for each isolate
- Hierarchical linkage matrices and dendrograms
- Cluster-level resistance profiles summarizing dominant phenotypic patterns

These outputs form the basis for supervised validation and interpretation, while remaining independent of external biological or contextual labels during discovery.

### Supervised Learning Validation

Supervised learning models are used solely to validate the discriminative capacity of the discovered resistance patterns. This phase implements leakage-safe train–test splitting, macro-averaged evaluation metrics, confusion matrix analysis, feature importance extraction, and cross-seed stability checks.

#### Classification Task

Supervised classification is designed to validate the unsupervised clustering results by assessing whether the discovered clusters represent discriminable resistance phenotypes:

Table 10: Supervised Classification Task

#### Leakage-Safe Data Splitting

To prevent information leakage between training and evaluation phases, the dataset is first partitioned into training (80%) and test (20%) subsets using stratified sampling

to preserve class distributions. Train–test splitting is performed prior to any prepro-

cessing operations, including missing value imputation and feature scaling.

All preprocessing steps are fitted exclusively on the training data, and the learned parameters are subsequently applied unchanged to both the training and test sets. This ensures that statistical properties of the test data do not influence model training, thereby preventing optimistic bias in supervised evaluation metrics.

#### Model Selection

Three classifier families are selected to represent different learning paradigms:

Table 11: Supervised Model Selection

### Hyperparameter Configuration:

Table 12: Model Hyperparameters

#### Evaluation Metrics

Performance is quantified using macro-averaged metrics to prevent class imbalance bias:

### Macro-Averaged Precision, Recall, F1

- Precision = (1/|C|) × Σ(c∈C) TPc / (TPc + FPc)
- Recall = (1/|C|) × Σ(c∈C) TPc / (TPc + FNc)
- F1 = 2 × (Precision × Recall) / (Precision + Recall)

where C is the set of classes and TP, FP, FN are true positives, false positives, and false negatives respectively.

### Accuracy

Overall classification correctness is measured as:

Accuracy = (TP + TN) / (TP + TN + FP + FN)

### Confusion Matrix

Per-class classification performance is visualized using confusion matrices to identify species-specific misclassification patterns.

#### Feature Importance Extraction

For Random Forest models, feature importance is extracted using Gini impurity:

Importance(f) = Σ(t∈T) ΔGt × 𝟙[ft = f]

where ΔGt is the decrease in Gini impurity at node t when feature f is used for splitting.

Language Discipline: Feature importance reflects associative relationships within the dataset. High importance indicates statistical association, not causal influence on resistance phenotype.

#### Stability Across Random Seeds

Model stability is validated across multiple random states to ensure that model performance is not dependent on a specific random initialization:

Algorithm 1: Cross-Seed Stability Check Algorithm

1: Input: Dataset D, Prediction Model M, Random Seeds S = {42, 123, 456, 789, 1011}
2: Output: Stability metrics (μ_metrics, σ_metrics)
3: R = ∅ (Initialize results container)
4: For each seed s ∈ S do:
5:   Set global random state to s
6:   Split D into D_train (80%) and D_test (20%) using stratified sampling
7:   Train M on D_train
8:   Evaluate M on D_test to obtain metric vector vs
9:   Append vs to R
10: Compute mean μ = (1/|S|) × Σ(v∈R) v
11: Compute standard deviation σ = √[(1/(|S|-1)) × Σ(v∈R) (v - μ)²]
12: Return μ, σ

Low standard deviation across seeds indicates robust model performance.

#### Sensitivity Analysis: Split Ratio and Cross-Validation

To justify the train–test split configuration, a sensitivity analysis is conducted comparing different partitioning strategies. Three split ratios (70/30, 80/20, 90/10) and two crossvalidation schemes (5-fold, 10-fold) are evaluated across all three classifier models to determine the optimal balance between training adequacy and evaluation reliability.

### Sensitivity Analysis Interpretation

The sensitivity analysis provides the following rationale for the chosen experimental

configuration:

- Stability Assessment: Standard deviations are analyzed across random seeds to ensure that the discriminative capacity is not an artifact of random initialization.
- 80/20 Split Rationale: The 80/20 split is selected as it provides a statistically reliable test set size (≈98 samples) while maintaining sufficient training data, balancing

model learning capacity with robust evaluation.

- Cross-Validation Selection: 5-fold and 10-fold cross-validation produce comparable stability. Given the computational efficiency of 5-fold CV, it is preferred for the

full experimental pipeline.

- Model Selection: Random Forest is selected as the primary validation model due to its consistently stable performance and its ability to provide interpretable feature

importance through Gini impurity.

These findings support the use of the 80/20 train–test split with Random Forest and 5-fold cross-validation as the robust standard configuration for supervised validation.

#### Supervised Validation Output

The output of this phase consists of:

- Classification performance metrics for each model and task
- Confusion matrices for per-class analysis
- Feature importance rankings from Random Forest
- Cross-seed stability statistics
- Sensitivity analysis results across split configurations
- Serialized model artifacts for deployment (.joblib)
- Structured feature importance data for dashboard integration (.json)

### Statistical Association Analysis

To characterize the relationships between resistance patterns and external variables, rigorous statistical association methods are employed.

#### Co-Resistance Analysis

Antibiotic co-resistance patterns are quantified using the phi coefficient (φ), calculated from binary resistance co-occurrence tables:

φ = (ad - bc) / √[(a+b)(c+d)(a+c)(b+d)]

where a, b, c, and d represent the counts in a 2×2 contingency table of resistance presence and absence between two antibiotics.

Table 13: Phi Coefficient Contingency Table Structure

Antibiotic clustering based on co-resistance similarity is subsequently performed using hierarchical clustering with distance defined as 1 - φ.

#### Metadata Association Analysis

Associations between resistance clusters and metadata variables are evaluated using Cramér's V, computed as:

V = √[χ² / (n × min(r-1, c-1))]

where χ² is the chi-square statistic, n is the sample size, and r and c are the dimensions of the contingency table.

Table 14: Cramér’s V Interpretation Guidelines [1]

#### Interpretation Protocol

Interpretation follows a strict staged interpretation strategy to maintain analytical integrity:

- Clusters are generated using resistance features only (Unsupervised Discovery)
- Metadata are overlaid after clustering for descriptive analysis
- Statistical associations are reported using associational language only
- No causal claims are made regarding resistance emergence or transmission

This protocol ensures that interpretive conclusions remain within the methodological scope of the study.

### Ethical Considerations

This study involved the secondary analysis of environmental and aquaculture-associated bacterial isolates. No human subjects, clinical samples, or personal identifiers were included in the dataset. The dataset was anonymized prior to analysis, and all results are reported at an aggregate level. Ethical approval was therefore not required for this computational study.

### Limitations

The following methodological limitations are acknowledged:

- Scope limitation: The dataset represents the Water–Fish interface; direct human clinical isolates are not included, limiting generalizability to the full Water–Fish–

Human nexus.

- Temporal limitation: The study analyzes a single cross-sectional dataset; temporal

dynamics of resistance evolution cannot be assessed.

- Imputation effects: Median imputation may introduce bias for antibiotics with

highly skewed resistance distributions.

- Clustering assumptions: Ward’s linkage assumes spherical clusters and may not

capture non-convex resistance pattern structures.

- External validation: Supervised validation assesses internal discriminative capacity but does not validate against external AMR surveillance datasets.

### Chapter Summary

This chapter presented a comprehensive, leakage-aware methodology for antimicrobial resistance pattern recognition using phenotypic AST data. The framework integrates unsupervised discovery, supervised validation, co-resistance analysis, and system-level evaluation while maintaining strict interpretive discipline.

The methodology establishes a rigorous analytical pipeline that transforms raw AST data into validated resistance patterns through unsupervised discovery, supervised validation, and statistical association analysis. This approach ensures that resistance structures emerge from objective, data-driven processes while maintaining strict separation between pattern discovery and biological interpretation throughout all analytical stages.

The methodology ensures that resistance patterns are discovered through objective, data-driven processes and that all interpretive statements remain within appropriate associational bounds. The integrated framework supports reproducible execution and interactive exploration of results.

---

## Chapter 5: ARCHITECTURAL DESIGN

### Introduction

This chapter presents the architectural design of the Antimicrobial Resistance (AMR) Pattern Recognition System. The system follows a layered pipeline architecture that transforms raw Antimicrobial Susceptibility Testing (AST) data into actionable insights through a series of well-defined processing stages. The architecture emphasizes modularity, reproducibility, and scientific rigor—ensuring that each component can be independently validated and that the analytical pipeline produces defensible results for clinical and epidemiological applications.

The system architecture comprises four primary stages: (1) Raw Data Input,

(2) Data Preprocessing, (3) Pattern Discovery, and (4) Output Visual Representation. Each stage is designed with clear inputs, outputs, and transformation logic, enabling traceability from raw laboratory data to final analytical conclusions.

### Overall System Architecture

The AMR Pattern Recognition System implements a pipeline architecture where data flows sequentially through preprocessing stages before branching into three parallel pattern discovery methods. The results from each analytical approach are then consolidated into unified visual representations for interpretation.

Figure 2: Overall System Architecture

#### Architecture Components Overview

The overall architecture consists of the following major components:

Table 15: Architecture Components Overview

The architecture employs a fan-out pattern at the Pattern Discovery stage, where the preprocessed data is simultaneously processed by three independent analytical methods. This design ensures that findings can be cross-validated across different methodological approaches, strengthening the scientific validity of conclusions.

### Data Preprocessing Stage

The Data Preprocessing stage transforms heterogeneous raw AST data into a standardized, analysis-ready dataset. This stage is critical for ensuring data quality,

reproducibility, and downstream analytical validity. The preprocessing pipeline consists of four sequential sub-stages: Data Ingestion, Data Cleaning, Resistance Encoding, and Feature Engineering.

Figure 3: Data Preprocessing Stage Architecture

#### Data Ingestion

The Data Ingestion sub-stage consolidates AST records from multiple regional surveillance sites into a unified dataset. The system processes CSV files from three Philippine regions: BARMM (Bangsamoro Autonomous Region in Muslim Mindanao), Region III (Central Luzon), and Region VIII (Eastern Visayas).

### Key Operations:

- Load Multiple CSV Files: Iteratively reads all CSV files from the raw data directory using glob pattern matching
- Unify Datasets: Concatenates individual dataframes into a master dataset while preserving source metadata (region, facility, collection date)
- Standardize Column Names: Normalizes column naming conventions and applies species standardization mappings to ensure taxonomic consistency

#### Data Cleaning

The Data Cleaning sub-stage ensures data quality by addressing missing values, invalid entries, and format inconsistencies that could compromise analytical validity.

### Key Operations:

- Handle Missing Values: Identifies and documents missing AST results; applies coverage thresholds to determine acceptable missingness levels
- Remove Invalid Entries: Excludes records with ambiguous species identification or incomplete metadata required for stratified analysis
- Standardize Data Formats: Normalizes date formats, categorical values, and text fields to ensure consistency
- Filter by Coverage Thresholds: Retains only antibiotics and isolates meeting minimum testing coverage requirements (≥70% antibiotic coverage, ≤30% missing values per isolate)

#### Resistance Encoding

The Resistance Encoding sub-stage transforms categorical AST interpretations into numerical values suitable for computational analysis.

### Key Operations:

- Convert S/I/R to Numerical: Applies ordinal encoding where Susceptible (S) = 0, Intermediate (I) = 1, and Resistant (R) = 2
- Create Encoded Columns: Generates new columns with _encoded suffix containing numerical values while preserving original categorical data
- Validate Encoding Range: Verifies all encoded values fall within expected range [0, 1, 2] and flags anomalies

#### Feature Engineering

The Feature Engineering sub-stage derives clinically meaningful indicators from the encoded resistance profiles.

### Key Operations:

- Select Encoded Antibiotic Columns: Identifies all _encoded columns to form the resistance fingerprint vector
- Calculate MAR Index: Computes the Multiple Antibiotic Resistance Index using the formula MAR = a/b, where a = number of antibiotics to which the isolate is resistant, and b = total antibiotics tested [22]
- Determine MDR Status: Classifies isolates as Multi-Drug Resistant (MDR) if resistant to at least one agent in ≥3 antimicrobial categories [23]
- Create Feature Matrix: Assembles the final feature matrix (X) containing encoded resistance values for all tested antibiotics

### Pattern Discovery Stage

The Pattern Discovery stage applies three complementary analytical methods to identify, validate, and characterize antimicrobial resistance patterns. Each method addresses a distinct analytical objective while providing cross-validation opportunities. The stage receives the analysis-ready dataset from preprocessing and produces cluster assignments, validation metrics, and association scores.

#### Unsupervised Clustering

The Unsupervised Clustering component identifies natural groupings in resistance patterns without predefined categories. This data-driven approach discovers resistance phenotypes—characteristic patterns of antibiotic susceptibility that may correspond to underlying biological or epidemiological phenomena.

Figure 4: Unsupervised Clustering Architecture

### Optimal k Selection

Before clustering, the optimal number of clusters (k) must be determined through

systematic evaluation.

### Key Operations:

- Elbow Method Analysis: Plots Within-Cluster Sum of Squares (WCSS) against cluster count; identifies the “elbow point” where additional clusters yield diminishing returns in variance reduction
- Silhouette Score Analysis: Computes silhouette coefficients for different k values; higher scores indicate better-defined cluster boundaries
- Determine Best k Value: Synthesizes elbow and silhouette analyses with domain knowledge to select the optimal cluster count

### Hierarchical Clustering

The system employs Hierarchical Agglomerative Clustering (HAC) to group isolates

based on resistance profile similarity.

### Key Operations:

- Apply Ward’s Linkage Method: Uses Ward’s minimum variance criterion to minimize within-cluster variance at each merge step, producing compact and wellseparated clusters [12]
- Use Euclidean Distance: Computes pairwise distances between isolates using Euclidean metric, appropriate for numerical resistance vectors and required by Ward’s linkage
- Generate Cluster Assignments: Cuts the dendrogram at the optimal level to assign each isolate to a specific cluster

### Quality Metrics

Cluster quality is assessed through internal validation metrics that quantify cluster

coherence and separation.

### Key Operations:

- Calculate Silhouette Score: Measures how similar isolates are to their own cluster compared to other clusters; values range from −1 to +1, with higher values indicating better clustering
- Calculate WCSS: Computes total within-cluster sum of squares as a measure of cluster compactness
- Validate Cluster Quality: Evaluates metrics against established thresholds to confirm clustering validity

#### Supervised Validation

The Supervised Validation component tests whether discovered clusters represent meaningful, predictable patterns. By training machine learning classifiers to predict cluster membership from resistance profiles, this stage validates that clusters capture genuine structure rather than random variation.

Figure 5: Supervised Validation Architecture

### Data Preparation

The clustered dataset is prepared for supervised learning by extracting features and

encoding target labels.

### Key Operations:

- Filter Valid Samples: Removes isolates with missing cluster assignments to ensure complete target labels
- Extract Resistance Fingerprints: Selects only _encoded antibiotic columns as features (X), explicitly excluding metadata to prevent data leakage
- Encode Target Labels: Converts categorical cluster identifiers to numerical labels using LabelEncoder for model compatibility

### Train-Test Split

The dataset is partitioned into training and testing subsets to enable unbiased perfor-

mance evaluation.

### Key Operations:

- 80% Training Set: Used for model fitting and hyperparameter tuning
- 20% Testing Set: Held out for final performance evaluation; models never see this data during training
- Stratified Splitting: Ensures proportional representation of each cluster in both subsets

### Preprocessing Pipeline

A leakage-safe preprocessing pipeline transforms features using statistics derived only

from training data.

### Key Operations:

- Fit Imputer on Train: Learns median values from training data to fill missing antibiotic results
- Fit Scaler on Train: Computes mean and standard deviation from training data for standardization
- Transform Training Data: Applies fitted transformations to training features
- Transform Testing Data: Applies the same transformations (using training statistics) to test features, preventing data leakage from test set into preprocessing

### Model Training

Three classifier architectures are trained to predict cluster membership, each offering

different analytical perspectives.

### Key Operations:

- Logistic Regression: Linear baseline model providing interpretable coefficients and establishing minimum expected performance
- Random Forest: Ensemble of decision trees capturing non-linear patterns and providing feature importance rankings
- K-Nearest Neighbors: Distance-based classifier validating that clusters occupy distinct regions in feature space
- Stratified K-Fold CV: Cross-validation on training set to assess model stability and tune hyperparameters

### Model Evaluation

All performance metrics are computed exclusively on the held-out test set to provide

unbiased estimates of generalization performance.

### Key Operations:

- Calculate Accuracy: Overall proportion of correct cluster predictions on test set
- Calculate Macro Precision/Recall/F1-Score: Per-cluster metrics averaged equally to prevent class imbalance bias
- Generate Confusion Matrix: Detailed breakdown showing which clusters are correctly classified or confused
- Extract Feature Importance: Identifies antibiotics most predictive of cluster membership (from Random Forest), revealing biological drivers of cluster separation

#### Statistical Analysis

The Statistical Analysis component quantifies pairwise relationships between antibiotic resistances through co-resistance analysis. This method identifies which antibiotics tend to co-occur in resistant isolates, potentially indicating shared resistance mechanisms, genetic linkage, or common selective pressures.

Figure 6: Statistical Analysis Architecture

### Pairwise Preparation

The analysis begins by systematically examining all possible pairs of antibiotics.

### Key Operations:

- Extract Antibiotic Pairs: Generates all unique combinations of antibiotics from the encoded columns using combinatorial enumeration
- Create Contingency Tables: Constructs 2×2 tables for each antibiotic pair showing co-occurrence of resistance (R) and non-resistance (S/I) states

### Statistical Tests

Rigorous statistical tests assess whether observed co-resistance patterns exceed chance

expectations.

### Key Operations:

- Chi-Square Test: Tests the null hypothesis that resistance to antibiotic A is independent of resistance to antibiotic B; applies Bonferroni correction to adjust significance threshold for multiple comparisons (α / n tests)
- Phi Coefficient: Calculates effect size for 2×2 contingency tables using the formula φ = (ad - bc) / √[(a+b)(c+d)(a+c)(b+d)], where values range from −1 (perfect negative association) to +1 (perfect positive association)

- P-value Matrix: Compiles significance values for all pairwise tests into a symmetric matrix for visualization and filtering

### Association Scoring

Significant associations are ranked and characterized to identify the strongest co-resis-

tance relationships.

### Key Operations:

- Calculate Association Strength: Combines statistical significance (p-value) with effect size (phi coefficient) to rank associations
- Rank Co-resistance Patterns: Orders antibiotic pairs by association strength to prioritize the most important relationships
- Identify Significant Pairs: Filters pairs meeting both significance threshold (Bonferroni-corrected α < 0.05) and minimum effect size (φ ≥ 0.2) criteria

### Output Visual Representation

The Output Visual Representation stage consolidates results from all three pattern discovery methods into an interactive dashboard for clinical and epidemiological interpretation. The system employs Streamlit for web-based visualization, enabling stakeholders to explore resistance patterns through multiple complementary views.

### Key Outputs:

- Cluster Distribution Charts: Bar charts and pie charts showing isolate distribution across resistance phenotype clusters
- Resistance Heatmaps: Color-coded matrices displaying resistance rates by cluster and antibiotic
- Validation Performance Tables: Summary statistics from supervised validation including accuracy, precision, recall, and F1-scores
- Confusion Matrices: Visual representation of cluster prediction performance
- Co-resistance Network Graphs: Network visualization where nodes represent antibiotics and edges indicate significant co-resistance relationships
- Feature Importance Rankings: Bar charts showing which antibiotics most strongly differentiate clusters

---

## Chapter 6: RESULTS AND DISCUSSION

### Introduction

This chapter presents the empirical findings of the antimicrobial resistance pattern recognition analysis conducted on 491 bacterial isolates collected from the water-fishhuman nexus across three Philippine regions: BARMM (Bangsamoro Autonomous Region in Muslim Mindanao), Region III (Central Luzon), and Region VIII (Eastern Visayas).

The results are organized into three complementary analytical approaches:

- Unsupervised Learning Results presents the resistance phenotype clusters identified through hierarchical agglomerative clustering, including Ward’s linkage methodol-

ogy, cluster characteristics, and internal validation metrics (Silhouette score, WCSS)

- Supervised Learning Validation evaluates the predictive validity of the clustering solution using Random Forest classification, demonstrating that cluster assignments

are reproducible from resistance features alone

- Statistical Analysis and Characterization contextualizes the clusters through Principal Component Analysis (PCA), regional and environmental distribution patterns,

and co-resistance network relationships

This progression follows a “Discovery → Validation → Interpretation” framework, wherein clusters are first identified (unsupervised), then validated for robustness (supervised), and finally characterized within their epidemiological context (statistical analysis).

The presentation adheres to a data-driven approach wherein every quantitative claim is substantiated by values extracted directly from the computed artifacts generated by the analysis pipeline [8].

### Unsupervised Learning Results

#### Clustering Parameters

The structure of the resistance dataset was analyzed using hierarchical agglomerative clustering. This approach builds a hierarchy of clusters by progressively merging similar isolates based on their resistance profiles.

### Ward’s Linkage Method

Ward’s minimum variance method was employed as the linkage criterion [12]. Unlike other linkage methods that focus on pairwise distances (e.g., single or complete linkage), Ward’s method minimizes the total within-cluster variance at each merger step. This optimization criterion is particularly effective for discovering compact, spherical clus- ters that correspond to distinct resistance phenotypes.

The Within-Cluster Sum of Squares (WCSS) quantifies the compactness

achieved by Ward’s method:

Table 16: Within-Cluster Sum of Squares (WCSS) by cluster solution. ΔWCSS shows the reduction from the previous k. The elbow point at k=4 marks diminishing returns in variance reduction.

In Table 16, k represents the number of clusters tested, WCSS is the Within-Cluster Sum of Squares measuring total variance within all clusters, ΔWCSS shows the absolute reduction from the previous k value, and % Reduction indicates the relative improvement in cluster compactness. The elbow point occurs where percent reduction begins to plateau.

### Euclidean Distance

Euclidean distance was selected as the dissimilarity metric, measuring the geometric distance between isolate resistance vectors. This metric is the required complement to Ward’s linkage method, as Ward’s objective function is defined based on squared Euclidean distances. The combination of Ward’s linkage and Euclidean distance provides a robust framework for identifying natural groupings in the multidimensional resistance data.

Table 17: Euclidean distance thresholds defining cluster solutions. The optimal k=4 solution is stable within the distance range 22.27 to 23.76.

In Table 17, Cluster Solution (k) indicates the resulting number of clusters, Lower Threshold (d) is the minimum Euclidean distance at which that solution becomes stable, and Upper Threshold (d) is the maximum distance before a merge reduces the cluster count.

#### Optimal Cluster Solution

Hierarchical agglomerative clustering using Ward’s linkage method and Euclidean distance (as described in Section 6.2.1, Clustering Parameters) was applied to 491 bacterial isolates collected from the water-fish-human nexus across three Philippine regions. Cluster (k) solutions from k=2 to k=8 were evaluated for optimal selection, with metrics computed to k=10 for validation purposes [35].

Table 18: Cluster Validation Metrics Across k Values

In Table 18, k is the number of clusters and Silhouette Score measures cluster separation (≥0.40 indicates strong structure). WCSS quantifies compactness (lower is better), while Calinski-Harabasz (higher is better) and Davies-Bouldin (lower is better) provide complementary validity checks.

The k=4 cluster solution was selected as the optimal configuration through a multi-criteria decision framework [17], [36]. The k=4 solution represents the elbow point in the WCSS curve and satisfies the silhouette threshold (≥0.40). Furthermore, the Davies-Bouldin index at k=4 (1.089) confirms reasonable separation without excessive overlap, supported by a competitive Calinski-Harabasz score (192.78), indicating dense and well-separated clusters.

Table 19: Multi-criteria decision matrix for optimal k selection. The k=4 solution satisfies all criteria with a favorable balance of statistical validity and biological interpretability.

The columns in Table 19 evaluate each cluster solution across multiple dimensions. Silhouette scores measure cluster cohesion (where ≥0.40 indicates strong structure), while the Elbow Point identifies the diminishing returns in variance reduction. Interpretability assesses the biological relevance of resulting groups, and Min Cluster Size ensures no cluster falls below n=20, a threshold required for reliable phenotype estimation.

Figure 7: Elbow method (left) and silhouette analysis (right) for cluster validation. The WCSS curve shows the elbow point at k=4, while the silhouette plot confirms moderate-to-strong structure at this configuration.

#### Sensitivity Analysis: Evaluation of k=5 and k=6

Driven by the favorable Calinski-Harabasz and Davies-Bouldin scores observed at higher cluster counts (Table 18), varying cluster solutions were rigorously evaluated to test the stability of the k=4 optimal selection.

Experiment k=5: The 5-cluster solution (Davie-Bouldin = 0.976) was generated and analyzed. While it achieved a lower dispersion index, inspection of the phenotype profiles revealed that the additional cluster resulted from the fragmentation of the Susceptible Cluster (C4) into two biologically indistinguishable subgroups, offering no additional clinical or epidemiological resolution.

Experiment k=6: The 6-cluster solution (Calinski-Harabasz = 214.74) yielded

the highest density score but introduced singleton clusters with n < 10 isolates. This violated the minimum cluster size requirement (ng = 20) established for statistical reliability, rendering the solution less robust for subsequent analysis.

Consequently, k=4 was retained as the most parsimonious solution that balances

statistical performance with biological interpretability.

#### Cluster Characteristics

The four identified clusters exhibited distinct resistance phenotype profiles:

Table 20: Cluster composition summary showing species distribution, MDR prevalence, and dominant resistance patterns

In Table 20, the columns describe each group’s key features. Cluster is the group name, while N Isolates shows the number and percentage of samples it contains. Dominant Species lists the most common bacteria found in that group, and MDR % shows how many are multidrug-resistant. Finally, Top Resistant Antibiotics lists the specific drugs

that the group resists, using these abbreviations: AN=Amikacin, GM=Gentamicin, AM=Ampicillin, CF=Cefalotin, CN=Cefalexin, TE=Tetracycline, DO=Doxycycline, FT=Nitrofurantoin.

### Cluster 1: The Salmonella-Aminoglycoside Phenotype

Cluster 1 comprises the smallest population (n=23, representing 4.7% of the 491 total isolates) and is exclusively composed of Salmonella species, representing a taxonomically homogeneous group. The cluster exhibits low MDR prevalence, with only 1 of 23 isolates (4.3%) classified as MDR, characterized by elevated resistance to aminoglycoside antibiotics (Amikacin, Gentamicin, Tobramycin). Geographically, 17 of 23 C1 isolates (73.9%) originate from Region III – Central Luzon, with 16 of 23 (69.6%) derived from water samples.

### Cluster 2: The Enterobacter-Penicillin Phenotype

Cluster 2 (n=93, representing 18.9% of total isolates) is dominated by Enterobacter cloacae (66 of 93, 71.0%) and Enterobacter aerogenes (20 of 93, 21.5%). The cluster displays low MDR prevalence, with only 2 of 93 isolates (2.2%) classified as MDR, characterized by resistance to Ampicillin, Cephalothin, and Gentamicin. The Ampicillin–Cephalothin co-resistance pattern is consistent with intrinsic chromosomal AmpC β-lactamase expression characteristic of Enterobacter species.

### Cluster 3: The Multi-Drug Resistant Archetype

Cluster 3 (n=123, representing 25.1% of total isolates) constitutes the primary MDR reservoir within the dataset. A striking 66 of 123 isolates (53.7%) are classified as multidrug-resistant [23]—accounting for 94.3% of all 70 MDR isolates in the dataset and representing a rate more than 100-fold higher than Cluster 4 (1 of 252, 0.4%). The cluster is dominated by Escherichia coli (95 of 123, 77.2%) and Klebsiella pneumoniae (27 of 123, 22.0%), both species recognized as priority pathogens in the WHO global AMR threat list. The resistance profile is characterized by high prevalence of Tetracycline (TE), Doxycycline (DO), and Ampicillin (AM) resistance.

The geographic distribution of C3 reveals that 66 of 123 isolates (53.7%) originate from the BARMM region—a coincidentally identical percentage to the MDR rate but representing a different subset of isolates. Additionally, 69 of 123 C3 isolates (56.1%) were derived from fish samples, while 9 of 123 (7.3%) were collected from hospital environments.

### Cluster 4: The Susceptible Majority

Cluster 4 (n=252, representing 51.3% of total isolates) is the largest cluster and the dominant susceptibility phenotype within the dataset. The cluster comprises Escherichia coli (129 of 252, 51.2%) and Klebsiella pneumoniae (119 of 252, 47.2%) in nearly equal proportions, yet exhibits a remarkably low MDR prevalence of only 1 of 252 isolates (0.4%). The near-complete susceptibility profile suggests that C4 isolates have not been subjected to the same selective pressures as C3, despite overlapping species composition.

### Supervised Learning Validation

The supervised validation approach evaluates whether the clusters identified through unsupervised hierarchical clustering represent reproducible, predictable patterns in the resistance data. By training a classifier to predict cluster membership from resistance features alone, we can assess whether the cluster assignments capture genuine structure rather than artifacts of the clustering algorithm.

#### Random Forest Classification

A Random Forest classifier was trained to predict cluster membership using the 22dimensional encoded resistance data as input features [24]. The model was evaluated on a held-out test set (20%) after stratified splitting to ensure robust performance estimates across all four clusters.

Table 21: Random Forest classification performance for cluster prediction (Held-out Test Set)

The exceptionally high classification accuracy (99.0%) demonstrates that cluster assignments are highly predictable from resistance data alone. This confirms that the four clusters represent distinct, reproducible resistance phenotypes rather than arbitrary groupings. The balanced macro F1-score (0.96) indicates excellent performance across all cluster sizes, including the smaller Cluster 1 (n=23).

#### Feature Importance

The Random Forest model also provides interpretable feature importance scores, indicating which antibiotics contribute most to cluster discrimination.

Table 22: Top 5 antibiotics by Random Forest feature importance for cluster discrimination

Tetracycline, cephalothin, and amoxicillin-clavulanic acid emerge as the most discriminating features, with tetracycline (0.241) retaining its strong role in defining the MDR Archetype cluster (C3). The prominence of beta-lactams (cephalothin, AMC) and tetracyclines (TE, DO) confirms that these drug classes are the primary drivers of phenotypic separation.

#### Sensitivity Analysis: Split Ratio and Cross-Validation

To validate the robustness of the chosen experimental configuration (80/20 split, Random Forest), a sensitivity analysis was conducted comparing different partitioning strategies. Three split ratios (70/30, 80/20, 90/10) and two cross-validation schemes (5fold, 10-fold) were evaluated across all three classifier models.

### Split Ratio Comparison

Table 23: F1 Scores Across Different Train–Test Split Ratios (Cluster Discrimination)

### Cross-Validation Comparison

Table 24: F1 Scores Across Different Cross-Validation Configurations

The analysis confirms consistently high performance (>0.96 F1) across all configurations, indicating that cluster separability is robust to sampling variations. The 80/20 split with 5-fold cross-validation was confirmed as an optimal balance between training adequacy and evaluation reliability.

#### Validation Implications

The successful supervised validation provides several key insights:

- Cluster Reproducibility: The 99.0% accuracy confirms that an independent learning algorithm can recover the same groupings with near-perfect precision,

substantially reducing concerns about clustering artifacts.

- Phenotype Distinctiveness: High precision and recall indicate clear boundaries between resistance phenotypes, supporting their use as meaningful epidemiological

categories.

- Feature Interpretability: The alignment between feature importance and known resistance mechanisms—particularly the strong discriminatory power of tetracycline-class antibiotics for MDR phenotypes—validates the biological coherence of the clustering solution.

### Statistical Analysis and Characterization

This section presents complementary statistical analyses that characterize the identified resistance phenotypes within their epidemiological context. These include dimensionality reduction via Principal Component Analysis (PCA), examination of regional and environmental distribution patterns, and co-resistance network relationships.

#### Principal Component Analysis

Principal Component Analysis (PCA) was performed on the 22-dimensional encoded resistance data to visualize the underlying structure and assess its dimensionality.

Table 25 details the contributions of the first five principal components (PC) to the total variance of the isolate profiles. In this table, Component identifies the PC axis, Variance Explained (%) indicates how much of the dataset’s total information is captured by that specific component, and Cumulative (%) shows the total variance accounted for by all components up to that point.

Table 25: Variance explained by the first five principal components of the encoded resistance matrix

The first two principal components capture 39.92% of the total variance, which is characteristic of high-dimensional phenotypic data where resistance patterns are influenced by multiple independent genetic determinants. Five components are required to exceed 68% cumulative variance, indicating substantial dimensionality in the resistance phenotype space. Despite the limited variance captured in two dimensions, the PCA projection reveals visually distinguishable cluster separation, particularly along PC1 which correlates strongly with the tetracycline–doxycycline resistance axis that defines the MDR Cluster 3 [20].

Figure 8: PCA projection of 491 isolates colored by cluster assignment. The scatter plot visualizes the separation of the four distinct resistance phenotypes along the first two principal components (PC1 and PC2).

#### Regional Distribution Patterns

The four resistance clusters exhibited differential distribution across the three participating regions, revealing significant regional heterogeneity.

Table 26: Regional distribution of resistance phenotype clusters (percentage of each cluster by region)

Central Luzon Dominance in C1: Cluster 1 (Salmonella-Aminoglycoside phenotype) shows strong geographic localization to Region III – Central Luzon, with 17 of 23 isolates (73.9%) originating from this region. This concentration suggests localized

Salmonella circulation in Central Luzon water systems or region-specific aminoglyco-

side selection pressure from agricultural antibiotic use.

BARMM Concentration of MDR: The MDR Archetype cluster (C3) shows predominant representation in BARMM, with 66 of 123 isolates (53.7%) originating from this region, making BARMM the primary hotspot for multidrug-resistant E. coli and K. pneumoniae [4]. BARMM also harbors 143 of 252 C4 isolates (56.7%), indicating both the highest MDR burden and largest reservoir of currently-susceptible isolates vulnerable to future resistance acquisition.

#### Environmental Niche Associations

Table 27: Environmental distribution of resistance phenotype clusters

Water-Associated C1: Cluster 1 shows the strongest water association, with 16 of 23 isolates (69.6%) from water samples, no hospital representation, and only 7 of 23 (30.4%) from fish samples—consistent with Salmonella waterborne ecology.

Hospital Penetration in C3/C4: Clusters 3 and 4 are the only clusters with hospital-derived isolates (9 of 123 [7.3%] and 32 of 252 [12.7%] respectively). The higher hospital proportion in the susceptible C4 compared to MDR C3 may reflect that MDR acquisition occurs primarily in environmental reservoirs before clinical introduction.

Fish Dominance: Fish samples predominate in Clusters 2–4 (53.8%–58.7%), underscoring aquaculture systems as key resistance reservoirs consistent with the One Health framework [9].

#### Co-resistance Pattern Analysis

To investigate the complex interactions between resistances, pairwise co-occurrence patterns of resistance profiles were analyzed. This analysis aims to uncover significant associations that may reflect shared genetic mechanisms, co-selection pressures, or cross-resistance phenomena within the isolate population.

### Phi Coefficient Analysis

Co-resistance relationships between antibiotic pairs were quantified using Phi coefficients, with significance determined via chi-square testing [21]. Pairs exhibiting Phi >

0.3 and p < 0.001 were considered statistically significant co-resistance associations. In Table 28, Antibiotic Pair lists the combinations evaluated, Phi Coefficient measures the strength of association (closer to 1.0 indicates stronger co-occurrence), and the p- value denotes statistical significance.

Table 28: Top Significant Co-resistance Pairs

The strongest co-resistance association was observed between doxycycline and tetracycline (Phi = 0.806), reflecting shared resistance mechanisms via ribosomal protection proteins and efflux pumps [39].

### Co-resistance Network

Network analysis revealed hub antibiotics with high connectivity, indicating they frequently co-occur with resistance to multiple other agents. These hub positions suggest potential targets for resistance surveillance prioritization.

Key findings from the network topology:

- Ampicillin exhibited the highest degree centrality, connecting to 8 other resistance phenotypes
- Fluoroquinolone resistance (enrofloxacin, marbofloxacin) formed a tightly connected subnetwork

### Clinical Implications

The identified co-resistance patterns have direct implications for empirical therapy selection. The strong tetracycline-doxycycline linkage suggests that resistance to one tetracycline should prompt consideration of alternative therapies across the class. Similarly, fluoroquinolone co-resistance patterns align with mechanistic understanding of efflux-mediated cross-resistance [40].

### Discussion of Results

#### Interpretation of Clustering Results

The four-cluster solution identified by hierarchical clustering reveals distinct antimicrobial resistance phenotypes within the Philippine isolate collection. The emergence of a high-MDR cluster (C3) dominated by E. coli and K. pneumoniae aligns with global reports of problematic Enterobacteriaceae strains exhibiting extensive drug resistance [41].

The clustering approach employed in this study offers advantages over singlegene molecular characterization by capturing the complete phenotypic resistance profile. This holistic view enables identification of clinically relevant resistance patterns that may arise from multiple underlying mechanisms [42].

#### Methodological Validation

The supervised validation approach using Random Forest classification addresses a key limitation of unsupervised learning: the lack of ground truth labels. By demonstrating that cluster assignments are reproducible via an independent learning algorithm, this

study provides evidence that the identified patterns represent genuine biological group-

ings rather than algorithmic artifacts [24].

The high macro F1-Score (0.96) indicates excellent discriminative ability, suggesting that resistance profiles within each cluster share common characteristics distinguishable from other clusters. This finding supports the utility of phenotypic clustering for AMR surveillance stratification.

#### Comparison with Parent Project Data

This study builds upon the extensive surveillance data collected by the parent project (INOHAC Project 2), shifting the analytical focus from descriptive statistics to multivariate pattern recognition. Table 29 details the similarities and key methodological advancements distinguishing this thesis from the primary surveillance reports.

Table 29: Comparative analysis between Parent Project surveillance data and Thesis Clustering results

The integration of data from the parent project [8] provides the necessary volume to detect these patterns, while the clustering approach elucidates the underlying structure of resistance that descriptive counts alone cannot reveal. Specifically, the “MDR Archetype” (Cluster 3) unifies the high MDR counts observed in BARMM E. coli and K. pneumoniae into a single, trackable phenotypic entity.

#### Limitations

Several limitations warrant consideration:

- Retrospective design: Analysis was conducted on historical AST data, limiting the ability to capture temporal trends
- Phenotypic focus: Genotypic resistance mechanisms were not characterized, precluding direct linkage of clusters to specific resistance genes
- Regional scope: Results may not generalize to other Philippine regions or international contexts
- Missing data: Some isolates lacked complete antibiotic panels, potentially affecting

cluster assignments

Despite these limitations, the study demonstrates the feasibility and utility of machine learning approaches for AMR pattern recognition in resource-limited surveillance settings.

### Chapter Summary

This chapter presented the results of the pattern recognition analysis on antimicrobial susceptibility data from 491 bacterial isolates across three Philippine regions. Key findings include:

- Optimal Clustering: Hierarchical clustering with Ward’s linkage identified k=4 as the optimal cluster solution, with silhouette score of 0.466 and biologically inter-

pretable cluster profiles

- Cluster Characterization: Four distinct resistance phenotypes were identified:
- C1 (n=23): Salmonella-aminoglycoside phenotype (4.3% MDR)
- C2 (n=93): Enterobacter-penicillin phenotype (2.2% MDR)
- C3 (n=123): Multi-drug resistant archetype (53.7% MDR) - primary public health concern
- C4 (n=252): Susceptible majority (0.4% MDR)
- MDR Concentration: Cluster 3 contains > 50-fold higher MDR prevalence than

Cluster 4, despite overlapping species composition

- Dimensionality Reduction: PCA captured 68.26% variance in 5 components, with

PC1 correlating strongly with tetracycline resistance

- Co-resistance Patterns: Strong associations identified between tetracyclines

(Phi=0.81) and within antibiotic classes

- Regional Patterns: BARMM exhibited highest concentration of MDR Cluster 3

isolates (66 of 123, 53.7%), warranting targeted surveillance

- Validation: Random Forest classification achieved 99.0% test set accuracy (macro

F1 = 0.96), confirming cluster stability and reproducibility

These findings support the utility of hybrid unsupervised-supervised machine learning frameworks for AMR surveillance and phenotype stratification in the Philippine waterfish-human nexus context [9].

---

## Chapter 7: CONCLUSION AND RECOMMENDATION

### Conclusion

This study developed and validated a hybrid unsupervised-supervised machine learning framework for pattern recognition of antimicrobial resistance phenotypes in bacterial isolates from the Philippine water-fish-human nexus. The analysis of 491 isolates collected through the INOHAC AMR Project Two across three regions—BARMM, Central Luzon, and Eastern Visayas—yielded the following conclusions:

#### Objective 1: Resistance Phenotype Identification

Hierarchical agglomerative clustering using Ward’s linkage method and Euclidean distance successfully identified four distinct resistance phenotype clusters:

- Cluster 1 (n=23, 4.7% of 491 isolates): A taxonomically homogeneous Salmonellaaminoglycoside phenotype with low MDR prevalence (1 of 23 isolates, 4.3%), geographically concentrated in Central Luzon (17 of 23, 73.9%) and predominantly

water-associated (16 of 23, 69.6%).

- Cluster 2 (n=93, 18.9% of total): An Enterobacter-penicillin phenotype exhibiting intrinsic AmpC β-lactamase-mediated resistance with minimal MDR (2 of 93 iso-

lates, 2.2%).

- Cluster 3 (n=123, 25.1% of total): The multi-drug resistant archetype dominated by E. coli (95 of 123, 77.2%) and K. pneumoniae (27 of 123, 22.0%), with striking

MDR prevalence (66 of 123 isolates, 53.7%)—accounting for 94.3% of all 70 MDR isolates in the dataset.

- Cluster 4 (n=252, 51.3% of total): The susceptible majority representing the largest cluster with near-complete antibiotic susceptibility (only 1 of 252 isolates, 0.4% MDR) despite similar species composition to Cluster 3.

#### Objective 2: Cluster Validation

The four-cluster solution achieved a silhouette score of 0.466, indicating moderate cluster structure appropriate for complex biological phenotypes. Supervised validation using Random Forest classification achieved 99.0% test set accuracy (macro F1 = 0.96), confirming that cluster assignments represent reproducible, learnable patterns rather than algorithmic artifacts [24].

#### Objective 3: Spatial and Environmental Patterns

Significant geographic heterogeneity was observed, with BARMM exhibiting the highest concentration of MDR Cluster 3 isolates (66 of 123, 53.7%), identifying this region as the primary AMR hotspot requiring targeted surveillance intervention [4]. Environmental analysis revealed distinct niche associations: Salmonella with water sources, and MDR Enterobacteriaceae with fish samples, supporting the One Health framework for integrated AMR surveillance [9].

#### Objective 4: Co-resistance Networks

Strong co-resistance associations were identified, particularly between tetracyclines (Phi=0.81), reflecting shared resistance mechanisms via ribosomal protection proteins and efflux pumps [39]. These patterns have direct implications for empirical therapy selection and resistance prediction.

#### Overall Contribution

This study demonstrates that machine learning approaches can effectively stratify AMR phenotypes in resource-limited surveillance settings, providing actionable intelligence for public health intervention. The reproducible computational pipeline enables ongoing resistance monitoring and phenotype tracking as new data become available.

### Recommendations

Based on the findings of this study, the following recommendations are proposed for AMR surveillance, public health practice, and future research:

#### For Public Health Authorities

- Prioritization of BARMM for AMR Intervention: Given that 66 of 123 MDR Cluster 3 isolates (53.7%) originate from BARMM, targeted antimicrobial stewardship programs and enhanced laboratory capacity warrant prioritization in this region.
- Integrate Environmental Surveillance: The identification of distinct resistance phenotypes in water (C1) and fish (C2–C4) sources supports the implementation of One Health surveillance frameworks that monitor AMR across human, animal, and

environmental sectors [9].

- Monitor Co-resistance Patterns: The strong tetracycline-doxycycline co-resistance (Phi=0.81) suggests that empirical therapy guidelines should consider cross-resistance when selecting treatment regimens, particularly in regions with high tetracycline use in aquaculture.

#### For Healthcare Practitioners

- Species-Specific Empiric Therapy: The clustering results indicate that Salmonella

isolates (C1) exhibit distinct aminoglycoside resistance patterns compared to E. coli/

K. pneumoniae (C3/C4), supporting species-guided empiric antibiotic selection.

- MDR Risk Stratification: Isolates from fish-derived sources in BARMM should be considered higher risk for MDR, warranting more aggressive susceptibility testing before treatment initiation.

#### For Surveillance Programs

- Adoption of Phenotypic Clustering: The validated clustering methodology provides a reproducible approach for stratifying resistance phenotypes that could be integrated into routine national AMR surveillance programs [5].
- Leverage Machine Learning: The demonstrated 99.0% validation accuracy supports the deployment of supervised classifiers for automated resistance phenotype

prediction in clinical microbiology laboratories.

- Standardize Data Collection: Consistent AST panel coverage across regions would enhance clustering precision and enable more robust temporal trend analysis.

#### For Aquaculture Management

- Reduction of Antibiotic Use: The concentration of MDR isolates in fish samples (69 of 123 C3 isolates, 56.1%) indicates aquaculture environments as significant resistance reservoirs, supporting policies to reduce prophylactic antibiotic use in aquaculture operations [43].
- Water Quality Monitoring: The water-associated Salmonella cluster (C1) suggests that water quality improvements could reduce environmental resistance transmission.

### Future Research Directions

While this study provides a foundation for machine learning-based AMR surveillance, several avenues for future research are recommended:

#### Methodological Extensions

- Genotypic Integration: Complement phenotypic clustering with whole-genome sequencing data to link resistance clusters to specific resistance genes and mobile genetic elements, enabling mechanistic interpretation of phenotype patterns.
- Temporal Analysis: Extend the retrospective analysis to include longitudinal data,

enabling detection of emerging resistance trends and cluster evolution over time.

- Deep Learning Approaches: Explore neural network architectures for resistance pattern recognition, potentially capturing non-linear relationships not detected by hierarchical clustering.

#### Geographic Expansion

- National Coverage: Expand the analysis to include additional Philippine regions beyond BARMM, Central Luzon, and Eastern Visayas to establish a comprehensive national resistance phenotype atlas.
- Southeast Asian Comparison: Compare Philippine resistance clusters with patterns observed in neighboring countries to assess regional transmission dynamics [26].

#### Clinical Translation

- Prospective Validation: Validate the clustering methodology prospectively using newly collected isolates to confirm generalizability beyond the training dataset.
- Clinical Outcome Linkage: Correlate resistance cluster membership with patient clinical outcomes to assess whether phenotype stratification predicts treatment

response.

- Real-time Dashboard: Deploy the Streamlit dashboard as a web-accessible tool for real-time AMR surveillance visualization by regional health authorities.

#### One Health Applications

- Animal Health Integration: Incorporate veterinary isolates beyond fish samples to capture the full spectrum of animal-derived resistance in the One Health framework.
- Environmental Sampling: Expand environmental surveillance to include sediment,

wastewater, and agricultural samples to comprehensively map resistance reservoirs. These extensions would strengthen the evidence base for machine learning-assisted

AMR surveillance and accelerate translation of computational insights into public health action.

### REFERENCES

- J. Cohen, Statistical Power Analysis for the Behavioral Sciences, 2nd ed. Lawrence Erlbaum Associates, 1988.
- World Health Organization, Global Antibiotic Resistance Surveillance Report 2025. World Health Organization, 2025. [Online]. Available: https://www.who.

int/publications/i/item/9789240116337

- The Review on Antimicrobial Resistance, “Tackling Drug-Resistant Infections Globally: Final Report and Recommendations.” [Online]. Available: https://amr-

review.org/sites/default/files/160525_Final%20paper_with%20cover.pdf

- C. Ng, J. Abrazaldo, P. d. Vera, S. G. Goh, and B. Tan, “Antibiotic Resistance in the Philippines: Environmental Reservoirs, Spillovers, and One-Health Research Gaps,” Frontiers in Microbiology, vol. 16, 2025, doi: 10.3389/

fmicb.2025.1711400.

- Antimicrobial Resistance Surveillance Program, “ARSP 2024 Annual Report: National Antimicrobial Resistance Surveillance in the Philippines,” Research

Institute for Tropical Medicine, 2024, [Online]. Available: https://arsp.com.ph/

- A. Sakagianni et al., “Data-Driven Approaches in Antimicrobial Resistance: Machine Learning Solutions,” Antibiotics, vol. 13, no. 11, p. 1052, 2024, doi:

10.3390/antibiotics13111052.

- K. T. S. Parthasarathi et al., “A machine learning-based strategy to elucidate the identification of antibiotic resistance in bacteria,” Frontiers in Antibiotics, vol. 3,

p. 1405296, 2024, doi: 10.3389/frabi.2024.1405296.

- F. M. Abamo et al., “INOHAC AMR Project Two: Antimicrobial Resistance in Water-Fish-Human Nexus — Mapping of Antibiotic-Resistant Escherichia coli, Salmonella spp., Shigella spp. and Vibrio cholerae,” Research Report, 2024.
- A. M. Franklin et al., “A one health approach for monitoring antimicrobial resistance: developing a national freshwater pilot effort,” Frontiers in Water, vol. 6,

2024, doi: 10.3389/frwa.2024.1359109.

- M. Reverter et al., “Aquaculture at the Crossroads of Global Warming and Antimicrobial Resistance,” Nature Communications, vol. 11, no. 1, p. 1870, 2020,

doi: 10.1038/s41467-020-15735-6.

- T. Hastie, R. Tibshirani, and J. Friedman, “The Elements of Statistical Learning: Data Mining, Inference, and Prediction.” [Online]. Available: https://esl.

hohoweiya.xyz/book/The%20Elements%20of%20Statistical%20Learning.pdf

- J. H. Ward, “Hierarchical Grouping to Optimize an Objective Function,” Journal of the American Statistical Association, vol. 58, no. 301, pp. 236–244, 1963, doi:

10.2307/2282967.

- E. Abada, A. Mashraqi, Y. Modafer, and S. O. Alshammari, “Clustering analysis of antibiotic resistance in multidrug-resistant bacteria from spoiled vegetables,” Microbial Pathogenesis, vol. 206, p. 107819, 2025, doi: 10.1016/

j.micpath.2025.107819.

- I. T. Jolliffe and J. Cadima, “Principal Component Analysis: A Review and Recent Developments,” Philosophical Transactions of the Royal Society A: Mathematical, Physical and Engineering Sciences, vol. 374, no. 2065, p. 20150202, 2016,

doi: 10.1098/rsta.2015.0202.

- P. J. Rousseeuw, “Silhouettes: A Graphical Aid to the Interpretation and Validation of Cluster Analysis,” Journal of Computational and Applied Mathematics, vol.

20, pp. 53–65, 1987, doi: 10.1016/0377-0427(87)90125-7.

- K. R. Shahapure and C. Nicholas, “Cluster Quality Analysis Using Silhouette Score,” 2020 IEEE 7th International Conference on Data Science and Advanced

Analytics (DSAA), 2020, doi: 10.1109/dsaa49011.2020.00096.

- H. Jeon, M. Aupetit, D. Shin, A. Cho, S. Park, and J. Seo, “Measuring the Validity of Clustering Validation Datasets,” IEEE Transactions on Pattern

Analysis and Machine Intelligence, vol. 47, pp. 5045–5058, 2025, doi: 10.1109/

tpami.2025.3548011.

- L. Breiman, “Random Forests,” Machine Learning, vol. 45, no. 1, pp. 5–32, 2001.
- R. Kou et al., “Spatial panel data analysis of antimicrobial resistance in Escherichia coli in China,” Scientific Reports, vol. 15, 2025, doi: 10.1038/

s41598-025-09085-w.

- P. K. Selvam, S. M. Elavarasu, H. Dey, K. Vasudevan, and G. P. Doss, “Decoding the Complex Genetic Network of Antimicrobial Resistance in Campylobacter jejuni Using Advanced Gene Network Analysis,” Gene Expression, vol. 23, pp.

106–115, 2024, doi: 10.14218/ge.2023.00107.

- H.-M. Martiny, P. Munk, C. Brinch, F. M. Aarestrup, M. L. Calle, and T. N. Petersen, “Utilizing co-abundances of antimicrobial resistance genes to identify potential co-selection in the resistome,” Microbiology Spectrum, vol. 12, p.

e410823, 2024, doi: 10.1128/spectrum.04108-23.

- P. Krumperman, “Multiple antibiotic resistance indexing of Escherichia coli to identify high-risk sources of fecal contamination of foods,” Applied and Environmental Microbiology, vol. 46, no. 1, pp. 165–170, 1983, doi: 10.1128/

aem.46.1.165-170.1983.

- A.-P. Magiorakos et al., “Multidrug-resistant, extensively drug-resistant and pandrug-resistant bacteria: an international expert proposal for interim standard definitions for acquired resistance,” Clinical Microbiology and Infection, vol. 18,

pp. 268–281, 2011, doi: 10.1111/j.1469-0691.2011.03570.x.

- C. M. Ardila, D. González-Arroyave, and S. Tobón, “Machine learning for predicting antimicrobial resistance in critical and high-priority pathogens: A systematic review considering antimicrobial susceptibility tests in real-world healthcare settings,” PLoS ONE, vol. 20, p. e319460, 2025, doi: 10.1371/journal.pone.0319460.
- S. Widodo, H. Brawijaya, and S. Samudi, “Stratified K-fold cross validation optimization on machine learning for prediction,” Sinkron, vol. 7, pp. 2407–2414,

2022, doi: 10.33395/sinkron.v7i4.11792.

- Y. Xie et al., “One health perspective of antibiotic resistance in Enterobacterales from Southeast Asia: a systematic review and meta-analysis,” Scientific Reports,

2025, doi: 10.1038/s41598-025-31195-8.

- A. J. Palmares et al., “Antibiotic resistance profile of Escherichia coli from Marikina River in the Philippines: Environmental and public health implications,” Journal of Applied and Natural Science, vol. 17, pp. 614–621, 2025, doi:

10.31018/jans.v17i2.6552.

- N. Luchian et al., “Episodeand Hospital-Level Modeling of Pan-Resistant Healthcare-Associated Infections (2020–2024) Using TabTransformer and Attention-Based LSTM Forecasting,” Diagnostics, vol. 15, p. 2138, 2025, doi: 10.3390/

diagnostics15172138.

- R. O. Duda, P. E. Hart, and D. G. Stork, Pattern Classification, 2nd ed. John Wiley

& Sons, 2001.

- A. K. Jain and R. C. Dubes, Algorithms for Clustering Data. Prentice-Hall, 1988.
- T. Hastie, R. Tibshirani, and J. Friedman, The Elements of Statistical Learning:

Data Mining, Inference, and Prediction, 2nd ed. Springer, 2009.

- S. Kaufman, S. Rosset, C. Perlich, and O. Stitelman, “Leakage in Data Mining: Formulation, Detection, and Avoidance,” ACM Transactions on Knowledge Dis-

covery from Data, vol. 6, no. 4, pp. 1–21, 2012, doi: 10.1145/2382577.2382579.

- S. S. Stevens, “On the theory of scales of measurement,” Science, vol. 103, no.

2684, pp. 677–680, 1946.

- J. Podani, “Extending Gower's general coefficient of similarity to ordinal charac-

ters,” Taxon, vol. 48, no. 2, pp. 331–340, 1999.

- A. M. Ikotun, A. E. Ezugwu, L. Abualigah, B. Abuhaija, and J. Heming, “K-means clustering algorithms: A comprehensive review, variants analysis, and advances

in the era of big data,” Information Sciences, vol. 622, pp. 178–210, 2022, doi:

10.1016/j.ins.2022.11.139.

- L. S. Ling and C. T. Weiling, “Enhancing Segmentation: A Comparative Study of Clustering Methods,” IEEE Access, vol. 13, pp. 47418–47439, 2025, doi: 10.1109/

access.2025.3550339.

- S. Dolnicar, “A Review of Unquestioned Standards in Using Cluster Analysis for Data-Driven Market Segmentation.” [Online]. Available: https://www.researchgate.net/publication/30385490_ A_Review_of_Unquestioned_Standards_in_Using_Cluster_Analysis_for_Data-

Driven_Market_Segmentation

- W. Qiu and H. Joe, “Generation of Random Clusters with Specified Degree of Separation,” Journal of Classification, vol. 23, pp. 315–334, 2006, doi: 10.1007/

s00357-006-0018-y.

- Q. Wang et al., “Widespread Dissemination of Plasmid-Mediated Tigecycline Resistance Gene tet(X4) in Enterobacterales of Porcine Origin,” Microbiology

Spectrum, vol. 10, p. e161522, 2022, doi: 10.1128/spectrum.01615-22.

- A. Shariati et al., “The resistance mechanisms of bacteria against ciprofloxacin and new approaches for enhancing the efficacy of this antibiotic,” Frontiers in

Public Health, vol. 10, 2022, doi: 10.3389/fpubh.2022.1025633.

- W. Zhao, P. Sun, W. Li, and L. Shang, “Machine Learning-Based Prediction Model for Multidrug-Resistant Organisms Infections: Performance Evaluation and Interpretability Analysis,” Infection and Drug Resistance, vol. 18, pp. 2255–

2269, 2025, doi: 10.2147/idr.s459830.

- H. K. Tolan et al., “Machine Learning Model for Predicting Multidrug Resistance in Clinical Escherichia coli Isolates: A Retrospective General Surgery Study,”

Antibiotics, vol. 14, no. 10, p. 969, 2025, doi: 10.3390/antibiotics14100969.

- F. Yusuf, S. M. Ahmed, D. Dy, K. Baney, H. Waseem, and K. A. Gilbride, “Occurrence and characterization of plasmid-encoded qnr genes in quinolone-

resistant bacteria across diverse aquatic environments in southern Ontario,” Canadian Journal of Microbiology, vol. 70, pp. 492–506, 2024, doi: 10.1139/ cjm-2024-0029.
