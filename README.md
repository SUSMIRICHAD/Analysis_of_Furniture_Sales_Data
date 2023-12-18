# Analysis_of_Furniture_Sales_Data

SASHELP.PRDSALE :

The SASHELP.PRDSALE dataset was obtained from SAS libraries and  contains information about furniture sales. The data set contains 1,440 observations. It has 10 features.

Feature Description :

•	ACTUAL: The actual sales amount in dollars for furniture products.
•	PREDICT: The predicted sales amount in dollars for furniture products.
•	COUNTRY: The country where the sales data was recorded.
•	REGION: The region within the country where the sales data was collected.
•	DIVISION: The division categorization of sales data, distinguishing between Education and Consumer segments.
•	PRODTYPE: The type or category of the furniture product.
•	PRODUCT: The specific product within the furniture category.
•	QUARTER: The quarter of the year when the sales occurred .
•	YEAR: The year when the sales data was recorded.
•	MONTH: The month when the sales data was recorded.


Code : 
   

title "The First Five Observations Out of 1,440";
proc print data=sashelp.prdsale(obs=5) noobs;
run;
title;

OUTPUT:



![Observations](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/391ef3fb-db79-4685-b583-6a41e8b0caec)


title "Sashelp.prdsale --- Furniture Sales Data";
proc contents data=sashelp.prdsale varnum;
ods select position;
run;
title;

Output : 

![Contents](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/dc2db247-21b6-42d6-a0e5-5fd46b7d4673)



title "The DIVISION and PRODTYPE Variables";
proc freq data=sashelp.prdsale;
tables DIVISION;
tables PRODTYPE;
run;
title;

Output : 

![Freq](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/c7c55a82-1c24-49d0-8f25-7ce6ee2ff793)

title "Correlation between Actual and Predicted variables";

proc corr data=sashelp.prdsale pearson;
   var ACTUAL PREDICT;
run;
title;

Output : 

![correlation](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/701e540c-91f6-4e20-9f6a-26b1620ebedd)

title"Frequency Analysis for categorical Data";
proc freq data=sashelp.prdsale;
   tables COUNTRY REGION DIVISION PRODTYPE PRODUCT;
run;
title;

Output :

![Frequency_analysis](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/0f874cbf-1397-44ab-a0ee-83bf5d14ff71)

DATA VISUALIZATION : 


Bar-Line Chart :

title"Bar-Line Chart for Monthly Sales Comparison:Actual vs. Predicted Sales";
proc sgplot data=sashelp.prdsale;
  vbar month/ response=actual datalabel datalabelattrs = (weight = bold)
                   fillattrs= (color = tan);
  vline month/ response=predict
                 lineattrs =(thickness = 3) markers;
  xaxis label= "Month";
  yaxis label = "Sales";
  keylegend / location=outside position=bottom across=1;
  run;
  title;

OUTPUT : 

![Bar-Line1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/79ff6e48-f2ad-410d-b3ec-6bf8937d4279)



title"Bar-Line Chart for Quarterly Sales Comparison:Actual vs. Predicted Sales";
proc sgplot data=sashelp.prdsale;
  vbar Quarter/ response=actual datalabel datalabelattrs = (weight = bold)
                   fillattrs= (color = tan);
  vline Quarter/ response=predict
                 lineattrs =(thickness = 3) markers;
  xaxis label= "Quarter";
  yaxis label = "Sales";
   keylegend / location=outside position=bottom across=1;
  run;
  title;

Output : 

![bar2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/5faf859e-3162-42c7-b7c4-6191ff09ed30)



title"Bar-Line Chart for Yearly Sales Comparison:Actual vs. Predicted Sales";
proc sgplot data=sashelp.prdsale;
  vbar year/ response=actual datalabel datalabelattrs = (weight = bold)
                   fillattrs= (color = tan);
  vline year/ response=predict
                 lineattrs =(thickness = 3) markers;
  xaxis label= "Year";
  yaxis label = "Sales";
  keylegend / location=outside position=bottom across=1;
              run;
  title;
  
 Output : 

 ![bar3](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/1af1b533-f57c-4eda-8b35-3b5d01e0eb87)


 Stacked Column Chart:

Code : 

title 'Actual Sales by Country and Product';
proc sgplot data=sashelp.prdsale;
  vbar Product / response=Actual group=Country stat=percent datalabel;
  xaxis display=(nolabel);
  yaxis grid  label='Actual Sales';
run;
title;

OUTPUT :


![stack1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/fc2dda44-d2df-4d04-9641-e47a62984514)

title 'Predicted Sales by Country and Product';
proc sgplot data=sashelp.prdsale;
  vbar Product / response=Predict group=Country stat=percent datalabel;
  xaxis display=(nolabel);
  yaxis grid  label='Predicted Sales';
run;
title;

OUTPUT :

![stack2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/652f3d4b-eb29-4d17-a41c-7a91394e2860)



      









