# DATA CLEANING: FIFA 2021

# Background
As part of my way of practicing the data analysis skills I have acquired through numerous courses, I decided to take a part in the data cleaning challenge hosted by members of the data field on Twitter. The data used for this challenge was the FIFA 21 dataset which was obtained from kaggle after having webscrapped from sofifa.com.
It contains information about football players and their performance until 2021.

# Objective
Knowing how crucial the data cleaning process is, my goal was to ensure that there is no inconsistencies across the columns or general errors that could pose a risk of generating poorly informed insights in the future.

# Data Cleaning
I imported and loaded the data into the power query editor for this cleaning challenge. The data contained 77 columns and 18,979 rows. Before starting out on cleaning, I scanned through the data dictionary provided to fully grasp the context of the data presented and to identify irrelevant columns. Next, I checked the data for duplicates using the ID column and found there was none. 
After observing the data, I noticed the following errors that needed cleaning;
-multiple variables stored in one column
-Special characters and different representations
-wrong data types
-Blanks

# Height & Weight

I started off with the more difficult tasks which included the height and weight columns.

![wei,hei  before](https://user-images.githubusercontent.com/116006674/226363994-61a7cc07-5c77-49d2-8f2c-ea50cac8124b.png)       ![height,weight](https://user-images.githubusercontent.com/116006674/226364410-4d2fd516-2c04-4e6f-8d2e-84b8b4231006.png)

To clean the height column, which had values existing in cm and feet-inches, I split the column into inches from the feet and cm values. Then applied a conditional column which converted the feet to inches by multiplying by 12. Then using another conditional column (now in inches), I multiplied the column by 2.54 to get all values in cm. I changed the data type to whole numbers.

Similar steps were applied for the weight column. Except after splitting the values in kg from those in lbs, I created a conditional column which multiplied the values in kg by 2.2 to obtain the weight in lbs as is the standard. I changed the data type to whole numbers
For the hits column, I also used a conditional column to multiply rows having ‘k’ and those not having with ‘1’ to get the values properly written. I changed the data type to whole numbers.

# Value, Wage, Release Clause
![values  before](https://user-images.githubusercontent.com/116006674/226365299-5ac25cdc-0803-489f-90c8-83d90c03cf0f.png)                  ![values](https://user-images.githubusercontent.com/116006674/226365365-0a55c8ab-048a-4438-87bf-4bd896cd30a5.png)


For the wage, value and release columns, I applied a conditional column to multiply each row bearing ‘M’, ‘K’ with ‘1000000’, ‘1000’ respectively. Any row not having either was multiplied by ‘1’. Thereafter, I used ‘replace values’ to replace the ‘M’, ‘K’ and the ‘£’ with blanks. On the format tab, I added the $ currency sign to the new values as is the standard. I formatted the column in 0 decimal places.

# Contract
![contract before](https://user-images.githubusercontent.com/116006674/226365573-fd84edd5-f4b7-4371-ba91-eed42462faa8.png)
![contract](https://user-images.githubusercontent.com/116006674/226365580-8124ea5c-9cfb-4d37-b372-21a46bc19960.png)


For the contract column, varying values existed so I split the column which produced 4 columns and removed other columns not bearing just years. All entries not existing in year format were replaced with ‘null’ and used ‘replace values’ to change the special character (~) in between the years to a hyphen (-).

# OVA, POT
![ova](https://user-images.githubusercontent.com/116006674/226373947-9b6eb81b-24b7-4a6d-b9c9-8bbbfa2e439c.png)


For the ova and pot columns which stands for overall rating and potential rating respetively, using the custom column function, I divided the rows by 100 and changed the data type to percentages.

# IR, W/F, SM
![ratings before](https://user-images.githubusercontent.com/116006674/226365770-4f5ed100-0a05-4d74-9089-f85c76f10131.png)
![ratings](https://user-images.githubusercontent.com/116006674/226365780-022eee34-823a-4440-a4cf-e093e7484844.png)

For the ratings columns having special characters, I simply splitted the numbers from the characters and deleted the column containing the characters. Then I changed the data type to whole numbers.
As for the blanks in the loan date end column, I replaced empty rows with ‘null’ using the 'replace values' function.


# CONCLUSION
Personally, I didn’t remove any columns from the data during the cleaning process because this challenge was primarily for cleaning the dataset. I believe if I were to consequently analyse and visualize the data, the research questions would be a better guide to know what parts of the data I would need to drop.
It was interesting taking part in this challenge as it gave me the opportunity to practice cleaning an actual dirty dataset whilst also learning about functions in power query that I didn’t know existed (the conditional column in particular ).

I am thankful to the organizers and I look forward to more tasks to help me hone my skills.
