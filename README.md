### Gene essentiality and synthetic lethality using flux balance analysis (FBA)

## Introduction
In this analysis, we investigated the metabolic network of Escherichia coli using the COBRApy framework, focusing on essential genes and synthetic lethality. The primary aim is to understand how gene knockouts affect biomass production, a proxy for growth and survival.

## Methodology
We utilized the* E. coli* core metabolic model (e_coli_core), containing 72 metabolites, 95 reactions, and 137 genes. Biomass production (BIOMASS_Ecoli_core_w_GAM) was set as the objective function.

Using the single_gene_deletion() function, we knocked genes out individually, and biomass production was measured. Genes whose deletion resulted in zero biomass were identified as essential genes. Non-essential genes were paired and tested for synthetic lethality using the double_gene_deletion() function. Then we classified gene pairs leading to zero biomass as synthetic lethal pairs.

## Results
# Single-Gene Knockouts
Single-gene knockouts resulted in the identification of the b1136 and b0720 genes (icd and gltA) which encode the enzyme isocitrate dehydrogenase (icd) (NADP-dependent) and Citrate Synthase (CS) respectfully. Isocitrate dehydrogenase enzyme catalyzes the ICDHyr reaction in the tricarboxylic acid (TCA) cycle. This enzyme facilitates the following reaction;

icit_c + nadp_c <=> akg_c + co2_c + nadph_c

Isocitrate + Nicotinamide adenine dinucleotide phosphate <=> 2-Oxoglutarate + CO2 CO2 + Nicotinamide adenine dinucleotide phosphate - reduced

The b1136 gene is vital for maintaining energy production, NADPH supply, and precursor availability in E. coli. Its loss halts ATP generation and biosynthesis, causing metabolic failure and ultimately preventing biomass production. This highlights the centrality of ICDHyr in the metabolic network and its critical role in sustaining growth and survival.

While the b0720 gene that encode of the Citrate Synthase enzyme plays a central role in the citric acid production, which is crucial for energy produciton and biosynthesis in E.coli. When it is knocked out, the citric acid cycle is disrupted, leading to reduced ATP production, altered metabolism, and compromised biomass synthesis. As a result, E. coli biomass is significantly affected, leading to slower growth, reduced cell division, and a decrease in overall biomass accumulation.

# Double-Gene Knockouts
We identified 92 synthetic lethal pairs in the double-gene knockout analysis, where the simultaneous deletion of two non-essential genes resulted in zero biomass production. These pairs reveal critical redundancies and dependencies in E. coli's metabolic network.

Our key findings include, but not limited to: Notable synthetic lethal pairs include b1849 (purT), which encodes formate-dependent glycinamide ribonucleotide (GAR) transformylase involved in purine biosynthesis (de novo), and b2926 (pgk), which encodes phosphoglycerate kinase, a key enzyme in glycolysis critical for energy production. The simultaneous knockout of these genes disrupts both nucleotide synthesis and energy metabolism, leading to complete growth failure. Also, the interaction between b2926 (pgk), encoding phosphoglycerate kinase in glycolysis, and b1276 (acnA), encoding aconitase A in the TCA cycle, highlights the critical balance between central metabolic pathways. Disruptions at these key nodes compromise energy production and metabolic flux, ultimately resulting in growth failure.

Many synthetic lethal pairs involve genes in interconnected pathways, such as gapA (Glyceraldehyde-3-phosphate dehydrogenase A) and eno (Enolase) genes which are involved in Glycolysis, are critical for energy generation. In addtiion, sdhC (Succinate dehydrogenase cytochrome) is involved in TCA cycle and play essential role in the oxidative metabolism of intermediates. These results underscore the interdependence of core metabolic processes.

## Discussion and Conclusion
This study highlights critical vulnerabilities in E. coli's metabolic network through the identification of essential genes and synthetic lethal pairs. The single-gene knockout analysis revealed b1136 (icd) as an essential gene encoding isocitrate dehydrogenase (NADP-dependent), a key enzyme in the TCA cycle. Its role in producing NADPH and 2-oxoglutarate, essential for biosynthesis and energy metabolism, underscores the TCA cycle’s centrality to cellular viability. The loss of b1136 disrupts ATP generation, precursor availability, and redox balance, making it a critical target for understanding and manipulating metabolic processes. The second gene revealed is b0720 (gltA) another key enzyme which plays a critical role in the citric acid production, which is in turn crucial for energy produciton and biosynthesis in E.coli. Its loss leads to reduced ATP production, altered metabolism, and compromised biomass synthesis.

The double-gene knockout analysis identified 92 synthetic lethal pairs, emphasizing the metabolic network's redundancy and co-dependencies. Key interactions, such as between b2926 (pgk) and b1276 (acnA), demonstrate how fermentation and the TCA cycle collectively sustain energy production and growth.

These findings have significant applications in metabolic engineering, where synthetic lethality can guide strain design for optimized production or biocontainment. Also, in drug discovery, targeting one gene in a synthetic lethal pair offers a promising strategy for designing combination therapies that exploit bacterial vulnerabilities, paving the way for innovative antimicrobial treatments.