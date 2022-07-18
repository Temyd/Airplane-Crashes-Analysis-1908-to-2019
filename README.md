# Airplane-Crashes-Analysis-1908-to-2019 ✈️


# Introduction 📖
Its being more than 20 days learning the world of Data Analytics in the ongoing #NG30daysoflearning training , in this past days i have learnt a lot about Data Analytics from creating a developers account on microsoft down to visualisation and telling stories with my report. This is a project to **Show my mentors what I can do with what I have learnt**

# Problem statement 🧾
A flight in an airplane is a highly exciting experience. It is flying in the air like a bird. The whole experience is wonderful. With more and more people preferring flying to traveling by trains or buses, there is no surprise that number of plane crashes will never end. They include the military as well as the civilian planes and the accidents do occur all over the six continents.
To be a witness to an accident is bad, but to be a part of it is greatly horrifying. As a witness a person feels helpless, however as a victim one feels let down by the Almighty and is forced to say good-bye to this world forever or spend the rest of his life completely crippled.
The odds of death of a person per total no of passengers flown is 1 to 6 million according to the Telegraph News(UK)

Objective of this project is to analyze the data set and derive various insights about the aviation accidents from 1908 to 2019

# Data Sourcing 📤
Two dataset was used
  - This Dataset was created on Kaggle in September 2016 but the original version was hosted by Open Data by [Socrata](https://opendata.socrata.com/Government/Airplane-Crashes-and-Fatalities-Since-1908/q2te-8cvq) and is (no longer available).  
The dataset contains data of airplane accidents involving civil, commercial and military transport worldwide from 9/17/1908 till 6/8/2009 
Data Can be gotten from [here](https://aka.ms/30DLDATGitHubRepo)
  - Second dataset is from 6/29/2009 to 7/30/2019
  Also gotten from [Kaggle](https://www.kaggle.com/datasets/cgurkan/airplane-crash-data-since-1908?resource=download)

# Data Transformation/ Cleaning 🧼
The data was dirty and had to be cleaned. Cleaning and Transformation took place in excel and power query.

Most of my data cleaning took place in excel

1.	I loaded both dataset into separate excel workbooks


2.	First Dataset contained 5,268 rows and 13 columns from 9/17/1908 to 6/9/2009

<img width="806" alt="1908 to 2019" src="https://user-images.githubusercontent.com/105246702/179434186-076b5b6d-fa20-4137-8e5f-d24ddd324697.png">

3.	Second dataset contained 254 rows and 13 columns from 6/29/2009 to 7/30/2019

<img width="800" alt="2009 to 2019" src="https://user-images.githubusercontent.com/105246702/179434141-61163d4e-12c2-45b0-a454-e6d2f31c3e8e.png">

4.	I checked to make sure they had the same columns and datatypes.

The attributes of the dataset are

  - Date: Date of accident
  - Time: Local time in 24hr
  - Location: Location of the accident
  - Operator: Airline/operator of the aircraft
  - Flight: flight no assigned by the aircraft operator
  - Route: complete/ partial route flown prior to the accident
  - Type: aircraft type
  - Registration: ICAO registration of the aircraft
  - Cn/in: construction or serial number/ line or fuselage number
  - Abroad: total abroad(passengers/crew)
  - Fatalities: Total fatalities abroad (passengers/crew)
  - Ground: total killed on ground
  - Summary: brief description of the accident and the cause if known
  
5.	I then merged both into a single workbook and continued the cleaning process

<img width="732" alt="merged" src="https://user-images.githubusercontent.com/105246702/179434440-c076be26-6b16-40ab-aa04-da9eee971b1e.png">

6.	Merging both datasets give a total of 5522 rows and 13 columns

7.	Missing values which were replaced with nil

<img width="556" alt="a  replace with nil" src="https://user-images.githubusercontent.com/105246702/179433681-be8d4634-313c-4321-af5c-e3d91ea2505d.png">

8.	I removed and replaced some wrong characters that was in the dataset using the find and replace function (Ctrl H)

<img width="791" alt="find and replace" src="https://user-images.githubusercontent.com/105246702/179433712-7760a938-d293-4bcd-80aa-85b9939d7c0e.png">

9.	I created a column to answer the question ‘WERE THERE SURVIVORS FROM THE CRASH’ I am interested in knowing the total number of crash that all abroad died, and the ones that had survivors. I used the if fxn in excel =IF([@Aboard]=[@Fatalities], "No survivor", "There are survivors") 

<img width="778" alt="are there survivors" src="https://user-images.githubusercontent.com/105246702/179433735-7a8ba1d7-12dc-4ee6-afcf-3d7ed82748d7.png">

10.	I also created a column to show total number of crashes that had survivors =COUNTIF(J:J,"There are survivors")

<img width="746" alt="there is survivor" src="https://user-images.githubusercontent.com/105246702/179433762-8300728b-38a6-4176-85d5-3c8a8d712356.png">

11.	A column also showing Total no of crashes without survivors =COUNTIF(J:J, "No Survivor")

<img width="639" alt="total crash without survivors" src="https://user-images.githubusercontent.com/105246702/179433784-ea5ad4e5-02a2-4e6d-80a8-2089a9fa24e4.png">

12.	I also created 

  - Survival column= abroad-fatalities
  <img width="548" alt="f  survivors formular" src="https://user-images.githubusercontent.com/105246702/179433835-56dd8227-ac68-4e56-b1d1-132e02f46e67.png">

  - Total fatality column= fatalities + ground
  <img width="670" alt="total fatalities" src="https://user-images.githubusercontent.com/105246702/179433842-0dff5e98-3875-48c8-8a50-0e3c016df51a.png">
  
13.	Using flash fill function in excel I extracted the countries from the location column

<img width="885" alt="flash fill to get countries" src="https://user-images.githubusercontent.com/105246702/179433858-5ba2c960-ae74-434e-a984-913ff566d635.png">

After all, done, I then saved, and it was ready to be loaded into Power bi

Using get data from excel workbook, I loaded the dataset into power query where I also did further transformation

In Power Query

14. Hour columns was also created, this was extracted from time

15. Year, Month and Weekday column were extracted from the date column
<img width="630" alt="new column in power query" src="https://user-images.githubusercontent.com/105246702/179434611-0b1fdff9-cfdf-49f4-9142-d2dfb6ffbd9c.png">

16. Having learnt about performance optimization in power bi 
  - I removed columns that added no value to the analysis (Flight, Registration, and cn/in columns)
  - And also created new measures _(this was after loading into power bi)_  (Total fatality on air, Total fatality on ground, Total people on board, Total survivors, Total crash, Grand fatality (ground + air) 
  <img width="303" alt="dax measure" src="https://user-images.githubusercontent.com/105246702/179434698-c8f6ce46-64e8-4eae-91ef-7cd648487557.png">

17. I checked data types and changed them to their correct type.

After thorough checking and validation, I closed and loaded my dataset into power bi ready for Visualization

# Data Visualization 📊
They say a picture is worth a thousand words. Once our data was tidy and neat, it was ready for visualization in power bi.

# Analysis 📈
### Brief Summary

From **9/17/1908 17:18** till **7/30/2019 02:00** there was a total of **5,522crashes** with **153,840** people on board, we had **112,335** fatalities with **41,626** survivors. There were also fatalities on the ground **5,857** giving us a total of **118,077** fatalities both in the air and on ground.

Out of the crashes, **3,688** crashes had no survivors, everyone on board died while **1,834** crashes had survivors.

### Countries with Highest Fatalities


### Yearly Trend

  - Crashes by year
There was a gradual increase in Plane crashes from 1908 to 1972, 1972 was highest with 104 crashes, trend shows there has been a reduction in plane crashes since then. Futher Analysis shows that improvement in flight saftey has helped no of crashes drop by 91% from 1972 to 2019.

  - Fatality in the air
Year 1972 had the highest fatality with 2,397 fatalities. There was a gradual increase from 1908 till 1972. Year 1972 was said to be the worst year in the aviation industry [💡](https://www.flightsafetyaustralia.com/2017/01/the-year-of-flying-dangerously-1972/). While report says that 1972 is the worst year, report also says that year 2017 was the safest year in history of commercial air travel [💡]()

Further dive into year 1972 showed that the Aeroflot airline topped the list of crashes in that year with total of 524 fatalities

2 major peaks was also seen in the trend 1985 and 1996 with 2670 and 2386 deaths respectively. From 1996 we can see a drastic reduction in number of fatalities till 2019.
 
  - Fatality on the Ground
Year 2001 was the deadliest with a total death of 2891 and the incidence is linked to the event of 9/11/2001. The highest in history so far.


Note; While visualizing I noticed, there was a very high spike in 2001 showing 5,641 deaths. Research shows that only about 3000 people were killed, exploring the data further showed that 2,750 was counted twice for ground on 9/11. Thus, I replaced one of the values with 0. 

_Reason why 2,570 was "repeated" twice is because both aircraft crashes occurred in the same location, World Trade Center, and so you can't really separate the fatalities on the ground that were caused specifically by each aircraft_[💡BolajiO](https://twitter.com/BolajiO_?s=20&t=5EGoUbGNFFq4VvHi1VVQPQ)

<img width="562" alt="wrong 2001" src="https://user-images.githubusercontent.com/105246702/179375036-80692be8-23c1-4d37-9f0e-07b4cc734d37.png">
<img width="943" alt="twin crash" src="https://user-images.githubusercontent.com/105246702/179375062-3c299349-f287-4b96-9692-45409b50fc7e.png">
<img width="934" alt="replaced with 0" src="https://user-images.githubusercontent.com/105246702/179375066-817b72df-e3ba-40f5-bdb9-55a97381b1c5.png">

  - Total fatality
Combining both ground and air fatality 2001 was the worst year with 4289 deaths followed by 1972 with 2967 deaths, then 1985 with 2671 

  - Trend with Number of People boarding plane and Fatalities
  Number of people boarding flight has increased over the  years, a report by [The World Bank](https://data.worldbank.org/share/widget?end=2020&indicators=IS.AIR.PSGR&start=1970&view=chart)

  thus comparing the average number of people on board to fatalities shows that fatalities has reduced this can be linked to improvement in flight safety.


### Monthly Trend
Highest number of crashes was in December with 537 crashes followed by January with 512 crashes, both months fall in the winter period. The winter period is a cold period and there are higher instances of slippery runways thus reduce brake action, reduce visibility due to snow mist and fog, and many more that might be a likely cause of the higher crashes.

Though the weather has its own advantage by giving cool and oxygen rich.

It should also be noted that People tend to travel more December due to festivity around that, thus with more People on board and higher crashes the fatality rate is also higher during this period.

From Auguest until the end of the year the high crash rate increases, Autumn falls in August, most people tend to travel more during this season thus 

### Operators
Aeroflot was the most boarded among the operators, it also accounted for the airline with highest fatalities rate with 7156 fatalities. And most crashes 179 crashes. Followed by Military Us Air Force with 176 crashes and 3717 fatalities, the next which is a commercial airline is Air France with 70 crashes and 1734 fatalities.

  - Short History About Aeroflot
![image](https://user-images.githubusercontent.com/105246702/179375851-403a5cbf-aceb-4645-a7e5-1d069fdeb563.png)

A Russian airline, founded in 1923, the flag carrier and largest airline of Russia (and formerly the Soviet Union) (formerly the world's largest airline). Making Aeroflot one of the oldest active airlines in the world. Has been in operation for about 99 years.
Research states that one of the reasons for their high crash was due to the collapse of the country’s aircraft manufacturing industry which caused the Russian airlines to rely on old aircraft they have been using for decades.

Analysis of thier crashes over time,shows it has reduced over the years. An indication of growth and improvement. Aeroflot: from world's deadliest airline to one of the safest in the sky[💡](telegraph.co.uk/travel/news/Aeroflot-from-worlds-deadliest-airline-to-one-of-the-safest-in-the-sky/)


### Type
Douglas DC3 is the most boarded, has the highst crashes and fatality rate among other types of airplane.
Brief history about Douglas tells us that it's a propeller-driven airliner, which had a lasting effect on the airline industry in the 1930s to 1940s and World War II. 
The DC-3 had many exceptional qualities compared to previous aircraft. It was fast, had a good range, was more reliable, and carried passengers in greater comfort. Before the war, it pioneered many air travel routes. It was able to cross the continental US from New York to Los Angeles in 18 hours, with only three stops. It is one of the first airliners that could profitably carry only passengers without relying on mail subsidies. Following the war, the airliner market was flooded with surplus transport aircraft, and the DC-3 was no longer competitive due to its size and speed.

### Causes of Airplane Crash from Summary Column

### Analysis on Fatalities that occured on the ground

The year 2001, month September has the highest ground death. September 11 to be precise was the worst period of ground death ever seen there was a total of 4 crashes that day 
<img width="959" alt="911 death" src="https://user-images.githubusercontent.com/105246702/179379551-7a77552d-aaf4-43fe-89fc-d657e07ae0cc.png">

9/11

On September 11, 2001—a clear, sunny, late summer day—al Qaeda terrorists aboard hijacked passenger planes and carried out coordinated suicide attacks against the World Trade Center in New York City and the Pentagon in Washington, D.C., killing everyone on board the planes and nearly 3,000 people on the ground. A fourth plane crashed into a field near Shanksville, Pennsylvania, killing all on board, after passengers and crew attempted to wrest control from the hijackers.

![image](https://user-images.githubusercontent.com/105246702/179379591-84baa21a-03aa-4b57-82c3-f38c024033e7.png)

Till this day a memorial is held every 9th of September at The National September 11 Memorial & Museum a memorial and museum in New York City commemorating the September 11, 2001, attacks.

Majority of the death occurred in New York City, New York.


Operator ‘American Airlines’ and ‘UnitedAir Lines’ were used in the attack

  - This incidence is followed by Year 1996, A ground fatality that happened in Africa.

 The 1996 Air Africa crash occurred on 8 January when an overloaded Air Africa Antonov An-32B aircraft, from Moscow Airways, Kinshasa and bound for Kahemba Airport, overshot the runway at N'Dolo Airport in Kinshasa, Zaire (now the Democratic Republic of the Congo) after failing to take off and ploughed into Kinshasa's Simbazikita street market. Although four of the aircraft's six crew survived, between 225 and 348 fatalities and around 253 serious injuries occurred on the ground. This crash remains the **deadliest in African history**, and caused the most ground fatalities of any air accident in history, superseded only by the intentional crashes of American Airlines Flight 11 and United Airlines Flight 175 in the September 11 attacks.
[Read further]( 1996 Air Africa crash - Wikipedia)

![image](https://user-images.githubusercontent.com/105246702/179379745-89b0f2f6-486c-458a-8216-0e34cb1f168c.png)


### Analysis of Fatalities that occured in the air based on location

Tenerife Canarlyislands has max fatality with 761.

There were 4 crashes in the area, with the highest occurring March 27,1977 out of 644 people on board there was a casualty of 583

<img width="960" alt="tene" src="https://user-images.githubusercontent.com/105246702/179376385-f1449d7e-57c1-4ab0-a8f7-8f8d423ed396.png">

The Tenerife airport disaster occurred on 27 March 1977, when two Boeing 747 passenger jets collided on the runway at Los Rodeos Airport (now Tenerife North Airport) on the Spanish island of Tenerife. The collision occurred when KLM Flight 4805 initiated its takeoff run while Pan Am Flight 1736 was still on the runway. The impact and resulting fire killed everyone on board KLM 4805 and most of the occupants of Pan Am 1736, with only 61 survivors in the front section of the aircraft. Resulting in 583 fatalities, the disaster is the deadliest accident in aviation history.
The Pan Am aircraft was named Clipper Victor. The KLM aircraft was named Rhine River.

![image](https://user-images.githubusercontent.com/105246702/179378378-2dd2217d-8756-41f9-bdcf-d3256b17172c.png)



Followed by Mt.Osutaka,nearUenoVillage,Japan with 520 fatalities

The aircraft suffered a naft pressure bulkhead failure at 23,900ft. The aircraft had severe control difficulties with loss of all controls and eventually after 40 minutes, collided with a mountain. This was due to Improper repair of the bulkhead while being supervised by Boeing engineers after a tail strike in 1978. It’s the **worst single plane disaster** in aviation history. [Kyu Sakamoto](https://www.bing.com/ck/a?!&&p=3f5d361e743b908e2a456dc694165c81ea9e1e14567007511929e0b458459756JmltdHM9MTY1ODAxNzk3OSZpZ3VpZD00Njc3MDU4Yy1jOWFkLTRmYTItOGY0ZS00Yjc3ZmJlZTM4YzEmaW5zaWQ9NTg2NQ&ptn=3&fclid=01fc51ac-0568-11ed-8d21-03c3925136b2&u=a1aHR0cDovL2VuLndpa2lwZWRpYS5vcmcvd2lraS9LeXVfU2FrYW1vdG8&ntb=1), 43, famous for his Japanese song ['Sukiyaki'](https://www.bing.com/ck/a?!&&p=c0af3f88b42c5ae0c53915cb427167d2011281a4300713bf136a02eadc3d3fdeJmltdHM9MTY1ODAxNzk3OSZpZ3VpZD00Njc3MDU4Yy1jOWFkLTRmYTItOGY0ZS00Yjc3ZmJlZTM4YzEmaW5zaWQ9NTI2NQ&ptn=3&fclid=01fb3158-0568-11ed-b45f-ee56e6fc2f90&u=a1aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1FVFhfRUpnT1Z3OA&ntb=1) was killed in the accident. 

![image](https://user-images.githubusercontent.com/105246702/179379228-86da6ecb-0277-4747-95b5-dc6a45d4bd63.png)

### Likely Causes using Word Cloud

![wordcloud cause](https://user-images.githubusercontent.com/105246702/179455663-619c4fac-25d4-4540-915d-781fda3b7673.png)



# Findings
  - First aircrash was in 1908,there was a steady increase in number of crashes till 1972 this can be linked to airplane becoming more popular and also the wars fought in the 70's from 1972 there has been a decrease in the crashes due to better and improved saftey measures and advanced technology
  - Most Crashes occured December and January which are winter periods, thus the cold weather seems to be a threat to air flights
  - Aeroflot a commercial airline had the highest number of crashes, followed by US Military airline, this may be as a result of their use in warfare
  - Douglas DC 3 has the highest number of crashes, this is linked to its widespread use during the world war 2
  - Countries with highest fatalities are USA probably due to their high frequency of flights, Russia due to rough terrain and weather conditions and Colombia due to poor fligth safety standards or regulations
  - Looking at trend of plane crashes since 1908, the rate has been decreasing since 1970. Fatalities has also been decreasing as well since 1970,when compared to the amount of passengers that has been travelling since 1970, there is a negative correlation between them. As passengers keep increasing there has been a decrease in fatalities and crashes
  
  







