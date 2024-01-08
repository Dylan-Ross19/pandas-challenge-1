# pandas-challenge-1
## Part 1: Explore the Data
client_dataset.csv was imported via pandas. 
Some comprehensive methods to explore the data.
To find most data I filtered for the top entries in data frame, and then made another data frame with only the data from the consumables column.
I then filtered for the top subcategory. 
![](<Screenshot 2024-01-08 133020.png>)

A couple more comprehensive methods to gather the top 5 clients with the most entries.

The next part we had to find the top client's total quantity
I utilized the same logic to find the most entries.
Filter all out except the top client. Create another dataframe that only uses the top entry in 'client_id'.
Make another data frame the sums up all the 'qty' column.

## Part 2: Transform the Data
This section I utilized iloc on the top client to showcase that i created new columns, as to not overinudate the user with the entire dataframe over and over.
Created a column subtotal by multiplying the columns unit_price and qty.

Created a function to apply a shipping rate. if the weight is under 51 lbs it will cost $10. Otherwise it will cost $7.
![](<Screenshot 2024-01-08 134957.png>)

Next we created a line_cost column but first created a funtion that multiplies the unit_cost and the quantity and then adds the shipping rate.
Within the new column we used a lambda function that inputs the values into the line_cost_calculation. Axis set to 1 to iterate over rows and not columns.
![](<Screenshot 2024-01-08 135831.png>)

Created a profit column using the same logic as above.

## Part 3: Confirm Your Work
To confirm our work we were given three order ids and its' total order value. Our output needs to match the given information.
I put the three ids in a list and then made a dataframe filtering all the other order ids out.
I used the groupby function we learned about in module 5 to group the order ids together and then summed the total_price column. I then reset the index to keep order_id as my defeault integer.
We then iterated the indeces of each order id which is just the aggregate of all the entries total price. and printed to match the statement above.
![Alt text](<Screenshot 2024-01-08 140940.png>)

## Part 4: Summarize and Analyze
The first prompt asked us to get the top 5 clients by qty and see how much they spent.
The .nlargest method was used to get the top 5 client ids in quantity.
Created a spending dataframe using the groupby and sum method similar to the last prompt in Part 3.
The data has gotten so large that it is reading as exponents. We will clean this up later.

Using the top 5 clients in part 1 we created a dataframe summarizing their ID, total units, total shipping price, total revenue, and profit.
I aggregated each column, and then reset the index to keep client_id as the default integer. We wanted to sort by total profit so I sorted values in a descending order to give us the largest profit first.
![](<summary_dfScreenshot 2024-01-08 141956.png>)

Finally we get to clean the dataframe up and make it presentable.
I asked chat gpt how to apply a dollar sign to all the floats within a data frame, and it suggested using pd.set_option to the 'display.float_format' format to have that and to rid it of exponents put it to the hundreths place. Also adding commas to the numerical values to serpate the thousands.
However there was a single column that uses floats that isn't currency and that was the unit weight.
I singled out that column to not put the $ before the float.
Also replaced the underscores with spaces and capitilized the words using the title method.
![](<formattedScreenshot 2024-01-08 142550.png>)

Finally assorted the cleaned dataframe by the bottom line biggest on top, smallest on bottom.
