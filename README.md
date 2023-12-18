# Analysis_of_Furniture_Sales_Data

SASHELP.PRDSALE :<br>

The SASHELP.PRDSALE dataset was obtained from SAS libraries and  contains information about furniture sales. The data set contains 1,440 observations. It has 10 features.<br>

Feature Description :<br>

•	ACTUAL: The actual sales amount in dollars for furniture products.<br>
•	PREDICT: The predicted sales amount in dollars for furniture products.<br>
•	COUNTRY: The country where the sales data was recorded.<br>
•	REGION: The region within the country where the sales data was collected.<br>
•	DIVISION: The division categorization of sales data, distinguishing between Education and Consumer segments.<br>
•	PRODTYPE: The type or category of the furniture product.<br>
•	PRODUCT: The specific product within the furniture category.<br>
•	QUARTER: The quarter of the year when the sales occurred .<br>
•	YEAR: The year when the sales data was recorded.<br>
•	MONTH: The month when the sales data was recorded.<br>


Code : <br>
   

title "The First Five Observations Out of 1,440";<br>
proc print data=sashelp.prdsale(obs=5) noobs;<br>
run;<br>
title;<br>

OUTPUT:<br>



![Observations](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/391ef3fb-db79-4685-b583-6a41e8b0caec)<br>


title "Sashelp.prdsale --- Furniture Sales Data";<br>
proc contents data=sashelp.prdsale varnum;<br>
ods select position;<br>
run;<br>
title;<br>

Output : <br>

![Contents](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/dc2db247-21b6-42d6-a0e5-5fd46b7d4673)<br>



title "The DIVISION and PRODTYPE Variables";<br>
proc freq data=sashelp.prdsale;<br>
tables DIVISION;<br>
tables PRODTYPE;<br>
run;<br>
title;<br>

Output : <br>

![Freq](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/c7c55a82-1c24-49d0-8f25-7ce6ee2ff793)<br>

title "Correlation between Actual and Predicted variables";<br>

proc corr data=sashelp.prdsale pearson;<br>
   var ACTUAL PREDICT;<br>
run;<br>
title;<br>

Output : <br>

![correlation](https://github.com/SUSMIRICHAD/Road_Accident_Data_Analysis/assets/146381149/701e540c-91f6-4e20-9f6a-26b1620ebedd)<br>

title"Frequency Analysis for categorical Data";<br>
proc freq data=sashelp.prdsale;<br>
   tables COUNTRY REGION DIVISION PRODTYPE PRODUCT;<br>
run;<br>
title;<br>

Output :<br>

![Frequency_analysis](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/0f874cbf-1397-44ab-a0ee-83bf5d14ff71)<br>

DATA VISUALIZATION : <br>


Bar-Line Chart :<br>

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

OUTPUT : <br>

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

Output : <br>

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
  
 Output : <br>

 ![bar3](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/1af1b533-f57c-4eda-8b35-3b5d01e0eb87)<br>


 Stacked Column Chart:<br>

Code : <br>

title 'Actual Sales by Country and Product';<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar Product / response=Actual group=Country stat=percent datalabel;<br>
  xaxis display=(nolabel);<br>
  yaxis grid  label='Actual Sales';<br>
run;<br>
title;<br>

OUTPUT :<br>


![stack1](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/fc2dda44-d2df-4d04-9641-e47a62984514)<br>

title 'Predicted Sales by Country and Product';<br>
proc sgplot data=sashelp.prdsale;<br>
  vbar Product / response=Predict group=Country stat=percent datalabel;<br>
  xaxis display=(nolabel);<br>
  yaxis grid  label='Predicted Sales';<br>
run;<br>
title;<br>

OUTPUT :<br>

![stack2](https://github.com/SUSMIRICHAD/Analysis_of_Furniture_Sales_Data/assets/146381149/652f3d4b-eb29-4d17-a41c-7a91394e2860)<br>



      









