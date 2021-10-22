# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

***
## SAT & ACT analysis of state in California
***


### Problem Statement

 This project aims to analyse  **2019 SATs and ACTs scores of Year 12 students for districts in California**, to help the **state** identify districts with poorer performance, in order to **allocate resources to help improve performance** to keep students in California competitive.

### Background
The SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). They have different score ranges, which you can read more about on their websites or additional outside sources (a quick Google search will help you understand the scores for each test):
* [SAT](https://collegereadiness.collegeboard.org/sat)
* [ACT](https://www.act.org/content/act/en.html)

Despite colleges and universities putting the requirement of standardized tests (ACTs & SATs) to a halt ([source](https://www.smithsonianmag.com/innovation/has-pandemic-put-end-to-sat-act-180978167/)), taking standardized tests will still provide the students with more alternatives in terms of the selection of schools they can apply to. There are still a large number of schools with compulsory standardized tests ([source](https://www.compassprep.com/college-profiles/)), hence if they are unable to apply for schools with optional standardized test, it keeps their options for alternative universities open.

Instead of the investing in schools to increase participation rate, we can also increase the number of students going to universities by investing in the education structure (e.g. providing subsidised tuition, extra classes, etc.). Even though most prestigious universities and colleges do not require ACTs and SATs, those which are less prestigious still have ACTs and SATs as an entrance requirement. This way, we can increases competitiveness and improve the performance of students in California, as it allows more students to get into universities.

***
## Framework
#### 1. Datasets
Two datasets were used for the purpose of this project:

> 1. **act_2019_ca**: which contains the participation rate and average test scores by state for ACT in 2019 for schools in the state of California
> 2. **sat_2019_ca**: which contains the participation rate and number of students who achieved test scores above benchmark (ERW = 480, Math = 530) by state for SAT in 2019 for schools in the state of California

#### 2. Data Cleaning
The following data cleaning was done before Exploratory Data Analysis:
* Replaced null data with mean values of State of California. If it cannot be replaced, remove rows.
* Data errors identified were fixed accordingly.
*The **sat_2019_ca** datasets were imported and and aligned to similar format as the **act_2019_ca** data.
*The 2 datasets were merged, and further cleaning was done to remove all null values.
* Created a new data variable to calculate the participation rate of both tests, by dividing number of test takers by total number of students enrolled.
* Imported final dataset for Exploratory Data Analysis and Visualisation.

#### 3. Data Dictionary

|**Feature**|**Type**|**Dataset**|**Description**|
|---|---|---|---|
|**cit_dis_sch**|*float*|act_ca|The city-district-school code. If analysis was done on district level, it will be city-district, for school, it will be city-district-school. So all districts will have the same city-district code.|
|**school**|*object*|act_ca|Name of school in which students who took their ACTs in 2019 were from.|
|**district**|*object*|act_ca|The district that the school was located, where students who took their ACTs in 2019.|
|**city**|*object*|act_ca|City that the school was located, where students who took their ACTs in 2019.|
|**enroll_act**|*float*|act_ca|Number of year 12 students who enrolled into school in 2019.|
|**testtakers_act**|*float*|act_ca|Number of year 12 students who took the ACTs in 2019.|
|**reading_act**|*float*|act_ca|The average score for the reading section of the ACT taken in California in 2019. This value ranges from 1 to 36.|
|**english_act**|*float*|act_ca|The average score for the english section of the ACT taken in California in 2019. This value ranges from 1 to 36.|
|**math_act**|*float*|act_ca|The average score for the math section of the ACT taken in California in 2019. This value ranges from 1 to 36.|
|**science_act**|*float*|act_ca|The average score for the science section of the ACT taken in California in 2019. This value ranges from 1 to 36.|
|**num_above21_act**|*float*|act_ca|The number of students with a composite ACT score of above or equal to 21. This value ranges from 1 to 36 and is obtained by taking the averaging scores from all four sections (english, math, reading, and science), and only students who scored above or equal to 21 where included|
|**pct_above21_act**|*float*|act_ca|The percentage of students with a composite ACT score of above or equal to 21 out of the number of test takers.(*unit example:45.30% will be 0.4530 (4 d.p.)*)|
|**enroll_sat**|*float*|sat_ca|Number of year 12 students who enrolled into school in 2019.|
|**testtakers_sat**|*float*|sat_ca|Number of year 12 students who took the SATs in 2019.|
|**num_erw_benchmark_sat**|*float*|sat_ca| Number of year 12 students who scored above the bench mark of 480 for Evidence-Based Reading. The score for Evidence-Based Reading ranges from 200-800.|
|**pct_erw_benchmark_sat**|*float*|sat_ca| The percentage of students with a SAT score of above or equal to 480 for Evidence-Based Reading, out of the number of test takers.(*unit example:45.30% will be 0.4530 (4 d.p.)*)|
|**num_math_benchmark_sat**|*float*|sat_ca|Number of year 12 students who scored above the bench mark of 530 for Math. The score for Math ranges from 200-800.|
|**pct_math_benchmark_sat**|*float*|sat_ca|The percentage of students with a SAT score of above or equal to 480 for Math, out of the number of test takers.(*unit example:45.30% will be 0.4530 (4 d.p.)*)|
|**num_tot_benchmark_sat**|*float*|sat_ca|Number of year 12 students who scored above the bench mark of 530 and 480 for both Evidence-Based Reading and Math respectively.|
|**pct_tot_benchmark_sat**|*float*|sat_ca|The percentage of students  scored above the bench mark of 530 and 480 for both Evidence-Based Reading and Math respectively, out of the number of test takers.(*unit example:45.30% will be 0.4530 (4 d.p.)*)|
|**act_participation**|*float*|act_ca|The percentage of ACT test takers over year 12 students who are enrolled in school. This is a data derived from the data set, taking **testtakers_act** / **enroll_act**|
|**sat_participation**|*float*|sat_ca|The percentage of SAT test takers over year 12 students who are enrolled in school. This is a data derived from the data set, taking **testtakers_sat** / **enroll_sat**|

#### 3. Analysis summary

###### 3.1 Which districts & schools have the lowest participation rates for 2019 SAT and ACT?
|**District**|**School [District *if different*]**|
|---|---|
|Adelanto Elementary | *San Diego Workforce Innovation High [Borrego Springs Unified]*|
Trona Joint Unified|California STEAM San Bernardino|
|Warner Unified|    |


Table above derived by using .groupby() by grouping columns, and aggregating data for participation rate for each test.

|**District**|**Test Type**|
|---|---|
|Borrego Springs Unified|ACTs|
|Meridian Elementary|ACTs|
|Liberty Elementary|SATs|
|Harmony Union Unified|SATs|


###### 3.2 Which districts have the lowest percentage of students performing above recommended benchmarks for the 2019 SAT and ACT?
|**District**|**School [District *if different*]**|
|---|---|
|Golden Plains Unified | 0% above benchmark for ACT and SAT|
|Williams Unified |0% above benchmark for SAT|

### Conclusions

State contracts and state funded test are key drivers to SAT and ACT participation.

**Subsidised Test fees & college fairs**
Hence in terms of districts, the State of California should place more emphasis on the following 3 districts as they have low participation rate in **both** tests:
- Adelanto Elementary
- Trona Joint Unified
- Warner Unified

Within these districts, these schools should be provided with extra help and fundings in the form of subsidised tests fees, etc., as they have the poorest ACT and/ or SAT participation:
- California STEAM San Bernardino | Trona Joint Unified
- San Diego Workfornce Innovation High | Borrego Springs Unified

Should budget permit, some emphasis should also be placed on the following districts as well as they have poor participation rates:
- Borrego Springs Unified (ACT)
- Meridian Elementary (ACT)
- Liberty Elementary (SAT)
- Harmony Union Elementary (SAT)


**Subsidised tuition fees & increased teaching quality**
Next, the State of California should place more emphasis on the following 3 districts as they have poor performance in **both** tests:
- Golden Plains Unified | 0% above benchmark for ACT and SAT
- Williams Unified |0% above benchmark for SAT


**Subjects to focus on**

*ACTs*
- English, Math, and Science sections in the ACTs have similar means, but English is the most dispersed, with the widest min-max range, as well as outliers.
- This means that the competency of students in english is the most diverse with large skill differences, as compared to math or science.

*SATs*
- Most students are competent in the Evidence Based Writing (EBW) section of the SATs, as compared to math due to the higher min value as well as median value.
- However, Math is a lot more dispersed, with the full min-max range, this means that the competency of students in math for SATs to close up the skill differences between students.
