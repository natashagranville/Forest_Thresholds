# Forest_Thresholds
Code used for analysis in Global Variation in Forest Thresholds for Biodiversity

Code written by Ben Howes and Natasha Granville

**01_PrepData**

01_01_getPREDICTSdata.R - filters, cleans and formats the 2016 release of the PREDICTS database to obtain studies on arthropods, birds, herptiles and mammals in forest ecoregions. 

01_02_getPREDICTSaddedData.R - filters, cleans and formats the 2022 release of the PREDICTS database to obtain studies on arthropods, birds, herptiles and mammals in forest ecoregions. 

01_03_createStudyGeometries.R - creates shapefiles for each study including the site locations (georeferenced point locations), and the buffered bounding box around each study.

01_04_makeTaxaTable.R - creates a table to record the taxonomic group and biogeographic realm of each study.

01_05_calculateDistance.R - calculates the geographic distance between sites in each study

01_06_getHansenMaps.R - creates a map of treecover within the buffered bounding box around each study.

01_07_calculateLandscapeForestCover.R - calculates the forest cover percentage within landscape-scale buffers (200, 500, 1000, 2000 m) around each site.

01_08_calculateRegionalForestCover.R - calculates the total forest cover proportion within the 1-degree-buffered bounding box around each study

01_09_combineSpeciesLandscapeData.R - combines the site-species matrix with the landscape-scale forest cover data for each study.

01_10_getDataQuality.R - identifies highly forested reference sites within each study, and removes studies with < 30% range of landscape-scale forest cover.

01_11_calculateSimilarity.R - calculates similarity in species composition between sites within each study, using Sorenson and Jaccard indices.

01_12_prepModelData.R - combines all data that will go into the piecewise models. This includes the compositional similarity and geographic distance between highly forested and deforested sites, as well as the landscape-scale forest cover data. Arcsin square root transform the compositional similarity. 


**02_SegmentedModels**

02_01_chooseScaleOfEffect.R - runs segmented models at each landscape scale and identify the scale that gives the highest R2 for each study.

02_02_runSegmentedModels.R - runs linear and segmented models at the optimal scale in each study.

02_03_compareMods.R - identifies conservation-relevant thresholds that meet three criteria: (1) segmented model has lower AIC than linear model. (2) 95% confidence intervals of both slopes in the segmented model do not overlap each other. (3) decrease in compositional intactness at forest cover percentages below the threshold.

02_04_prepAnalysisData.R - formats data for analysis, including whether the study showed a conservation-relevant threshold, the forest cover proportions at which these thresholds were identified, and all explanatory variables for models exploring potential factors affecting threshold presence and position.


**03_StatisticalAnalysis**

03_01_Analyse_Threshold_Presence.R - runs binomial GLMs testing factors affecting the probability of detecting a threshold.

03_02_Analyse_Threshold_Position.R - runs beta GLMs testing factors affecting the forest cover percentage at which the threshold was identified.


**04_Figures**

04_01_Figure1_ThresholdPresence.R - plots figure 1.

04_02_Figure2_ThresholdPosition.R - plots figure 2.

04_03_MapByTaxa.R - plots map of study locations, with the colour and shape of the points showing the taxonomic group.

04_04_Realm_ThresholdPresence - plots figure showing the proportion of studies within each biogeographic realm that showed a threshold.

04_05_ThresholdPresence_ForestRange_Lat.R - plots graphs showing the probability of detecting a threshold as a function of the range of forest cover within each study, and the average absolute latitude of the study.

04_06_Lat_ThresholdPosition_Graph.R - plots graph showing the threshold position as a function of the absolute average latitude of the study in which the threshold was detected.

04_07_Scale_Diagram.R - plots figure illustrating the definitions of different scales used in the manuscript (regional scale, landscape scale and local scale).


**05_Supplementary**

05_01_SpeciesRichness - R scripts within this folder re-run all analyses using species richness as the response variable for the segmented models.

05_02_CommunityComposition - R scripts within this folder re-run all analyses using community composition (first axis of PCoA performed on community similarity matrix) as the response variable for the segmented models.

05_03_Jaccard - R scripts within this folder re-run all analyses with the response variable (compositional similarity between highly forested and deforested sites) that was calculated using the Jaccard index. 
