# DATA CLEANING: FIFA 2021

![image](https://user-images.githubusercontent.com/116006674/226679309-57a1715c-3007-483f-9c1d-e399e1fa21d7.png)

# Background
In a quest to practice my acquired data analysis skills, I decided to take a part in the data cleaning challenge organized by members of the data field on Twitter. The data used for this challenge was the FIFA 21 dataset which was obtained from kaggle after having webscrapped from sofifa.com. It contains information about football players and their performance until 2021.

# Objective
Knowing how crucial the data cleaning process is, my goal was to ensure that there were no inconsistencies or general errors that could pose a risk of generating poorly informed insights after analysis.

# Data Cleaning
I imported and loaded the data into the power query editor for this cleaning challenge. The data contained 77 columns and 18,979 rows. Before starting out on cleaning, I scanned through the data dictionary provided to fully grasp the context of the data presented and to identify irrelevant columns. Next, I checked the data for duplicates using the ID column and found there was none. 
After observing the data, I noticed the following errors that needed cleaning;
-multiple variables stored in one column
-Special characters and inconsistencies
-wrong data types
-Blanks

# Height & Weight

I started off with the more difficult tasks which included the height and weight columns. These columns had values existing in different measurements as well as wrong data type.
Before                                                                                                                   |                                                                                                            After
:-----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------
![wei,hei  before](https://user-images.githubusercontent.com/116006674/226363994-61a7cc07-5c77-49d2-8f2c-ea50cac8124b.png)| ![height,weight](https://user-images.githubusercontent.com/116006674/226364410-4d2fd516-2c04-4e6f-8d2e-84b8b4231006.png)

To clean the height column, which had values existing in cm, feet & inches, I split the the inches into a separate column from the feet and cm values. Then applied a conditional column which converted the feet to cm by multiplying by 12 and rows having values in cm multiplied by 1. Then using another conditional column, I multiplied the column containing the inches by 2.54 to get all values in cm. Then I added the two columns having the values now exisiting in cm. i removed all other columns created as well as the initial messy column. I changed the data type to whole numbers.

Similar steps were applied for the weight column as same observation was made in this column. This column contained weight values in both kg and lbs. After splitting the values in kg from those in lbs, I created a conditional column which multiplied the values in kg by 2.2 to obtain the weight in lbs as is the desired standard of measurement. I changed the data type to whole numbers.

# Hits
Before                                                                                                                   |                                                                                                            After
:-----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------
![hits before](https://user-images.githubusercontent.com/116006674/226389723-99f0e4ce-3976-40a1-b0fe-4b03b9c80138.png)|![hits after](https://user-images.githubusercontent.com/116006674/226390679-ebc62b07-2bc2-4184-afd4-df2101f39959.png)


The hits column had to be normalized as some values had 'K' attached t them. I used a conditional column to multiply rows having ‘K’ with '1000' and those not having with ‘1’ to get the values properly written. Then I removed  the 'K' by replacing with blank and changed the data type of the column to whole numbers before multiplying it with the conditional column created earlier. 

# Value, Wage, Release Clause
Before                                                                                                                   |                                                                                                            After
:-----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------
![values  before](https://user-images.githubusercontent.com/116006674/226365299-5ac25cdc-0803-489f-90c8-83d90c03cf0f.png)|![values](https://user-images.githubusercontent.com/116006674/226365365-0a55c8ab-048a-4438-87bf-4bd896cd30a5.png)


The wage, value and release columns had inconsistencies such as the prefix '£' and suffix 'M', and 'K'. I applied a conditional column to multiply each row bearing ‘M’, ‘K’ with ‘1000000’, ‘1000’ respectively. Any row not having either was multiplied by ‘1’ in the 'else' rule. Thereafter, I used ‘replace values’ to replace the ‘M’, ‘K’ and the ‘£’ with blanks before multiplying with the conditional column. I changed the data type of the column to '$' currency sign as is the standard.

# Contract
Before                                                                                                                   |                                                                                                            After
:-----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------
![contract before](https://user-images.githubusercontent.com/116006674/226365573-fd84edd5-f4b7-4371-ba91-eed42462faa8.png)|![contract](https://user-images.githubusercontent.com/116006674/226365580-8124ea5c-9cfb-4d37-b372-21a46bc19960.png)


The contract column contained varying values such as 'free', 'on loan', long dates and year. First, I split the column which produced 4 columns and removed other columns not bearing just years. All entries not existing in year format were replaced with ‘null’ and I used ‘replace values’ to change the special character (~) in between the years to a hyphen (-). I split the years to separate columns using the delimeter (-) and renamed them to 'contract start' and 'contract end' respectively.

# OVA, POT
Before                                                                                                                   |                                                                                                            After
:-----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------
![ova](https://user-images.githubusercontent.com/116006674/226373947-9b6eb81b-24b7-4a6d-b9c9-8bbbfa2e439c.png)|![POT AFTER (2)](https://user-images.githubusercontent.com/116006674/226383357-922542b7-b34c-4992-9098-aabc9d3513c4.png)


The ova and pot columns which stands for overall rating and potential rating respetively had a wrong data types. Using the custom column function, I divided the rows by 100 and changed the data type to percentages.

# IR, W/F, SM
Before                                                                                                                   |                                                                                                            After
:-----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------
![ratings before](https://user-images.githubusercontent.com/116006674/226365770-4f5ed100-0a05-4d74-9089-f85c76f10131.png)|![ratings](https://user-images.githubusercontent.com/116006674/226365780-022eee34-823a-4440-a4cf-e093e7484844.png)

For the ratings columns having special characters, I simply splitted the numbers from the characters and deleted the column containing the characters. Then I changed the data type to whole numbers.
As for the blanks in the loan date end column, I replaced empty rows with ‘null’ using the 'replace values' function.


# CONCLUSION
Personally, I didn’t remove any columns from the data during the cleaning process because this challenge was primarily for cleaning the dataset. I believe if I were to consequently analyse and visualize the data, the research questions would be a better guide to know what parts of the data I would need to drop.
It was interesting taking part in this challenge as it gave me the opportunity to practice cleaning an actual dirty dataset whilst also learning about functions in power query that I didn’t know existed (the conditional column in particular ).

I am thankful to the organizers and I look forward to more tasks to help me hone my skills.
