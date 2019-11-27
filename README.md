# Introduction
General introduction of WQ issues. <br>
As the leading state of corn, soybean, and hog production in the United States, Iowa also faces many water quality issues resulted from the intensive agricultural activities. Locally, nitrogen (N) loading into drinking water sources may result in higher water treatment costs, while phosphorus (P) loading may lead to eutrophication of freshwater systems. At a larger scale, Iowa is estimated to account for 29% of the nitrate loading into the Mississippi-Atchafalaya River Basin, which contributes to the formation of hypoxic zone in the Gulf of Mexico. 

<kbd>
<img src="https://github.com/jiyeow/jy_project/blob/master/BHL_aerial_view.jpg" height="400"> <br>
Fig 1: Aerial image of Black Hawk Lake (obtained from blackhawklake.org)
</kbd> <br>

Iowa Nutrient Reduction Strategy document has highlighted that a single best management practice (BMP) may not be sufficient to achieve the N and P 45% load reduction goal. Instead, several BMPs are needed to be combined in a single agricultural field or catchment. This project was designed to compare the stacked benefits of BMPs at two adjacent agricultural catchments located in Black Hawk Lake watershed, Iowa.


#### Problem Statement
Our project requires that we provide a semi-annual updates of our monitoring results. Traditionally, new monitoring data was added into the existing dataset (or modification to existing dataset) and the same analyses were performed manually every six months. This repetitve process consumed a huge amount of time, which then led to the the motivation to automate the process. The goal of this project was to develop a consistent workflow (i.e. reproducibility) to analyze the nutrient and sediment data and the associated parameters (i.e. flow, weather). <br>

The following program will allow any users with minimal python knowledge to analyze the datasets using a consistent method, in addition to saving time from analyzing each dataset manually every time a modification is made to the dataset. <br>

The questions to be answered using this program were: <br>
a) Is analyte concentration higher in one catchment than the other? <br>
b) Is analyte load higher in one catchment than the other? <br> 
c) How does environmental factor (flow, precipitation, and temperature) affect analyte concentration and load? <br>

Additional data can be imported and additional analyses may be added in future development, as needed.

## Method and Approach
#### Monitoring sites and sample collection
Two adjacent catchments, namely catchment 11 and 12, were monitored between 2015 and 2018. Catchment 11 has lower areal extend of BMPs implementation than catchment 12. ISCO automated water samplers were installed to collect continuous flow measurement data and to collected flow-weighted samples at each catchment outlet. Catchment 11 only has one surface outlet, and the monitoring station was named as Surface 11 (S11). Catchment 12 has one surface outlet and one tile outlet, and were named as Surface 12 (S12) and Tile 12 (T12), respectively. The combined load from S12 and T12 represented the total loading from cgitatchment 12. <br>

<kbd>
<img src="https://github.com/jiyeow/jy_project/blob/master/BHL_watershed_map.png" height="400"> <br>
Fig 2: Black Hawk Lake watershed. The lake is located on the north end of the watershed; the monitored catchments (cathcment 11 and 12) are highlighted in green. Side note: "catchment" is labelled as "sub" in this image.
</kbd> 

#### Sample and data analysis  
The water samples were categorized into base flow samples and event (storm) flow samples. They were analyzed for NH3 (ammonia), NOx (nitrate+nitrite), TN (total nitrogen), DRP (dissolved reactive phosphorus), TP (total phosphorus), TSS (total suspended solid), and VSS (volatile suspended solid) concentrations. Nutrient and sediment concentrations between two catchments were tested for significant differences. Normally distributed dataset was tested using t-test; non-normal dataset was tested using Wilcoxon Rank Sum test. In addition, correlations between nutrient/sediment concentration was tested for correlation with auxiliary parameter (flow, precip, temp). Normally distributed dataset was tested using pearsonr correlation; non-normal dataset was tested using spearmanr correlation test. Nutrient and sediment load at each catchment outlet was calculated by multiplying nutrient concentration and flow. Nutrient and sediment load between two catchments were also compared. <br>

#### Project workflow
This project workflow describes the analysis process used in the [Python Notebook](https://github.com/jiyeow/jy_project/blob/master/ABE516x_finalproject.ipynb)
<kbd>
<img src="https://github.com/jiyeow/jy_project/blob/master/ABE516x_project_workflow.png" height="500"> <br>
Fig 3: Project workflow
</kbd>



## Results and Discussions
#### Comparison of nutrient and sediment export between catchments
Insert t-test/Wilcoxon test results here (consider using a table). <br>
Insert load comparison here (consider using a figure). <br>

#### Drivers for nutrient and sediment export
Insert PCA analysis here (consider using a figure). <br>


## Supplemental information
Put the code here (or link to Jupyter notebook). 

