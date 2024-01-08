# PowerBI_Call_Centre_Analysis
Here I have analyzed a dataset from a call center and created visuals on overall  performance metrics.
# Call Centre  Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/9805d876-01b3-440e-a085-8313bb0caacf/ReportSection?experience=power-bi


### Problem Statement:	Analyse CALL CENTRE dataset and make informative output out of it.  

### About Dataset :	Let us first go through the data and try analysing/understanding it to visualize the data in any meaningful way to help to get the solution result as per the company requirements.


### Columns Present in dataset are : 		CALLER ID, this column gives the unique identification number of each caller
						AGENT, here we have names of each agent 
						DATE, gives you the date of each call have been received/got it on that particular date
						TIME, we have time here in hh:mm:ss format of each call have been received
						TOPIC, name of the subject on calls has been received (topic names)
						ANSWERED, here we get to know whether call has been received or abounded by giving us a value in yes/no format(Y/N) 
						RESOLVED, name of the column itself says, calls which agents received it resolved or not. (Y/N)
						SPEED OF ANSWER IN SECOND, what is the speed of each call
						AVG. TALK DURATION, particular agent how long has been gone through on particular call-in average duration
						SATISFATION RATE, the rating of each agent, who has got how much rating on satisfying callers query on each call


### Note:	 Before performing the task, make sure to perform all these 3 steps for better result/output
		 	-Firstly, replace all null values/blank values to 0
 			-Change datatype wherever required 
 			-Extract seconds, minutes from avg. talk duration and create a new column by naming -Duration on calls (change the data type)


After understanding/visualize the data, design a report for the call centre review information. Make sure to create interactive insight of report.

	

Below are the information/KPIs/demands to be performed in order to meet client’s requirement:

	Calculate total number of calls
	Create a new column to calculate total number of calls answered and total number of calls been rejected
	Calculate total % of calls been answered and total % of calls been rejected
	Create a new column to calculate how many calls been resolved 
	Create a new column to calculate how many calls been not-resolved 
	Find top 1 agent who answered maximum calls
	Top 1 agent who got highest satisfaction rate
	Use a chart to display total number of calls by topic wise
	Duration on calls by every agent
	Total calls by  months for the year 2021
	Use Slicers to interactive with other charts by month and day wise.
	Finally, give the overall 2021 performance satisfaction ratings . Use any suitable custom chart to show(give) overall 2021 performance satisfaction rating. 



### Steps followed 

Data Cleaning:

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : It was observed that  there were some columns where the entire columns were null valued  , hence they were removed 
- Step 4 : The columns which had few null values were replaced with zeroes as asked by the stakeholders 
- Step 5 : A column name "minutes" was added where the minute value of the column "Average Talk Duration " was taken using the "time-->minute" from  "date and time" pane
- Step 6 : A column name "seconds" was added where the second value of the column "Average Talk Duration " was taken using the "time-->seconds" from  "date and time" pane
- Step 7 : The two new columns "minutes and seconds"  were merged into a single column and named as "Duration of Call"
- Step 8 : Data type of the new column "Duration of Call" was changed to duration 
- Step 9 : Calculated Columns & DAX Function used :
		1) Calls Answered  : This column is created with a purpose to count the total Answered Calls and later on the percentage of answered calls. 
				     Here  "Answered" Column is used on which we apply DAX

				   	### DAX Function : Calls Answered = IF('Call Centre Performance'[Answered (Y/N)]="Y",1,0)


		2) Calls Rejected  : This column is created with a purpose to count the total Rejeced Calls and later on the percentage of rejected calls
				     Here  "Answered" Column is used on which we apply DAX

					### DAX Function : Calls Rejected = IF('Call Centre Performance'[Answered (Y/N)]="Y",1,0)


 		3) Calls Resolved : This column is created with a purpose to count the total Resolved Calls and later on the percentage of Resolved calls. 
				    Here  "Resolved " Column is used on which we apply DAX

					### DAX Function : Calls Answered = IF('Call Centre Performance'[Answered (Y/N)]="Y",1,0) 


		4) Calls Not Resolved : This column is created with a purpose to count the total Resolved Calls and later on the percentage of Resolved calls. 
				     	Here  "Resolved " Column is used on which we apply DAX

					### DAX Function : Calls Answered = IF('Call Centre Performance'[Answered (Y/N)]="Y",1,0) 

- Step 10 : Measures & DAX funtion used :

		1) Total Calls :  This measure is created to count the total calls made 
					### DAX Function :Total Calls = count('Call Centre Performance'[Call Id])
		

		2) % of Calls Answered : This measure is created to count the percentage of Answered calls
					### DAX Function :% Of Calls Answered = CALCULATE(SUM('Call Centre Performance'[Calls Answered])/[Total Calls])

		3) % of Calls rejected : This measure is created to count the percentage of rejected calls 
					### DAX Function :% Of Calls Answered = % Of Calls Rejected = CALCULATE(SUM('Call Centre Performance'[Calls Rejected])/[Total Calls])


- Step 11 : A title to the report Page is given using "Text Box" and named as  " Call Centre Performance Analysis"
- Step 12 : 8 Cards are created to visualize the :
				1) Total Calls 
				2) Calls Answered 
				3) Calls Rejected 
				4) Total Agents   ( Ditinct count of "Agents" was taken)
				5) Calls Anwered By %
				6) Calls Rejected By %
				7) Max Calls Answered (Filtered the Top1 Agent on the basis of the total sum of "Calls Answered" Calculated column )
				8) Highest Satisfaction rate (Filtered the Top1 Agent on the basis of the Average of Satisfaction rating column )

![Call centre Cards values](https://github.com/bigit91/PowerBI_Call_Centre_Analysis/assets/155818756/84c0d1fb-063e-4666-b8ce-6f2798515c6f)
![Calls ans and Highest Sat](https://github.com/bigit91/PowerBI_Call_Centre_Analysis/assets/155818756/f5ac38c4-0d11-471f-af2e-167d78544002)

- Step 13 : 2 Date Slicers are created :
				1) Month wise date slicer ( Horizontal tile)
				2) Overall Date (Slider)

- Step 14 : A tree map chart of the Agents by Sum of call duration(In minutes)  was created 
![Treemap Call by agent](https://github.com/bigit91/PowerBI_Call_Centre_Analysis/assets/155818756/3ad74426-3df3-46ad-9473-c2af00a3481f)

- Step 15 : A Pie chart is created to visulaize the Number of calls and percentage of  "Calls Answered by each Agent "

- Step 16 : An area chart is create to  find out the frequency of calls ("Total Calls by Month")  in each month

![Pie and area Chart](https://github.com/bigit91/PowerBI_Call_Centre_Analysis/assets/155818756/afb12f64-f283-40b2-be38-3e141aa73db3)

- Step 17 : A Rating visual(by TME AG) was imported using get more visual . It was used to find out the "Avg Satisfaction" rating of all the employees 
![Rating](https://github.com/bigit91/PowerBI_Call_Centre_Analysis/assets/155818756/82ebc12d-eca4-412c-b88e-465269023aa2)

- Step 18 : A bar chart was created to visualize "Total calls by Resolution"

- Step 19 : A donut Chart was created to "Topic wise calls " answered by the agents




Insights : 
		1) Out of total 5000 calls , 4054 calls were answered which is 81.1% , 946 calls went unanswered/rejected which is 18.9% of the total calls.
		2) Max calls were answered by Jim (536) which constitues 13.2 % of the overall calls as it  can  be seen in the pie  chart 
		3) Customers were much satisfied and comfortable talking to Dan who has  Highest Customer Satisfaction rate
		4) The total calls in the month of January was 1772 which decred in themonth of feb and march making Jan the peak call month
		5) Average satisfaction rate is just 2.76 out of 5 which is a little worrysome . Measures need to be taken to increase the same 
		6) Total Calls that were resolved was 3646 and unresolved cases were 1354 . 
		7) Lastly Most calls were  based on the Streaming topic (1022 calls) and the least were based on  Admin support (976)

Dashboard Snap :
		![Dashoard](https://github.com/bigit91/PowerBI_Call_Centre_Analysis/assets/155818756/b29d23e3-54a6-4e7a-9bd8-c52b5c67e93e)
