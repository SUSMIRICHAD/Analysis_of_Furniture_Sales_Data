# Analysis_of_Furniture_Sales_Data

<h2><b>SASHELP.PRDSALE :</b></h2><br>

The SASHELP.PRDSALE dataset was obtained from SAS libraries and  contains information about furniture sales. The data set contains 1,440 observations. It has 10 features.<br>


<h2><b>Feature Description :</b></h2><br>

•	ACTUAL: The actual sales amount in dollars for furniture products.<br><br>
•	PREDICT: The predicted sales amount in dollars for furniture products.<br><br>
•	COUNTRY: The country where the sales data was recorded.<br><br>
•	REGION: The region within the country where the sales data was collected.<br><br>
•	DIVISION: The division categorization of sales data, distinguishing between Education and Consumer segments.<br><br>
•	PRODTYPE: The type or category of the furniture product.<br><br>
•	PRODUCT: The specific product within the furniture category.<br><br>
•	QUARTER: The quarter of the year when the sales occurred .<br><br>
•	YEAR: The year when the sales data was recorded.<br><br>
•	MONTH: The month when the sales data was recorded.<br><br>



<h5>Code :</h5> <br>
   

title "The First Five Observations Out of 1,440";<br>
proc print data=sashelp.prdsale(obs=5) noobs;<br>
run;<br>
title;<br>


<h5>OUTPUT:</h5><br>



![Observations](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/391ef3fb-db79-4685-b583-6a41e8b0caec)<br>


title "Sashelp.prdsale --- Furniture Sales Data";<br>
proc contents data=sashelp.prdsale varnum;<br>
ods select position;<br>
run;<br>
title;<br>


<h5>Output :</h5> <br>

![Contents](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/dc2db247-21b6-42d6-a0e5-5fd46b7d4673)<br>



title "The DIVISION and PRODTYPE Variables";<br>
proc freq data=sashelp.prdsale;<br>
tables DIVISION;<br>
tables PRODTYPE;<br>
run;<br>
title;<br>

<h5>Output : </h5><br>

![Freq](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/c7c55a82-1c24-49d0-8f25-7ce6ee2ff793)<br>

title "Correlation between Actual and Predicted variables";<br>

proc corr data=sashelp.prdsale pearson;<br>
   var ACTUAL PREDICT;<br>
run;<br>
title;<br>

<h5>Output :</h5> <br>

![correlation](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/701e540c-91f6-4e20-9f6a-26b1620ebedd)<br>

title"Frequency Analysis for categorical Data";<br>
proc freq data=sashelp.prdsale;<br>
   tables COUNTRY REGION DIVISION PRODTYPE PRODUCT;<br>
run;<br>
title;<br>

<h5>Output :</h5><br>

![Frequency_analysis](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/0f874cbf-1397-44ab-a0ee-83bf5d14ff71)<br>

<h2><b></b>DATA VISUALIZATION : </b></h2><br>


<h2><b>Bar-Line Chart :</b></h2><br>

title"Bar-Line Chart for Monthly Sales Comparison:Actual vs. Predicted Sales";<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar month/ response=actual datalabel datalabelattrs = (weight = bold)<br>
                   fillattrs= (color = tan);<br>
  vline month/ response=predict<br>
                 lineattrs =(thickness = 3) markers;<br>
  xaxis label= "Month";<br>
  yaxis label = "Sales";<br>
  keylegend / location=outside position=bottom across=1;<br>
  run;<br>
  title;<br>

<h5>OUTPUT : </h5><br>

![Bar-Line1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/79ff6e48-f2ad-410d-b3ec-6bf8937d4279)<br>



title"Bar-Line Chart for Quarterly Sales Comparison:Actual vs. Predicted Sales";<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar Quarter/ response=actual datalabel datalabelattrs = (weight = bold)<br>
                   fillattrs= (color = tan);<br>
  vline Quarter/ response=predict<br>
                 lineattrs =(thickness = 3) markers;<br>
  xaxis label= "Quarter";<br>
  yaxis label = "Sales";<br>
   keylegend / location=outside position=bottom across=1;<br>
  run;<br>
  title;<br>

<h5>Output :</h5> <br>

![bar2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/5faf859e-3162-42c7-b7c4-6191ff09ed30)<br>



title"Bar-Line Chart for Yearly Sales Comparison:Actual vs. Predicted Sales";<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar year/ response=actual datalabel datalabelattrs = (weight = bold)<br>
                   fillattrs= (color = tan);<br>
  vline year/ response=predict<br>
                 lineattrs =(thickness = 3) markers;<br>
  xaxis label= "Year";<br>
  yaxis label = "Sales";<br>
  keylegend / location=outside position=bottom across=1;<br>
              run;<br>
  title;<br>
  
 <h5>Output :</h5> <br>

 ![bar3](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/1af1b533-f57c-4eda-8b35-3b5d01e0eb87)<br>


<h2><b>Stacked Column Chart:</b></h2><br>

<h5>Code:</h5><br>

title 'Actual Sales by Country and Product';<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar Product / response=Actual group=Country stat=percent datalabel;<br>
  xaxis display=(nolabel);<br>
  yaxis grid  label='Actual Sales';<br>
run;<br>
title;<br>

<h5>OUTPUT :</h5><br>


![stack1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/fc2dda44-d2df-4d04-9641-e47a62984514)<br>

title 'Predicted Sales by Country and Product';<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar Product / response=Predict group=Country stat=percent datalabel;<br>
  xaxis display=(nolabel);<br>
  yaxis grid  label='Predicted Sales';<br>
run;<br>
title;<br>

<h5>OUTPUT :</h5><br>

![stack2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/652f3d4b-eb29-4d17-a41c-7a91394e2860)<br>


<h2><b>Time Series Analysis:</b></h2><br>
   <h3><b>Sorting the dataset by YEAR :</b></h3><br>
   
title"Univariate Time Series Analysis"<br>

ods noproctitle;<br>
ods graphics / imagemap=on;<br>

proc sort data=SASHELP.PRDSALE out=Work.preProcessedData;<br>
	by YEAR;<br>
run;<br>

<h2><b>ARIMA Model (Performing univariate time series analysis):</b></h2><br>

proc arima data=Work.preProcessedData plots(only)=(series(corr) residual(corr <br>
		normal) forecast(forecast));<br>
	identify var=ACTUAL;<br>
	estimate method=ML;<br>
	forecast lead=12 back=0 alpha=0.05 id=YEAR interval=month;<br>
	outlier;<br>
	run;<br>
 title;<br>
 
 <h5>Output</h5>

 ![uni](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/d0aa5f19-4ecf-460f-91e4-71e80b6c4ed3)<br><br>

 ![Trendcor](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/b5c3c5db-6cac-4cfd-8190-27c467b58010)<br><br>

 ![Maxlike](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/865ed52a-df30-4411-b4b0-648eb5902550)<br><br>

 ![resi](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/582e3615-81a5-4a0a-b09c-199f5fd27851)<br><br>

 ![resnor](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/3b0974d8-1474-4908-bda0-f5f98892a201)<br><br>

 ![resdis](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/b6ea2af2-451d-4332-8874-4d35cf236c09)<br><br>

 ![resqq](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/b4bee117-f17e-4b43-9acc-ad3f12c1d79d)<br><br>

 ![for](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/d097c7b9-b814-43f9-9499-50436e01a815)<br><br>

 ![foract](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/0bfafa4e-21ce-4628-9c95-7b8a16958b20)<br><br>

<h2><b>Predictive Modeling:<h2><b><br>

    <h3><b>Proc GLM (Performing one-way ANOVA):</b></h3><br>
/*One-Way ANOVA*/<br>
title "One-Way ANOVA: Analyzing Predicted Sales by Country" <br>
ods noproctitle;<br>
ods graphics / imagemap=on; <br>
proc glm data=SASHELP.PRDSALE;<br>
	class COUNTRY;<br>
	model PREDICT=COUNTRY;<br>
	means COUNTRY / hovtest=levene welch plots=none;<br>
	lsmeans COUNTRY / adjust=tukey pdiff alpha=.05;<br>
	run;<br>
quit;<br>
title;<br>
![1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/2fcf4709-0e51-4cff-90d0-387c7b198375)<br><br>

![2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/af869e7b-fb33-4924-a28d-7d07d74e19a2)<br><br>
![3](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/15331156-1dd0-41c8-a591-a1107b685f2a)<br><br>
![4](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/4673d6ba-f529-4a49-8893-553c0d086ee5)<br><br>
![5](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/906236ae-fda0-42de-8862-adbb3d3f3083)<br><br>
![6](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/2dd51238-1559-4cc1-a93e-b851ae7ebb66)<br><br>
![7](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/914ee50a-c51e-47a5-9c32-0668cbc4424d)<br><br>

<h2><b>Proc Discrim (Performing discriminant analysis) :</b></h2> <br>
/* Discriminant Analysis*/<br>
title "Discriminant Analysis: Analyzing Product Sales";<br>

ods noproctitle;<br>

proc discrim data=SASHELP.PRDSALE pool=yes;<br>
	class PRODUCT;<br>
	var ACTUAL PREDICT;<br>
run;<br>
title;<br>

Output :

![1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/f67e4a74-ddea-43db-bf34-34a1ad1b4ee4)<br><br>
![2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/492f8622-27a5-4043-8067-8a666f4607c0)<br><br>
![3](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/190b5434-3d15-4afd-bd2c-fd27f74c165b)<br><br>

 
 



 


      









