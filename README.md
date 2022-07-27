# Capstone Project: Airplane-Crashes-Analysis-1908-to-2019 ✈️
<img width="505" alt="Intro" src="https://user-images.githubusercontent.com/105246702/179857478-660f5a8b-7d9c-45e6-8724-c3fab1f3b11b.png">

# Introduction 📖
It’s being more than 20 days learning the Data Analytics in the ongoing [#NG30daysoflearning](https://twitter.com/TheOyinbooke/status/1540103138568556544?s=20&t=czg8tAAOx-n4yht-FHB1tw), in these past days, I have learnt a lot about Data Analytics from creating a developer's account on Microsoft down to visualization and telling stories with my report. This is a project to **Show my mentors what I can do with what I have learnt**.

# Background Study
The first and the second airplane crashes occurred in France and America in 1785 and 1908 respectively. While the former led to the death of the two occupants, the latter resulted into one mortality and one morbidity. The incidence of the airplane crashes has been on the increase since then.
The first crash that led to the death of more than 300 persons took place in 1974, while the biggest loss of life overall in a collective incident is the 2,997 mortalities in the organized terrorist attack of airplanes and occupied buildings in 2001. However, there has been reduction in the prevalence of crashes in the
past one decade.

# Problem statement 🧾
  A flight in an airplane is a highly exciting experience. It is flying in the air like a bird. The whole experience is wonderful. With more and more people preferring flying to traveling by trains or buses, there is no surprise that number of plane crashes will never end. They include the military as well as the
civilian planes and the accidents do occur all over the six continents. 

  To be a witness to an accident is bad, but to be a part of it is greatly horrifying. As a witness, a person feels helpless, however, as a victim
one feels let down by the Almighty and is forced to say good-bye to this world forever or spend the rest of his life completely crippled. The odds of death of a person per total no of passengers flown is 1 to 6 million according to the Telegraph News (UK).

  Most of the airplane crashes can be traced to a variety of causes such as: pilot error, air traffic controller error, design and manufacturer flaws, maintenance letdowns, interference, or severe weather.
  
  Hence, the objective of this project is to analyze the data sets on the subject matter and derive various insights about the aviation accidents from 1908 to 2019.

# Data Sourcing 📤
The initial dataset given to us was from 1908 to 2009, to further observe the trend of aviation crashes I took a step further in sourcing for dataset that contained data from 2009 till 2019
  - First Dataset (1908 to 6/8/2009)
This Dataset was created on Kaggle in September 2016, but the original version was hosted by Open Data by [Socrata](https://opendata.socrata.com/Government/Airplane-Crashes-and-Fatalities-Since-1908/q2te-8cvq) and is (no longer available).  
The dataset contains data of airplane accidents involving civil, commercial and military transport worldwide from 9/17/1908 till 6/8/2009 
Data Can be gotten from [here](https://aka.ms/30DLDATGitHubRepo)
  - Second dataset is from 6/29/2009 to 7/30/2019
  Also gotten from [Kaggle](https://www.kaggle.com/datasets/cgurkan/airplane-crash-data-since-1908?resource=download)

# Data Transformation/ Cleaning 🧼

The data was dirty and had to be cleaned. Cleaning and Transformation took place in excel and power query.
###### Most of my data cleaning took place in excel.
  - I loaded both dataset into separate excel workbooks
  
  - First Dataset contained 5,268 rows and 13 columns from 9/17/1908 to 6/9/2009
  
  - Second dataset contained 254 rows and 13 columns from 6/29/2009 to 7/30/2019. I checked to make sure they had the same columns and datatypes. 
  
  <img width="596" alt="2 separate workbooks" src="https://user-images.githubusercontent.com/105246702/179857720-6e5e0704-41c2-4dca-9204-0890947f38c8.png">

  - Merging both datasets give a total of 5522 rows and 13 columns
  
 <img width="732" alt="merged" src="https://user-images.githubusercontent.com/105246702/179857973-a5de1231-3fc6-4da2-b2fc-46b5933f393b.png">

  - Missing values which were replaced with nil, I removed and replaced some wrong characters that was in the dataset using the find and replace function (Ctrl H)
  
  <img width="791" alt="find and replace" src="https://user-images.githubusercontent.com/105246702/179857919-022fac9b-98dd-4302-9f0a-f51be5e31cd2.png">

  - New Columns were created
1. ‘Crashes with or without Survivors’ I am interested in knowing the total number of crash that all abroad died, and the ones that had survivors. I used the if fxn in excel =IF([@Aboard]=[@Fatalities], "No survivor", "There are survivors") 
2. Total that had survivors =COUNTIF(J:J,"There are survivors")
3. Total crashes without survivors =COUNTIF(J:J, "No Survivor")
4. Survival column= abroad-fatalities
5. Total fatality column= fatalities + ground
6. Countries was extracted from the location column

<img width="695" alt="new column in excel" src="https://user-images.githubusercontent.com/105246702/179858512-aa5eaff7-aeec-406f-87bc-a081cf6f2ef0.png">

  - After all, done, I then saved, and it was ready to be loaded into Power bi
  
###### In Power Query

  - Hour columns was also created, this was extracted from time
  
  - Causes of crash column using the conditional column feature in power bi
  
  <img width="673" alt="new column in power query" src="https://user-images.githubusercontent.com/105246702/179858711-d9ea0c69-b0b8-4b68-b3f4-f07ad4ce7f21.png">

  - Having learnt about performance optimization in power bi 
  
  1. I removed columns that added no value to the analysis (Flight, Registration, and cn/in columns)
  
  2. Created new measures _(this was after loading into power bi)_  (Total fatality on air, Total fatality on ground, Total people on board, Total survivors, Total crash, Grand fatality (ground + air) 
   
  - I created a date table in power bi
  
  <img width="233" alt="dax measure" src="https://user-images.githubusercontent.com/105246702/179859533-70ffb4d4-37fd-4009-bd8a-f97c73f2d48b.png">

  - I checked data types and changed them to their correct type.

  - After thorough checking and validation, I closed and loaded my dataset into power bi ready for Visualization
  
 # Attributes of the Data
 It's important to understand what each attribute means.
 
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


# Model
Having created a Date Table, I had to make sure there was a relationship between it and my aircrash dataset

<img width="554" alt="model" src="https://user-images.githubusercontent.com/105246702/179613852-1db2008f-d896-47f4-95e6-7a2b1923fdd1.png">

# Data Visualization 📊
They say a picture is worth a thousand words. Once our data was tidy and neat, it was ready for visualization in power bi.

<img width="263" alt="dashboard" src="https://user-images.githubusercontent.com/105246702/181175066-98a5bdd7-6b8a-48d5-b838-c06b3c2ef339.png">

[Interact With report here](https://app.powerbi.com/view?r=eyJrIjoiZGVkNzk2YTctYmQwNC00MDYyLWJmMGYtMWJhZmU2YmMwODcxIiwidCI6IjBjZmU3YmI2LTZhMzUtNDM4OS1hODQ4LTU1ZTdjZjZlN2NmMSJ9&pageName=ReportSection04d5b904be1eb0969fdd)

# Analysis 📈
### Brief Summary

From **9/17/1908 17:18** till **7/30/2019 02:00** there was a total of **5,522crashes** with **153,840** people on board, we had **112,335** fatalities with **41,626** survivors, thus a fatality rate of **73.02%**. There were also fatalities on the ground **5,857** giving us a total of **118,077** fatalities both in the air and on ground.

Out of the crashes, **3,688** crashes had no survivors, everyone on board died while **1,834** crashes had survivors.

<img width="493" alt="brief over view" src="https://user-images.githubusercontent.com/105246702/179753425-6a6901de-0652-444f-88e8-c522d26a596b.png">

### Countries with Highest Fatalities

Russia tops the list.This can be linked to the Aeroflot airline which is a russian airline and also has the most crashes among the operators.

<img width="250" alt="fatalities by country" src="https://user-images.githubusercontent.com/105246702/179568494-0bd3cdf5-0a9e-4668-a440-b433d7800037.png">

### Yearly Trend
  - Crashes by year
  
There was a gradual increase in Plane crashes from 1908 to 1972, 1972 was highest with 104 crashes, trend shows there has been a reduction in plane crashes since then. Futher Analysis shows that improvement in flight saftey has reduced rate of crash by 91% from 1972 to 2019.

<img width="527" alt="total crashes by year" src="https://user-images.githubusercontent.com/105246702/179850362-670519d1-5916-48d1-8ce9-47f06aca4f6a.png">

  - Fatality in the air
  
Year 1972 had the highest fatality with 2,397 fatalities. There was a gradual increase from 1908 till 1972. Year 1972 was said to be the worst year in the aviation industry [💡](https://www.flightsafetyaustralia.com/2017/01/the-year-of-flying-dangerously-1972/). While report says that 1972 is the worst year, report also says that year 2017 was the safest year in history of commercial air travel

<img width="648" alt="fatalities in air by year" src="https://user-images.githubusercontent.com/105246702/179870393-831e4b6c-9fbc-44a0-924b-1e4d0d91b825.png">

Further dive into year 1972 showed that the Aeroflot airline topped the list of crashes in that year with total of 524 fatalities

<img width="590" alt="fatalities by operator year 1972" src="https://user-images.githubusercontent.com/105246702/179582348-ff1beadc-3382-478b-84cc-2a46ef95c3e9.png">

2 major peaks was also seen in the trend 1985 and 1996 with 2670 and 2386 deaths respectively. From 1996 we can see a drastic reduction in number of fatalities till 2019.
 
  - Fatality on the Ground
  
Year 2001 was the deadliest with a total death of 2891 and the incidence is linked to the event of 9/11/2001. The highest in history so far.

<img width="509" alt="fatalities on ground by year" src="https://user-images.githubusercontent.com/105246702/179850465-dca4ce13-511a-4dcd-a5f7-e266fb57e40c.png">

Note; While visualizing I noticed, there was a very high spike in 2001 showing 5,641 deaths. Research shows that only about 3,000 people were killed, exploring the data further showed that 2,750 was counted twice for ground on 9/11. Thus, I replaced one of the values with 0. 

<img width="562" alt="wrong 2001" src="https://user-images.githubusercontent.com/105246702/179862104-6e1ec42c-ce6c-4ade-9431-b17ee6ddff21.png">

_Reason why 2,570 was "repeated" twice is because both aircraft crashes occurred in the same location, World Trade Center, and so you can't really separate the fatalities on the ground that were caused specifically by each aircraft_[💡BolajiO](https://twitter.com/BolajiO_?s=20&t=5EGoUbGNFFq4VvHi1VVQPQ)

<img width="548" alt="9 11 story" src="https://user-images.githubusercontent.com/105246702/179843508-a387cee3-d483-44e3-b144-bcacd3f77703.png">

  - Grand fatality
  
Combining both ground and air fatality, to give us an insight of the total fatalities that occurred for each year. 2001 was the worst year with 4,289 deaths followed by 1972 with 2,967 deaths, then 1985 with 2,671.

<img width="637" alt="Grand fatalities by year" src="https://user-images.githubusercontent.com/105246702/179870519-20807f79-2cf3-4d2f-b055-3148bece5140.png">

  - Trend with Number of People boarding plane and Fatalities
  
  Number of people boarding flight has increased over the  years, a report by [The World Bank](https://data.worldbank.org/share/widget?end=2020&indicators=IS.AIR.PSGR&start=1970&view=chart). Thus comparing the average number of people on board to fatalities shows that fatality rate has reduced over the years. This can be linked to improvement in flight safety.
  
  <img width="649" alt="people abroad and fatalities by year" src="https://user-images.githubusercontent.com/105246702/179583051-cdba145a-f14f-49ce-b425-a913c67e5b9a.png">

### Monthly Trend
Highest number of crashes was in December with 537 crashes followed by January with 512 crashes, both months fall in the winter period. The winter period is a cold period and there are higher instances of slippery runways thus reduce brake action, reduce visibility due to snow mist and fog, and many more that might be a likely cause of the higher crashes.

<img width="611" alt="total crashes by month" src="https://user-images.githubusercontent.com/105246702/179583127-066e2992-dece-4d16-8990-7f35d0fabf61.png">

Though the weather has its own advantage by giving cool and oxygen rich air.

It should also be noted that People tend to travel more December due to festivity around that, thus with more People on board and higher crashes the fatality rate is also higher during this period.

<img width="654" alt="December trend" src="https://user-images.githubusercontent.com/105246702/179843342-411c6413-3d8b-4fb2-a714-8b3cf937242f.png">

### Operators
Aeroflot was the most boarded among the operators, it also accounted for the airline with highest fatalities rate with 7,156 fatalities. And most crashes 179 crashes. Followed by Military Us Air Force with 176 crashes and 3,717 fatalities, the next which is a commercial airline is Air France with 70 crashes and 1,734 fatalities.

<img width="374" alt="Operators" src="https://user-images.githubusercontent.com/105246702/179583345-f30ddc96-fd39-4ab6-997b-5884a14c8d08.png">

  - Short History About Aeroflot
  
![image](https://user-images.githubusercontent.com/105246702/179375851-403a5cbf-aceb-4645-a7e5-1d069fdeb563.png)

A Russian airline, founded in 1923, the flag carrier and largest airline of Russia (and formerly the Soviet Union) (formerly the world's largest airline). Making Aeroflot one of the oldest active airlines in the world. Has been in operation for about 99 years.
Research states that one of the reasons for their high crash was due to the collapse of the country’s aircraft manufacturing industry which caused the Russian airlines to rely on old aircraft they have been using for decades.

Analysis of thier crashes over time,shows it has reduced over the years. An indication of growth and improvement. Aeroflot: from world's deadliest airline to one of the safest in the sky[💡](telegraph.co.uk/travel/news/Aeroflot-from-worlds-deadliest-airline-to-one-of-the-safest-in-the-sky/)

<img width="583" alt="aeroflot crash trend over the years" src="https://user-images.githubusercontent.com/105246702/179583451-61ea4de4-1c60-498d-8c93-26f83a75452b.png">

### Type
Douglas DC3 is the most boarded, has the highest crashes and fatality rate among other types of airplane.

<img width="399" alt="fatalities by type" src="https://user-images.githubusercontent.com/105246702/179583585-5b7304c4-bff8-4663-8691-0696a19464db.png">

  - Brief history about Douglas tells us that it's a propeller-driven airliner, which had a lasting effect on the airline industry in the 1930s to 1940s and World War II. 
The DC-3 had many exceptional qualities compared to previous aircraft. It was fast, had a good range, was more reliable, and carried passengers in greater comfort. Before the war, it pioneered many air travel routes. It was able to cross the continental US from New York to Los Angeles in 18 hours, with only three stops. It is one of the first airliners that could profitably carry only passengers without relying on mail subsidies. Following the war, the airliner market was flooded with surplus transport aircraft, and the DC-3 was no longer competitive due to its size and speed.

<img width="583" alt="douglas dc 3" src="https://user-images.githubusercontent.com/105246702/179583655-5624f1b0-fea8-4773-9c11-299a46055865.png">

### Causes of Airplane Crash from Summary Column

<img width="325" alt="causes" src="https://user-images.githubusercontent.com/105246702/179611768-ea2e30f8-1ca2-4a83-b6a0-b1ade86ea823.png">

Major cause was due to weather condition, Heavy rainstorms, fog and snow can make it more difficult for airplanes to maneuver and can lead to deadly accidents. Visibility issues, high winds and skidding during takeoff and landing are the most dangerous weather-related threats to aircraft.

### Analysis on Fatalities that occured on the ground

The year 2001, month September has the highest ground death. September 11 to be precise was the worst period of ground death ever seen there was a total of 4 crashes that day 

<img width="558" alt="9 11 story" src="https://user-images.githubusercontent.com/105246702/179583870-5a4982a6-56e1-4512-8367-506894bb5ec9.png">

  - On September 11, 2001—a clear, sunny, late summer day—al Qaeda terrorists aboard hijacked passenger planes and carried out coordinated suicide attacks against the World Trade Center in New York City and the Pentagon in Washington, D.C., killing everyone on board the planes and nearly 3,000 people on the ground. A fourth plane crashed into a field near Shanksville, Pennsylvania, killing all on board, after passengers and crew attempted to wrest control from the hijackers.

![image](https://user-images.githubusercontent.com/105246702/179379591-84baa21a-03aa-4b57-82c3-f38c024033e7.png)

Till this day a memorial is held every 9th of September at The National September 11 Memorial & Museum a memorial and museum in New York City commemorating the September 11, 2001, attacks.

Majority of the death occurred in New York City, New York. Operator ‘American Airlines’ and ‘UnitedAir Lines’ were used in the attack

<img width="529" alt="more on 9 11" src="https://user-images.githubusercontent.com/105246702/179583994-c48a8f98-a319-49df-876c-50ecdc4de6fd.png">

  - This incidence is followed by Year 1996, A ground fatality that happened in Africa.

 The 1996 Air Africa crash occurred on 8 January when an overloaded Air Africa Antonov An-32B aircraft, from Moscow Airways, Kinshasa and bound for Kahemba Airport, overshot the runway at N'Dolo Airport in Kinshasa, Zaire (now the Democratic Republic of the Congo) after failing to take off and ploughed into Kinshasa's Simbazikita street market. Although four of the aircraft's six crew survived, between 225 and 348 fatalities and around 253 serious injuries occurred on the ground. This crash remains the **deadliest in African history**, and caused the most ground fatalities of any air accident in history, superseded only by the intentional crashes of American Airlines Flight 11 and United Airlines Flight 175 in the September 11 attacks.
[Read further](https://www.bing.com/search?q=1996+Air+Africa+crash&cvid=8ade70a262df4cac8faa45a340ef890e&aqs=edge..69i57j69i60l2.661j0j9&FORM=ANAB01&PC=U531)

![image](https://user-images.githubusercontent.com/105246702/179379745-89b0f2f6-486c-458a-8216-0e34cb1f168c.png)


### Analysis of Fatalities that occured in the air based on location

  - Tenerife Canarlyislands has max fatality with 761.

<img width="339" alt="fatalities in air by location" src="https://user-images.githubusercontent.com/105246702/179589495-c318d0fe-e89f-4825-af17-b4116214fb31.png">

There were 4 crashes in the area, with the highest occurring March 27,1977 out of 644 people on board there was a casualty of 583

<img width="583" alt="tenerife" src="https://user-images.githubusercontent.com/105246702/179599369-5c16e011-55b5-428b-80c2-023ad4106852.png">

The Tenerife airport disaster occurred on 27 March 1977, when two Boeing 747 passenger jets collided on the runway at Los Rodeos Airport (now Tenerife North Airport) on the Spanish island of Tenerife. The collision occurred when KLM Flight 4805 initiated its takeoff run while Pan Am Flight 1736 was still on the runway. The impact and resulting fire killed everyone on board KLM 4805 and most of the occupants of Pan Am 1736, with only 61 survivors in the front section of the aircraft. Resulting in 583 fatalities, the disaster is the deadliest accident in aviation history.
The Pan Am aircraft was named Clipper Victor. The KLM aircraft was named Rhine River.

![image](https://user-images.githubusercontent.com/105246702/179378378-2dd2217d-8756-41f9-bdcf-d3256b17172c.png)

  - Followed by Mt.Osutaka,nearUenoVillage,Japan with 520 fatalities that occurred August 12, 1985

The aircraft suffered a naft pressure bulkhead failure at 23,900ft. The aircraft had severe control difficulties with loss of all controls and eventually after 40 minutes, collided with a mountain. This was due to Improper repair of the bulkhead while being supervised by Boeing engineers after a tail strike in 1978. [Kyu Sakamoto](https://www.bing.com/ck/a?!&&p=3f5d361e743b908e2a456dc694165c81ea9e1e14567007511929e0b458459756JmltdHM9MTY1ODAxNzk3OSZpZ3VpZD00Njc3MDU4Yy1jOWFkLTRmYTItOGY0ZS00Yjc3ZmJlZTM4YzEmaW5zaWQ9NTg2NQ&ptn=3&fclid=01fc51ac-0568-11ed-8d21-03c3925136b2&u=a1aHR0cDovL2VuLndpa2lwZWRpYS5vcmcvd2lraS9LeXVfU2FrYW1vdG8&ntb=1), 43, famous for his Japanese song ['Sukiyaki'](https://www.bing.com/ck/a?!&&p=c0af3f88b42c5ae0c53915cb427167d2011281a4300713bf136a02eadc3d3fdeJmltdHM9MTY1ODAxNzk3OSZpZ3VpZD00Njc3MDU4Yy1jOWFkLTRmYTItOGY0ZS00Yjc3ZmJlZTM4YzEmaW5zaWQ9NTI2NQ&ptn=3&fclid=01fb3158-0568-11ed-b45f-ee56e6fc2f90&u=a1aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1FVFhfRUpnT1Z3OA&ntb=1) was killed in the accident. 
The aircraft, was carrying 524 people. All 15 crew members and 505 of the 509 passengers died in the accident. Some of the passengers survived the initial crash but died of their injuries hours later while awaiting rescue. Surpassing the fatalities of All Nippon Airways Flight 58, which crashed 14 years earlier with 162 fatalities, it is the **deadliest single-aircraft accident both in Japan and global aviation history**.

![image](https://user-images.githubusercontent.com/105246702/179860727-c315187d-585e-4899-b2ba-13d14025d672.png)

# Findings 🔍
  - First air crash was in 1908, there was a steady increase in number of crashes till 1972 this can be linked to airplane becoming more popular and the wars fought during those period from 1972 there has been a decrease in the crashes due to better and improved safety measures and advanced technology
  
  - Most Crashes occurred December and January which are winter periods, thus the cold weather seems to be a threat to air flights
  
  - Aeroflot a commercial airline had the highest number of crashes, followed by US Military airline, this may be as a result of their use in warfare
  
  - Douglas DC 3 has the highest number of crashes, this is linked to its widespread use during the World War 2
  
  - Countries with highest fatalities are Russia due to rough terrain and weather conditions, USA probably due to their high frequency of flights, and Colombia.

# Recommendations ✅
  - Weather is a factor for airplane crash, airlines should make use of the weather forecast in planning their flights
 
  - Airline operators should adhere to the safety rules and ensure proper maintenance of their fleets
 
  - Russia had a lot of plane crashes,probably due to rough terrain and weather conditions, they should imbibe a high level of safety measure








