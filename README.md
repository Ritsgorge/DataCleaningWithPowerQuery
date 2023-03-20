# Data Cleaning Challenge

# BACKGROUND
As part of my way of practicing the data analysis skills I have acquired through numerous courses, I decided to take a part in the data cleaning challenge hosted by members of the data field on Twitter. The data used for this challenge was the FIFA 21 dataset which was obtained from kaggle after having webscrapped from sofifa.com.

# OBJECTIVE
Knowing how crucial the data cleaning process is, my goal was to ensure that there is no inconsistencies across the columns or general errors that could pose a risk of generating poorly informed insights in the future.

# DATA CLEANING
I imported and loaded the data into the power query editor for this cleaning challenge. The data contained 77 columns and 18,979 rows. Before starting out on cleaning, I scanned through the data dictionary provided to fully grasp the context of the data presented and to identify irrelevant columns. Next, I checked the data for duplicates using the ID column and found there was none. 
After observing the data, I noticed the following errors that needed cleaning;
-multiple variables stored in one column
-Special characters and different representations
-wrong data types
-Blanks

I started off with the more difficult tasks which included the height and weight columns specifically.


To clean the height column, which had values existing in cm and feet-inches, I split the column into inches from the feet and cm values. Then applied a conditional column which converted the feet to inches by multiplying by 12. Then using another conditional column (now in inches), I multiplied the column by 2.54 to get all values in cm. I changed the data type to whole numbers.

Similar steps were applied for the weight column. Except after splitting the values in kg from those in lbs, I created a conditional column which multiplied the values in kg by 2.2 to obtain the weight in lbs as is the standard. I changed the data type to whole numbers
For the hits column, I also used a conditional column to multiply rows having ‘k’ and those not having with ‘1’ to get the values properly written. I changed the data type to whole numbers.

For the wage, value and release columns, I applied a conditional column to multiply each row bearing ‘M’, ‘K’ with ‘1000000’, ‘1000’ respectively. Any row not having either was multiplied by ‘1’. Thereafter, I used ‘replace values’ to replace the ‘M’, ‘K’ and the ‘£’ with blanks. On the format tab, I added the $ currency sign to the new values as is the standard. I formatted the column in 0 decimal places.

For the contract column, varying values existed so I split the column which produced 4 columns and removed other columns not bearing just years. All entries not existing in year format were replaced with ‘null’ and used ‘replace values’ to change the special character (~) in between the years to a hyphen (-).
For the ova and pot columns which stands for overall rating and potential rating, I used the custom column to divide the rows by 100 and changed the data type to percentages.

For the ratings columns having special characters, I simply splitted the numbers from the characters and deleted the column containing the characters. Then I changed the data type to whole numbers.
As for the blanks in the loan date end column, I replaced empty rows with ‘null’.


# CONCLUSION
Personally, I didn’t remove any columns from the data during the cleaning process because this challenge was primarily for cleaning the dataset. I believe if I were to consequently analyse and visualize the data, the research questions would be a better guide to know what parts of the data I would need to drop.
It was interesting taking part in this challenge as it gave me the opportunity to practice cleaning an actual dirty dataset whilst also learning about functions in power query that I didn’t know existed (the conditional column in particular ).

I am thankful to the organizers and I look forward to more tasks to help me hone my skills.
