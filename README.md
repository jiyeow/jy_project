# Table of Content
<!--ts-->
* [Introduction](#introduction) <br>
  * [Problem statement](#problem-statement) <br>
* [Method and Approach](#method-and-approach) <br>
  * [Monitoring sites and sample collection](#monitoring-sites-and-sample-collection) <br>
  * [Sample and data analysis](#sample-and-data-analysis) <br>
  * [Project workflow and reproducibility](#project-workflow-and-reproducibility) <br>
  * [Integration of class concepts and techniques](#integration-of-class-concepts-and-techniques) <br>
* [Results and Discussion](#results-and-discussion) <br>
  * [Comparison of nutrient and sediment concentrations](#comparison-of-nutrient-and-sediment-concentrations) <br>
  * [Comparison of nutrient and sediment loads](#comparison-of-nutrient-and-sediment-loads) <br>
  * [Correlation between nutrient/sediment and environmental parameters](#correlation-between-nutrientsediment-and-environmental-parameters) <br>
* [Summary of Data Analysis](#summary-of-data-analysis) <br>
* [Supplemental Information](#supplemental-information) <br>
<!--te-->

# Introduction
As the leading state for corn, soybean, and hog production in the United States, Iowa also faces many water quality issues resulted from the intensive agricultural activities, such as application of nitrogen and phosphorus fertilizers. Locally, nitrogen (N) loading into drinking water sources may result in higher water treatment costs, while phosphorus (P) loading can lead to eutrophication in freshwater systems (e.g. lake). At the basin scale, Iowa is estimated to account for 29% of the N loading into the Mississippi-Atchafalaya River Basin, which contributes to the formation of hypoxic zone in the Gulf of Mexico. <br>

Iowa Nutrient Reduction Strategy document has highlighted that a single best management practice (BMP) may not be sufficient to achieve the 45% N and P load reduction goal. However, several BMPs can combined in an agricultural field or catchment to improve the overall load reduction. This project was designed to compare the stacked benefits of BMPs at two adjacent agricultural catchments located in Black Hawk Lake watershed, Iowa (Figs 1 and 2). <br>

<kbd>
<img src="BHL_aerial_view.jpg" height="400"> <br>
Fig 1: Aerial image of Black Hawk Lake (obtained from blackhawklake.org).
</kbd> <br>

#### Problem statement
This 5-year water quality monitoring project requires that we provide a semi-annual updates of our monitoring results. Traditionally, new monitoring data was added into the existing dataset (or modification to existing dataset) and the same analyses were performed manually every six months. This repetitve process consumed a huge amount of time, which led to the the motivation to automate the process. The goal of this project was to develop a consistent workflow (i.e. reproducibility) to analyze the nutrient/sediment data and the associated environmental parameters (e.g. flow, weather). <br>

The following program will allow any users with minimal python knowledge to analyze the datasets using a consistent approach, in addition to saving time from analyzing each dataset manually every time a addition/modification is made to the dataset. <br>

This program was written to answer the following research questions: <br>
a) Was analyte concentration higher in one catchment than the other? <br>
b) Was analyte load higher in one catchment than the other? <br> 
c) How did environmental factors (flow, precipitation, and temperature) affect analyte concentration and load? <br>

Additional data can be imported to perform additional analysesin the future as needed. See [Project workflow and reproducibility](#project-workflow-and-reproducibility) section for details.

## Method and Approach
#### Monitoring sites and sample collection
Two adjacent catchments, namely catchment 11 and 12, were monitored between 2015 and 2018. Catchment 11 has lower areal extend of BMPs implementation than catchment 12. ISCO automated water samplers were installed to collect continuous flow measurement data and to collected flow-weighted samples at each catchment outlet. Catchment 11 only has one surface outlet, and the monitoring station was named as Surface 11 (S11). Catchment 12 has one surface outlet and one tile outlet, and were named as Surface 12 (S12) and Tile 12 (T12), respectively. The combined load from S12 and T12 represent the total loading from catchment 12. Flow-weighted concentration at catchment 12 was calculated using S12 and T12 concentration and flow data. <br>

<kbd>
<img src="BHL_watershed_map.png" height="400"> <br>
Fig 2: Black Hawk Lake watershed. The lake is located on the north end of the watershed; the monitored catchments (cathcment 11 and 12) are highlighted in green. Side note: "catchment" is labelled as "sub" in this image.
</kbd> 


#### Sample and data analysis  
The water samples were categorized into base flow and event (i.e. precipitation) flow samples. Each sample was analyzed for NH3 (ammonia), NOx (nitrate+nitrite), TN (total nitrogen), DRP (dissolved reactive phosphorus), TP (total phosphorus), and TSS (total suspended solid) concentrations. Nutrient and sediment concentrations between two catchments were tested for significant differences. Normally distributed dataset was tested using t-test; non-normal dataset was tested using Wilcoxon Rank Sum test. In addition, nutrient/sediment concentration was tested for correlation with environmental parameters (flow, precip, temp). Normally distributed dataset was tested using pearsonr correlation; non-normal dataset was tested using spearmanr correlation test. Nutrient and sediment load at each catchment outlet was calculated by multiplying nutrient concentration, flow, and sample duration. The loading rate was then divided by catchment area to allow comparison of load per unit area between two monitored catchments. <br>

#### Project workflow and reproducibility
The project workflow (Fig 3) describes the analysis processes used in the [Python Notebook](https://github.com/jiyeow/jy_project/blob/master/ABE516x_finalproject.ipynb), which included both manual (black arrows) and automated (orange arrows) processes. Manual processes allowed users to visually inspect the data through scatter plots, box plots and data summaries (mean, median, std dev) prior to the automated data analysis process.

In order for a user to reproduce the data analysis, the input data has to be organized into the preset template (see "BHL_data" worksheet). The required inputs are "Site", "Sample date", "Sample interval", "Sample type", "Flow (cms)", "DRP (mg P/L)", "TP (mg P/L)", "TSS (mg/L)", "Nitrate (mg/L)", "TN (mg/L)". As the program was written to loop through a "list_of_analytes", the user may choose to add additional analytes (in concentration format) into the last column of the template worksheet. Note that the user will also need to add the analyte name into the "list_of_analyte" in the program. All data analysis can be performed by simply running the entire program on Python 3 Notebook (or export the script as .py file, then run it in different platform). Several sections will prompt the user to input text (e.g. site selection), if desired; if not desired, the user may choose to skip the step. All main figures will be exported as png files; intermediate (i.e. for visual inspection of dataset prior to data analysis) figures will not be exported.

The main advantage of this program is that a large portion of the data analysis/organization process is automated. For example, the data will be automatically organized into the desired data format prior to data analysis (correlation test, load calculation, t-test). However, the data analysis options are only limited to those that are currently included in this program. Although manual visual inspection will be performed, manual modifications to the program will be needed if the dataset requires an alternate data analysis/organization option. This could be a disadvantage for future users who are not familiar with Python. The other disadvantage (more like future development) is that this program did not incorporate machine learning (I tried a few models but none worked for this dataset due to high sample variability and relatively small sample size). Therefore, a missing data will not be automatically filled with the "prediced value". <br>

An example assignment with instructions from input to output can be found [here](https://github.com/jiyeow/jy_project/blob/master/Example_assignment.ipynb).

<kbd>
<img src="ABE516x_project_workflow.png" height="500"> <br>
Fig 3: Project workflow
</kbd>

#### Integration of class concepts and techniques
One of the primary concepts that I have applied in this project was version control through github. This has allowed me to work on the project at different work stations by simply pulling the latest version through Gitbash. It also allowed me to track the changes that I have made over time. The other common technique in this program was using the loop (while, if, for) function to iterate through datasets, then perform additional data organization/analysis techniques. The data organization techniques include importing raw data (i.e. pd.read), slicing dataset (e.g. iloc), grouping subdatasets (e.g. groupby), and merging subdatasets (e.g. pd.merge). This allowed me to update all the "downstream" subdatasets by simply changing the raw input file. The analysis techniques that were used here were simple math functions (addition, multiplication), t-tests (or Wilcoxon), principal component analysis, and correlation analysis. I also have attempted to apply machine learning models (clustering, linear regression) to predict missing values but was not successful. More machine learning options should be tested in the future. Finally, text scrapping technique was also used to download weather data that was needed for the data analysis.

## Results and Discussion
#### Comparison of nutrient and sediment concentrations

Table 1: Median of analyte concentrations of base flow and event flow samples (2015-2018) at each catchment. The alphabet annotations represent the significant differences between base flow and event flow samples. <br>

|Catchment  | Sample Type   | DRP    | TP     | TSS    | NOx    | TN     |
| ---------:|--------------:| ------:| ------:| ------:| ------:| ------:|
|11         | Base          | 0.003 b| 0.035 b| 15.8 b | 26.9 a | 29.0 a |
|           | Event         | 0.014 a| 0.241 a| 148.0 a| 25.1 a | 28.7 a |
|12         | Base          | 0.007 a| 0.034 b| 7.2 b  | 8.8 a  | 9.1 a  |
|           | Event         | 0.016 a| 0.063 a| 18.6 a | 8.6 a  | 9.4 a  |

Highlights:
- The median concentrations of DRP, TP, and TSS were higher in the event samples than base flow at both catchments; the differences were significant, except for DRP at catchment 12.
- The median concentrations of NOx and TN were similar in base and event flow samples at both catchments; the minor differences were not significant. <br>

Table 2: Median of analyte concentrations of base flow and event flow samples (2015-2018) at each catchment. The alphabet annotations represent the significant differences between catchments. <br>

|Sample Type | Catchment | DRP    | TP     | TSS    | NOx    | TN     |
| ---------- |:---------:| ------:| ------:| ------:| ------:| ------:|
|Base        | 11        | 0.003 b| 0.035 a| 15.8 a | 26.9 a | 29.0 a |
|            | 12        | 0.007 a| 0.034 a| 7.2 b  | 8.8 b  | 9.1 b  |
|Event       | 11        | 0.014 a| 0.241 a| 148.0 a| 25.1 a | 28.7 a |
|            | 12        | 0.016 a| 0.063 b| 18.6 b | 8.6 b  | 9.4 b  |

Highlights: <br>
1) For baseflow samples
- DRP concentrations were significantly lower at catchment 11 than at catchment 12.
- TP concentrations were not significantly different at both catchments.
- TSS, NOx, and TN concentrations were significantly higher at catchment 11 than at catchment 12. <br>
2) For event flow samples
- DRP concentrations were not significantly different at both catchments.
- TP, TSS, NOx, and TN concentrations were significantly higher at catchment 11 than at catchment 12.
 
#### Comparison of nutrient and sediment loads 
<kbd>
<img src="Annual%20comparison%20of%20DRP_load.png" height="250"> <br>
Fig 4: Annual DRP load at catchment 11 and 12. Side note: "catchment" is labelled as "sub" in this figure.
</kbd> <br>
DRP loads were higher at catchment 11 than at catchment 12 during 2016 and 2017, but was lower during 2018.

<kbd>
<img src="Annual%20comparison%20of%20TP_load.png" height="250"> <br>
Fig 5: Annual TP load at catchment 11 and 12. Side note: "catchment" is labelled as "sub" in this figure.
</kbd> <br>
TP loads were consistently higher at catchment 11 than at catchment 12 between 2016 and 2018.

<kbd>
<img src="Annual%20comparison%20of%20TSS_load.png" height="250"> <br>
Fig 6: Annual TSS load at catchment 11 and 12. Side note: "catchment" is labelled as "sub" in this figure.
</kbd> <br>
TSS loads were consistently higher at catchment 11 than at catchment 12 between 2016 and 2018.

<kbd>
<img src="Annual%20comparison%20of%20NOx_load.png" height="250"> <br>
Fig 7: Annual NOx load at catchment 11 and 12. Side note: "catchment" is labelled as "sub" in this figure.
</kbd> <br>
NOx loads were consistently higher at catchment 11 than at catchment 12 between 2016 and 2018.

<kbd>
<img src="Annual%20comparison%20of%20TN_load.png" height="250"> <br>
Fig 8: Annual TN load at catchment 11 and 12. Side note: "catchment" is labelled as "sub" in this figure.
</kbd> <br>
TN loads were consistently higher at catchment 11 than at catchment 12 between 2016 and 2018.

#### Correlation between nutrient/sediment and environmental parameters
PCA analysis was used to as a preliminary step to determine if these environmental parameters can explain the nutrient or sediment concentrations. Note that PCA analysis cannot distinguish individual relationship between nutrient/sediment concentration and environmental parameters. If PC1, PC2, and PC3 explained little variance of the nutrient/sediment data, then correlation test will not likely yield any useful information. If PC1, PC2, and PC3 explained majority of the nutrient/sediment concentration, then correlation test can be used to reveal the individual relationship between nutrient/sediment concentrations and environmental parameters.

The tested environmental parameters were:
- 1-day precipitation
- 2-day precipitation
- 3-day precipitation
- Temperature
- Flow rate

There were 10 PCA outputs, and all showed similar trend. Therefore, only one example output is included here. For individual outputs, refer to [Python Notebook](https://github.com/jiyeow/jy_project/blob/master/ABE516x_finalproject.ipynb) Part 3C.

<kbd>
<img src="Sub12_DRP_PCA.PNG" height="250"> <br>
Fig 9: Example PCA output. DRP data from catchment 12 was used in this analysis. More than 90% of the variance was explained by the environmental parameters.
</kbd>

To prevent having a messy output table (2 catchments x 2 sample types x5 analytes x 5 environmental parameters = 100 correlation tests) and the difficulty to read through the ouputs, only significant correlations (p<0.05) are printed. The test ouputs are summarized in the Tables 3 and 4.

Table 3: Correlations of nutrient/sediment concentration (separated by base and event flow samples) and environmental parameters at catchment 11. Non-significant correlations were left blank in the table. <br>

|Sample Type | Analyte (mg/L) | Flow (cms)| 1-day ppt (mm)| 2-day ppt (mm)| 3-day ppt (mm)| Temp (ºC)|
| ---------- |:--------------:| ---------:| ------------:| ------------:| ------------:| --------:|
|Base        | DRP            |           |              |              |              |          |
|            | TP             |           |              |              |              |          |
|            | TSS            |           |              |              |              |          |
|            | NOx            |           |              |              |              |          |
|            | TN             |           |              |              |              |          |
|Event       | DRP            | 0.486     |              |              |              |          |
|            | TP             | 0.409     |              |              |              | 0.383    |
|            | TSS            | 0.564     |              |              |              | 0.508    |
|            | NOx            |           |              | -0.45        |              |          |
|            | TN             |           |              |              |              |          |

Table 4: Correlations of nutrient/sediment concentration (separated by base and event flow samples) and environmental parameters at catchment 12. Non-significant correlations were left blank in the table. <br>

|Sample Type | Analyte (mg/L) | Flow (cms)| 1-day ppt (mm)| 2-day ppt (mm)| 3-day ppt (mm)| Temp (ºC)|
| ---------- |:--------------:| ---------:| ------------:| ------------:| ------------:| --------:|
|Base        | DRP            |           |              | -0.024       |              |          |
|            | TP             |           |              |              |              |          |
|            | TSS            |           |              |              |              | 0.228    |
|            | NOx            | 0.436     |              |              |              |          |
|            | TN             | 0.478     |              |              |              |          |
|Event       | DRP            | 0.626     |              |              |              |          |
|            | TP             | 0.616     |              |              |              |          |
|            | TSS            | 0.559     |              |              |              |          |
|            | NOx            |           | -0.434       |              |              | -0.319   |
|            | TN             |           |              |              |              | -0.383   |

Only consistent correlations were found between Flow and DRP, TP, and TSS concentrations for event samples.

## Summary of Data Analysis
Key note:
Catchment 11 has smaller aeral extent of BMPs implementation; catchment 12 has larger aereal extent of BMPs implementation.

a) Was analyte concentration higher in one catchment than the other? <br>
Yes, significant differences were found in some of the analytes at these two catchments. Higher TP, TSS, NOx, and TN concentrations were found in catchment 11. However, DRP concentration appeared to be higher in catchment 12. <br>

b) Was analyte load higher in one catchment than the other? <br> 
TP, TSS, NOx, and TN loads were consistenly higher in the catchment 11 during all monitoring years. Meanwhile, DRP loads were higher in catchment 11 during 2016 and 2017, but became lower than catchment 12 during 2018.

c) How did environmental factor (flow, precipitation, and temperature) affect analyte concentration and load? <br>
Only flow rates showed consistent and significant correlations with DRP, TP, and TSS concentrations of event samples.

This summary showed the results of data analysis conducted using data between 2015 and 2018. The tables and figures above can be used in the semi-annual reports. The figures and test outputs will be produced automatically by simply adding new monitoring data into the template worksheet, then run the program. Year-to-year comparison is available for certain data analysis, such as load calculation, box plot, and descriptive summary. Correlation test and significant test are not available for year-to-year comparison (although overall comparison will be updated), but this option can be added in the future.
##

## Supplemental Information
Codes for all data analysis can be found [here](https://github.com/jiyeow/jy_project/blob/master/ABE516x_finalproject.ipynb) <br>
Codes for weather data scrapping can be found [here](https://github.com/jiyeow/jy_project/blob/master/Weather_scrapping.ipynb) <br>
All other files related to this project (e.g. raw input file) can be found [here](https://github.com/jiyeow/jy_project)

Box plots of nutrient/sediment concentrations. <br>
<kbd>
<img src="Box%20plot%20ofDRP.png" height="250"> <br>
Fig S1: DRP (mg/L) concentration at catchment 11 and 12 between 2015 and 2018.
</kbd> <br>

<kbd>
<img src="Box%20plot%20ofTP.png" height="250"> <br>
Fig S2: TP (mg/L) concentration at catchment 11 and 12 between 2015 and 2018.
</kbd> <br>

<kbd>
<img src="Box%20plot%20ofTSS.png" height="250"> <br>
Fig S3: TSS (mg/L) concentration at catchment 11 and 12 between 2015 and 2018.
</kbd> <br>

<kbd>
<img src="Box%20plot%20ofNOx.png" height="250"> <br>
Fig S4: NOx (mg/L) concentration at catchment 11 and 12 between 2015 and 2018.
</kbd> <br>

<kbd>
<img src="Box%20plot%20ofTN.png" height="250"> <br>
Fig S5: TN (mg/L) concentration at catchment 11 and 12 between 2015 and 2018.
</kbd>
<br>
<br>
Pairplot to visualize correlations <br>
<kbd>
<img src="corr_ppSub11.png" height="800"> <br>
Fig S6: Pairplot at catchment 11.
</kbd> <br>

<kbd>
<img src="corr_ppSub12.png" height="800"> <br>
Fig S7: Pairplot at catchment 12.
</kbd>

