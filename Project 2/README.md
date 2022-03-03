
# Triple-A Ames Housing Price Model

### Contents
- [Problem Statement](#problemstatement)
- [Executive Summary](#executivesummary)
- [Data Dictionary](#datadictionary)
- [Model Performance](#modelperformance)
- [Recommendations](#recommendations)

***
<div id="problemstatement"></div>

## Problem Statement

As part of the Ames City Council's digitalization drive, the Planning Division has been tasked to develop a housing price model to forecast the sale price of properties in Ames. As the Planning Division's appointed data scientist, construct a regression-based model by utilizing past data on house sales in Ames, Iowa between 2006 to 2010, which includes over 2000 records of houses sold and 80 accompanying attributes. The model should be reasonably accurate, applicable and accessible. For accuracy and applicability, the threshold set is a maximum degradation rate of 15% on both R2-scores and RMSE, which will be construed as acceptable estimates for bias and variance respectively. 

<div id="executivesummary"></div>

## Executive Summary

In Part 1, after laying the project foundations and defining the problem statement in the first section, the second section conducts preliminary EDA on the predictor variables by type (discrete, continuous, ordinal, nominal). The section also examines the target variable (housing sale price) in contrast to the national average, where an additional column for log sale price was created for more meaningful comparison with predictor features. After which, data cleaning was performed which included removing outliers based on abnormally high gross living area and site area, dropping four features (Pool quality, Misc. features, Alley, Fence) with an exceptionally high proportion of missing values and imputing values for remaining missing data, converting to appropriate datatypes where relevant, dropping Garage year built due to potential multicollinearity, and mapping of ordinal features into numeric form. 

In Part 2, the predictor features were first preprocessed for visualization and engineering. This included removing features with high-modal skewness (Street, Condition 2, Roof material, Heating, Central), scoring relevant nominal features (Neighbourhood, Zoning, Land contour) and categorizaing features based on potential interfacing. Next, feature engineering was carried out using the constructed feature categories and through a rigid assessment, a total of 30 predictor variables (including dummies) across the categories were eventually identified. Pre-modelling analysis revealed that geographical and internal built environment factors have the largest influence on housing prices in Ames, followed closely by external built environment factors. On the contrary, parcellation and miscellaneous factors pale in comparison, except where the Age of the house is concerned.

In Part 3, model training, tuning and benchmarking was performed, which involved dropping another two featuers (Gross living area, Garage cars). A total of four models were developed (namely Ordinary Least Squares, Ridge, Lasso and Elastic Net), which were then systematically evaluated. Eventually, the Elastic Net model was selected as the production model as it returned the best R2-scores and RMSE on the training dataset. When applied to the full training dataset, the production model returned consistent R2-scores of about 0.9, which is well within the established baseline R2-score of 0.85 based on a maximum degradation rate of 15%. Likewise, the kaggle score (same in effect to Test RMSE) of ~26,000 is within the maximum permissible RMSE of ~USD27,000 based on the same degradation rate of 15%. Therefore, the accuracy and applicability criteria underpinning the model is achieved. In the closing chapter, we acknowledge the primary assumptions before stating the recommendations and areas for improvement. 

<div id="datadictionary"></div>

## Data Dictionary

The data dictionary for the predictor features in the production model is as follows: 

|Feature|Type|Origin|Description|
|---|---|---|---|
|**neighborhood**|*int*|engineered feature|Imputed score (1 to 4) based on dividing the neighbourhoods into four baskets according to mean house sale price|
|**overall_qual**|*int*|train.csv|Rates the overall material and finish of the house|
|**ms_zoning**|*int*|engineered feature|Imputed score (1 to 7) based on the following zoning order: Commercial > Industry > Agriculture > Floating Village Residential > Residential Low Density > Residential Medium Density > Residential High Density|
|**ms_subclass_60_house_style_2Story**|*int*|dummy interaction term|Interaction term derived by multiplying dummy feature for ms_sub_class_60 with dummy feature for house_style_2story|
|**lot_area**|*int*|train.csv|Lot size in square feet|
|**lot_shape**|*int*|engineered feature|Imputed score (0 to 3) based on regularity of plot shape|
|**lot_frontage**|*float*|train.csv|Linear feet of street connected to property|
|**paved_drive**|*int*|engineered feature|Imputed score (0 to 2) based on full, partial or no paved driveway|
|**totrms_abvgrd**|*int*|train.csv|Total rooms above grade (does not include bathrooms)|
|**kitchen_qual**|*int*|train.csv|Kitchen quality|
|**fireplaces**|*int*|train.csv|Number of fireplaces|
|**fireplace_qu**|*int*|engineered feature|Imputed score (0 to 5) based on fireplace quality|
|**abv_grd_sf**|*int*|engineered feature|Total above grade area derived by aggregating 1st floor area and 2nd floor area|
|**total_bath**|*int*|engineered feature|Total number of bathrooms derived by aggregating above grade and below grade full/half baths|
|**below_grd_sf**|*float*|engineered feature|Total below grade area derived by aggregating total basement area and type 1 basement finished area|
|**overall_bsmt_score**|*int*|engineered feature|Overall basement score derived by aggregating basement quality, basement exposure and type 1 basement finish|
|**exter_qual**|*int*|engineered feature|Imputed score (0 to 4) based on exterior quality|
|**total_outdoor_area**|*float*|engineered feature|Total outdoor area derived by aggregating garage area, masonry veneer area and all porch/deck areas|
|**overall_garage_score**|*int*|engineered feature|Overall garage score derived by aggregating garage quality, garage condition and garage  finish|
|**foundation_PConc**|*int*|dummy feature|1 indicates house has poured concrete foundation, 0 if otherwise|
|**garage_type_Attchd**|*int*|dummy feature|1 indicates house has attached garage, 0 if otherwise|
|**garage_type_Detchd**|*int*|dummy feature|1 indicates house has detached garage, 0 if otherwise|
|**roof_style_Hip**|*int*|dummy feature|1 indicates house has hip roof style, 0 if otherwise|
|**exterior_1st_VinylSd**|*int*|dummy feature|1 indicates house has vinyl siding for exterior covering, 0 if otherwise|
|**mas_vnr_type_None**|*int*|dummy feature|1 indicates house does not have masonry veneer type, 0 if otherwise|
|**age**|*int*|engineered feature|Age of house derived by year sold minus year remodelled/A&A|
|**electrical**|*engineered feature*|engineered feature|Imputed score (0 to 4) based on electricity system|
|**sale_type_New**|*int*|dummy feature|1 indicates sale type for house is new, 0 if otherwise|

<div id="modelperformance"></div>

## Model Performance

Table summaring the relative model performance (including production model):  

||Train R2 Score|Train Cross-validation Mean Score|Train Cross-val RMSE Score|Test R2 Score|Test RMSE Score|
|---|---|---|---|---|---|
|**OLS**|0.9057|0.9014|26,351.9597|0.857|20,504.0885|
|**Ridge**|0.9057|0.9015|26,336.9819|0.8571|20,458.6934|
|**Lasso**|0.9056|0.9017|26,351.9593|0.8577|20,452.2196|
|**Enet**|0.9056|0.9017|26,339.8375|0.8578|20,421.308|
|**Production Model (based on Enet)**|0.8969|0.8952|26,518.8845|-|26,704.7271|

<div id="recommendations"></div>

## Recommendations

The envisioned goal to develop a regression-based predictor model guided by the triple-A framework (accurate, applicable, accessible) for Ames housing sale prices was achieved and thresholds established duly complied with. The model serves its primary purpose of providing an indicative estimated selling price of a given house in Ames. Having successfully developed the production model, the next step would be to liaise with the relevant Ames City Council departments (e.g. IT Division) in creating an end-product for consumers. This includes integrating the production model with the interface on Beacon - where users can identify subject houses by keying in the Parcel ID, to create a map/geospatial app for end-users, of which the Ames population and individuals/families considering to migrate to Ames will form the bulk. The process of purchasing a house is afterall, an inherently spatial process. 
