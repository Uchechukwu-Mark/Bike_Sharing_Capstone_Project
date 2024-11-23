# Bike_Sharing_Capstone_Project
This project delves into how different bike users being the annual members and casual users use bike and how casual users can be converted to annual member users.


"Google Data Analytics Capstone project"

Case Study 1(R Programming Language)

How Does a Bike-Share Navigate Speedy Success?

Introduction

This capstone project shades light on Cyclist, a bike sharing company in chicago. This company has two set of people who uses their bikes: annual members and casual riders. Annual member subscribe to package while casual riders use and make payment on use bases. . Cyclistic's finance analysts have concluded that annual members are much more profitable than casual riders. The director of marketing believes the company's future success depends on maximizing the number of annual memberships. Rather than creating a marketing campaign that targets all-new customers, the marketing director believes there is a very good chance to convert casual riders into members.

Business Task

How do annual members and casual riders use bikes differently and how do we convert casual riders to annual members/design a new marketing strategy to convert casual riders into annual members.

Ask

How do annual members and casual riders use Cyclistic bikes differently?
Why would casual riders buy Cyclistic annual memberships?
How can Cyclistic use digital media to influence casual riders to become members?
Prepare

This is a large dataset comprising of millions of rows when merged thus it will time consuming to run in SQL and nearly impossible to be analysed in excel. Thererfore the best tool for this analysis is R Programming Language.

installing and loading the necessary packages

library(tidyverse)  
library(lubridate)  
library(ggplot2)
library(readr)
library(dplyr)
library(skimr)
library(janitor)
library(hms)
library(scales)
library(tidyr)
library(tibble)
── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
✔ ggplot2 3.4.0      ✔ purrr   1.0.1 
✔ tibble  3.1.8      ✔ dplyr   1.0.10
✔ tidyr   1.2.1      ✔ stringr 1.5.0 
✔ readr   2.1.3      ✔ forcats 0.5.2 
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
Loading required package: timechange


Attaching package: ‘lubridate’


The following objects are masked from ‘package:base’:

    date, intersect, setdiff, union



Attaching package: ‘janitor’


The following objects are masked from ‘package:stats’:

    chisq.test, fisher.test



Attaching package: ‘hms’


The following object is masked from ‘package:lubridate’:

    hms



Attaching package: ‘scales’


The following object is masked from ‘package:purrr’:

    discard


The following object is masked from ‘package:readr’:

    col_factor


m1<-read_csv("/kaggle/input/divvy-monthly-data-2022/202201-divvy-tripdata/202201-divvy-tripdata.csv")
m2<-read_csv("/kaggle/input/divvy-monthly-data-2022/202202-divvy-tripdata/202202-divvy-tripdata.csv")
m3<-read_csv("/kaggle/input/divvy-monthly-data-2022/202203-divvy-tripdata/202203-divvy-tripdata.csv")
m4<-read_csv("/kaggle/input/divvy-monthly-data-2022/202204-divvy-tripdata/202204-divvy-tripdata.csv")
m5<-read_csv("/kaggle/input/divvy-monthly-data-2022/202205-divvy-tripdata/202205-divvy-tripdata.csv")
m6<-read_csv("/kaggle/input/divvy-monthly-data-2022/202206-divvy-tripdata/202206-divvy-tripdata.csv")
m7<-read_csv("/kaggle/input/divvy-monthly-data-2022/202207-divvy-tripdata/202207-divvy-tripdata.csv")
m8<-read_csv("/kaggle/input/divvy-monthly-data-2022/202208-divvy-tripdata/202208-divvy-tripdata.csv")
m9<-read_csv("/kaggle/input/divvy-monthly-data-2022/202209-divvy-tripdata/202209-divvy-publictripdata.csv")
m10<-read_csv("/kaggle/input/divvy-monthly-data-2022/202210-divvy-tripdata/202210-divvy-tripdata.csv")
m11<-read_csv("/kaggle/input/divvy-monthly-data-2022/202211-divvy-tripdata/202211-divvy-tripdata.csv")
m12<-read_csv("/kaggle/input/divvy-monthly-data-2022/202212-divvy-tripdata/202212-divvy-tripdata.csv")
Rows: 103770 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 115609 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 284042 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 371249 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 634858 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 769204 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 823488 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 785932 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 701339 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 558685 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 337735 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 181806 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
dbl  (4): start_lat, start_lng, end_lat, end_lng
dttm (2): started_at, ended_at

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
# check the data set columns to make sure they are similar
colnames(m1)
colnames(m2)
colnames(m3)
colnames(m4)
colnames(m5)
colnames(m6)
colnames(m7)
colnames(m8)
colnames(m9)
colnames(m10)
colnames(m11)
colnames(m12)
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
'ride_id''rideable_type''started_at''ended_at''start_station_name''start_station_id''end_station_name''end_station_id''start_lat''start_lng''end_lat''end_lng''member_casual'
# bind data set together (#d.f = all_trip)
all_trip <- bind_rows(m1,m2,m3,m4,m5,m6,m7,m8,m9,m10,m11,m12)

# remove unwanted data frames to free memory
rm(m1,m2,m3,m4,m5,m6,m7,m8,m9,m10,m11,m12)
the whole dataset has been merged

Process

# selecting the relevant column for analysis
all_trip <- all_trip %>%  select("rideable_type", "started_at", "ended_at", "start_station_name", "start_station_id", "end_station_name", "end_station_id","member_casual")


# extracting unique data only and dropping n/a(removing duplicate = all_trip2)
all_trip2 <- unique(all_trip)
all_trip2<- drop_na(all_trip2)
# checking for any duplicate
anyDuplicated(all_trip2)
0
the column names needs to be formatted for easy readability

all_trip2<- all_trip2 %>% rename( bike_type = "rideable_type",
                                  start_time ="started_at",
                                  end_time ="ended_at",
                                  start_station ="start_station_name",
                                  end_station ="end_station_name",
                                  user_type = "member_casual")
More formatting that will help in the analysis needs to be done, these formatting include ride_length(how long a user used the bike in secs and in days), day_of_week (day the ride started), month (month the ride started) and trip (combination of start and end station)

all_trip3 <- all_trip2 %>% 
  mutate(ride_length = difftime(end_time ,start_time)) %>% 
  mutate(day_of_week = weekdays(start_time, abbreviate=FALSE)) %>% 
  mutate(days = round(difftime( end_time,start_time, unit="days"))) %>% 
  mutate(month = format(as.Date(all_trip2$start_time),'%b_%y'))%>% 
  unite(trip, start_station, end_station, remove=FALSE, sep= " - ")

#Lets have a last look at our data set
  glimpse(all_trip3)
Rows: 4,369,334
Columns: 13
$ bike_type        <chr> "electric_bike", "electric_bike", "classic_bike", "cl…
$ start_time       <dttm> 2022-01-13 11:59:47, 2022-01-10 08:41:56, 2022-01-25…
$ end_time         <dttm> 2022-01-13 12:02:44, 2022-01-10 08:46:17, 2022-01-25…
$ trip             <chr> "Glenwood Ave & Touhy Ave - Clark St & Touhy Ave", "G…
$ start_station    <chr> "Glenwood Ave & Touhy Ave", "Glenwood Ave & Touhy Ave…
$ start_station_id <chr> "525", "525", "TA1306000016", "KA1504000151", "TA1309…
$ end_station      <chr> "Clark St & Touhy Ave", "Clark St & Touhy Ave", "Gree…
$ end_station_id   <chr> "RP-007", "RP-007", "TA1307000001", "TA1309000021", "…
$ user_type        <chr> "casual", "casual", "member", "casual", "member", "me…
$ ride_length      <drtn> 177 secs, 261 secs, 261 secs, 896 secs, 362 secs, 20…
$ day_of_week      <chr> "Thursday", "Monday", "Tuesday", "Tuesday", "Thursday…
$ days             <drtn> 0 days, 0 days, 0 days, 0 days, 0 days, 0 days, 0 da…
$ month            <chr> "Jan_22", "Jan_22", "Jan_22", "Jan_22", "Jan_22", "Ja…
Analysis

To find the maximum, mean and minimum ride_length

max(all_trip3$ride_length)
min(all_trip3$ride_length)
mean(all_trip3$ride_length)
Time difference of 2061244 secs
Time difference of -10122 secs
Time difference of 1025.709 secs
There is a negative time difference as the minimum ride_length which is wrong. It needs to be done removed as time cannot be negative for a trip.Also there are ride_length of 0 secs. assuming that trips are charged per minute, trip less than 60secs shouldn't be taken inot account. Therefore a new d.f needs to be created with only ride_length of 60secs and above

all_trip4 <- all_trip3 %>%
  filter(ride_length >59) %>% 
  glimpse()
Rows: 4,292,684
Columns: 13
$ bike_type        <chr> "electric_bike", "electric_bike", "classic_bike", "cl…
$ start_time       <dttm> 2022-01-13 11:59:47, 2022-01-10 08:41:56, 2022-01-25…
$ end_time         <dttm> 2022-01-13 12:02:44, 2022-01-10 08:46:17, 2022-01-25…
$ trip             <chr> "Glenwood Ave & Touhy Ave - Clark St & Touhy Ave", "G…
$ start_station    <chr> "Glenwood Ave & Touhy Ave", "Glenwood Ave & Touhy Ave…
$ start_station_id <chr> "525", "525", "TA1306000016", "KA1504000151", "TA1309…
$ end_station      <chr> "Clark St & Touhy Ave", "Clark St & Touhy Ave", "Gree…
$ end_station_id   <chr> "RP-007", "RP-007", "TA1307000001", "TA1309000021", "…
$ user_type        <chr> "casual", "casual", "member", "casual", "member", "me…
$ ride_length      <drtn> 177 secs, 261 secs, 261 secs, 896 secs, 362 secs, 20…
$ day_of_week      <chr> "Thursday", "Monday", "Tuesday", "Tuesday", "Thursday…
$ days             <drtn> 0 days, 0 days, 0 days, 0 days, 0 days, 0 days, 0 da…
$ month            <chr> "Jan_22", "Jan_22", "Jan_22", "Jan_22", "Jan_22", "Ja…
ordering and checking for day and month with most bike hire

all_trip4$day_of_week<- ordered(all_trip4$day_of_week,levels =c("Monday", "Tuesday", "Wednesday","Thursday","Friday","Saturday","Sunday"))
all_trip4$month <- ordered(all_trip4$month, levels =c("Jan_22","Feb_22", "Mar_22","Apr_22", "May_22", "Jun_22", "Jul_22","Aug_22", "Sep_22", "Oct_22", "Nov_22","Dec_22"))
levels(all_trip4$day_of_week)
levels(all_trip4$month)
'Monday''Tuesday''Wednesday''Thursday''Friday''Saturday''Sunday'
'Jan_22''Feb_22''Mar_22''Apr_22''May_22''Jun_22''Jul_22''Aug_22''Sep_22''Oct_22''Nov_22''Dec_22'
#Plotting for hire frequency
ggplot(data=all_trip4, mapping =aes(x= month))+
  geom_bar(fill= "red") + theme(axis.text.x=element_text(angle=45)) + 
  labs(x="Months", y="Frequency of bike hire", title="Frequency of bike hire for each month of the year")+
  scale_y_continuous(labels = function (x) format(x,scientific= FALSE))

there is a steady visible increase from the month of March, the peak being the month of July and then a steady decline.

Plotting for hire frequency based on user_type

ggplot(data=all_trip4, mapping =aes(x= month))+
  geom_bar(fill= "red") + facet_wrap(~user_type) + theme(axis.text.x=element_text(angle=45)) + 
  labs(x="Months", y="Amount of bike hire", title="Amount of bike hire for each month of the year based on user_type")+
  scale_y_continuous(labels = function (x) format(x,scientific= FALSE))

There is a similar pattern in the manner at which both casuals and member hire bikes. Though on the months of June, July and August members maintained a certain threshold while casual maxed out on the month of july and staterd declining immediatly

#Plotting for hire frequency for each day
ggplot(data=all_trip4, mapping = aes(x = day_of_week))+
  geom_bar(fill="skyblue")+ theme(axis.text.x = element_text(angle = 45))+
  labs(x="days", y = "Number_of_bikes", title = "Bike_hired_per_day")+ 
  scale_y_continuous(labels = function(x) format(x, scientific = FALSE))

On general, the day with the highest hire amount is Saturday being a weekend

ggplot(data=all_trip4, mapping = aes(x = day_of_week))+
  geom_bar(fill="skyblue")+ facet_wrap(~user_type) + theme(axis.text.x = element_text(angle = 45))+
  labs(x="days", y = "Number_of_bikes", title = "Bike_hired_per_day")+ 
  scale_y_continuous(labels = function(x) format(x, scientific = FALSE))

Looking at this hire frequency, it is clear that members use bikes more on week days, probably for a work purpose, while casual use bikes mainly on saturday, which is probably for exercise.

We need to find out the most used stations (start and end station) to enable know where we will concentrate for our adverts

all_trip4 %>% group_by(start_station) %>% summarise(popular_station = n()) %>% arrange(desc(popular_station)) %>%head()
all_trip4 %>% group_by(end_station) %>% summarise(popular_station = n()) %>% arrange(desc(popular_station)) %>%head()
all_trip4 %>% group_by(trip) %>% summarise(popular_trip = n()) %>% arrange(desc(popular_trip)) %>%head()
A tibble: 6 × 2
start_station	popular_station
<chr>	<int>
Streeter Dr & Grand Ave           	69926
DuSable Lake Shore Dr & Monroe St	38581
DuSable Lake Shore Dr & North Blvd	37081
Michigan Ave & Oak St             	36589
Wells St & Concord Ln             	34015
Millennium Park	32278
A tibble: 6 × 2
end_station	popular_station
<chr>	<int>
Streeter Dr & Grand Ave           	71201
DuSable Lake Shore Dr & North Blvd	39947
DuSable Lake Shore Dr & Monroe St	37830
Michigan Ave & Oak St             	37660
Wells St & Concord Ln             	34196
Millennium Park	33137
A tibble: 6 × 2
trip	popular_trip
<chr>	<int>
Streeter Dr & Grand Ave - Streeter Dr & Grand Ave                    	10863
Ellis Ave & 60th St - University Ave & 57th St                       	6797
DuSable Lake Shore Dr & Monroe St - DuSable Lake Shore Dr & Monroe St	6705
University Ave & 57th St - Ellis Ave & 60th St                       	6362
Ellis Ave & 60th St - Ellis Ave & 55th St                            	6359
Ellis Ave & 55th St - Ellis Ave & 60th St                            	5716
The most popular start station, end station and trip made is in Streeter Dr & Grand Ave.

Since the focus is on converting casuals to members, finding out the most stations used by casual

all_trip4 %>% filter(user_type == "casual") %>% group_by(start_station) %>% summarise(popular_station = n()) %>% arrange(desc(popular_station))%>%head()
all_trip4 %>% filter(user_type == "casual") %>% group_by(end_station) %>% summarise(popular_station= n()) %>% arrange(desc(popular_station))%>%head()
all_trip4 %>% filter(user_type == "casual") %>% group_by(trip) %>% summarise(popular_trip = n()) %>% arrange(desc(popular_trip))%>%head()
A tibble: 6 × 2
start_station	popular_station
<chr>	<int>
Streeter Dr & Grand Ave           	54138
DuSable Lake Shore Dr & Monroe St	29781
Millennium Park	23570
Michigan Ave & Oak St             	23409
DuSable Lake Shore Dr & North Blvd	21829
Shedd Aquarium	19121
A tibble: 6 × 2
end_station	popular_station
<chr>	<int>
Streeter Dr & Grand Ave           	56890
DuSable Lake Shore Dr & Monroe St	28062
Millennium Park	25297
Michigan Ave & Oak St             	25021
DuSable Lake Shore Dr & North Blvd	24978
Theater on the Lake	18448
A tibble: 6 × 2
trip	popular_trip
<chr>	<int>
Streeter Dr & Grand Ave - Streeter Dr & Grand Ave                    	9712
DuSable Lake Shore Dr & Monroe St - DuSable Lake Shore Dr & Monroe St	6134
DuSable Lake Shore Dr & Monroe St - Streeter Dr & Grand Ave          	5100
Michigan Ave & Oak St - Michigan Ave & Oak St                        	4260
Millennium Park - Millennium Park	3682
Streeter Dr & Grand Ave - DuSable Lake Shore Dr & Monroe St          	2854
The most popular start and end station for casual users is Streeter Dr & Grand Ave

The top most popular trip between stations for casual users are

Streeter Dr & Grand Ave - Streeter Dr & Grand Ave 9712

DuSable Lake Shore Dr & Monroe St - DuSable Lake Shore Dr & Monroe St 6134

DuSable Lake Shore Dr & Monroe St - Streeter Dr & Grand Ave 5100

When advertising the target should be on these routes since this is where the the most trip occure.

Checking the most popular start_station and end_station

all_trip4 %>% filter(user_type == "member") %>% group_by(start_station) %>% summarise(popular_station = n()) %>% arrange(desc(popular_station))%>%head()
all_trip4 %>% filter(user_type == "member") %>% group_by(end_station) %>% summarise(popular_station = n()) %>% arrange(desc(popular_station))%>%head()
all_trip4 %>% filter(user_type == "member") %>% group_by(trip) %>% summarise(popular_trip = n()) %>% arrange(desc(popular_trip))%>%head()
A tibble: 6 × 2
start_station	popular_station
<chr>	<int>
Kingsbury St & Kinzie St    	23134
Clark St & Elm St           	20193
Wells St & Concord Ln       	19364
Clinton St & Washington Blvd	18399
Loomis St & Lexington St    	17826
Clinton St & Madison St     	17576
A tibble: 6 × 2
end_station	popular_station
<chr>	<int>
Kingsbury St & Kinzie St    	22822
Clark St & Elm St           	20539
Wells St & Concord Ln       	19962
Clinton St & Washington Blvd	19106
Clinton St & Madison St     	18103
University Ave & 57th St    	18094
A tibble: 6 × 2
trip	popular_trip
<chr>	<int>
Ellis Ave & 60th St - University Ave & 57th St	5848
University Ave & 57th St - Ellis Ave & 60th St	5544
Ellis Ave & 60th St - Ellis Ave & 55th St     	5278
Ellis Ave & 55th St - Ellis Ave & 60th St     	4745
State St & 33rd St - Calumet Ave & 33rd St    	3268
Calumet Ave & 33rd St - State St & 33rd St    	3215
Looking at the most trip for members we find out that the first 6 is a replica of each other with less than 5% difference, this simply implies and validate the claim that members use bike for a certain purpose daily which is likely work.

how long in days are bikes kept

all_trip4 %>% group_by(days) %>% summarise(number_of_day= n())   
all_trip4 %>% filter(user_type=="member") %>% group_by(days) %>% summarise(number_of_day= n()) 
all_trip4 %>% filter(user_type=="casual") %>% group_by(days) %>% summarise(number_of_day= n())
A tibble: 14 × 2
days	number_of_day
<drtn>	<int>
0 days	4290725
1 days	1907
2 days	20
3 days	11
4 days	3
5 days	3
6 days	3
7 days	4
8 days	2
10 days	2
19 days	1
20 days	1
22 days	1
24 days	1
A tibble: 2 × 2
days	number_of_day
<drtn>	<int>
0 days	2561028
1 days	445
A tibble: 14 × 2
days	number_of_day
<drtn>	<int>
0 days	1729697
1 days	1462
2 days	20
3 days	11
4 days	3
5 days	3
6 days	3
7 days	4
8 days	2
10 days	2
19 days	1
20 days	1
22 days	1
24 days	1
for all bike users 99.9% return the bikes the same day

for members more that 99% return the bike the same day and no member keeps bike more than 1 day from hiring time

for casual users more than 99% return the bike the same day, with few keeping it for more than 1 day.

calculating the average ride_length

#average ride_length
average_ride_length_general<- all_trip4 %>% group_by(user_type) %>% 
  summarise(average_ride_length = mean(ride_length)) %>% glimpse()

average_ride_length_per_day <- all_trip4 %>% group_by(day_of_week, user_type) %>% 
  summarise(average_ride_length = mean(ride_length)) %>% view()

#Plotting for average ride length for each day of the week
ggplot(data = average_ride_length_per_day, mapping = aes(x=day_of_week, y=average_ride_length, fill=user_type))+
  geom_bar(stat='identity', position = 'dodge')+
  theme(axis.text.x = element_text(angle = 45))+
  labs(x="days_of_week", y="Average_ride_length(secs)", title="Average_Ride_Length")+
  scale_y_continuous()
Rows: 2
Columns: 2
$ user_type           <chr> "casual", "member"
$ average_ride_length <drtn> 1461.5657 secs, 761.1096 secs
`summarise()` has grouped output by 'day_of_week'. You can override using the
`.groups` argument.

members use bike for about 750 secs on average daily

Maximum ride_lengths

#max ride
Max_ride_per_day<- all_trip4 %>% group_by(user_type) %>% summarise(max_ride = max(ride_length)) %>% view()
#max ride
Max_ride_per_day<- all_trip4 %>% group_by(day_of_week, user_type) %>% summarise(max_ride = max(ride_length)) %>% view()


#Plotting for max ride length for each day of the week
ggplot(data = Max_ride_per_day, mapping = aes(x=day_of_week, y=max_ride, fill=user_type))+
  geom_bar(stat='identity', position = 'dodge')+
  theme(axis.text.x = element_text(angle = 45))+
  labs(x="days_of_week", y="Max_ride_length(secs)", title="Maximum_Ride_Length_per_day")+
  scale_y_continuous(labels= function(x) format(x,scientific=FALSE))
`summarise()` has grouped output by 'day_of_week'. You can override using the
`.groups` argument.

the maximum ride is on Saturday.

Most used bike_type

#Popular bikes - Member
bike_type_mem <- all_trip4 %>%
  filter(user_type=="member") %>%
  group_by(bike_type) %>%
  summarise(mem_num_bike=n())

  tibble(bike_type_mem)

#Popular bikes - casual
bike_type_casual <- all_trip4 %>%
  filter(user_type=="casual") %>%
  group_by(bike_type) %>%
  summarise(cas_num_bike=n())

  tibble(bike_type_casual)
A tibble: 2 × 2
bike_type	mem_num_bike
<chr>	<int>
classic_bike	1682890
electric_bike	878583
A tibble: 3 × 2
bike_type	cas_num_bike
<chr>	<int>
classic_bike	875996
docked_bike	173340
electric_bike	681875
Summary of Analysis

Days bike were borrowed

The majority of users (both user type) borrow bikes and return them the same day (within 24 hours).

Popular stations

Casual riders and member riders have different popular stations

Days of the week vs bike hire

There is a peak of bike hire by casual riders on weekends especially on Saturdays. Members use bikes mostly during the week.

Trip duration

casual riders trip is more than 2 times longer on average than trip duration for members. Casual riders use bikes for longer duration throughout the weekend.

Popular bike hire months

Most bikes are hired between June and August by both user types. During these months (Jun to August), members frequency of hiring is almost constant whereas for casual riders, the frequency of bike hire rises and reaches maximum in July. Bike hiring is low in the beginning of the year.

Popular bike types

Members use two types of bikes: Classic bikes and Electric bikes. Most members prefer classic bikes. Casual members uses all three types of bikes. Most of the casual riders use Classic bikes and electric bikes

Top Three Recommendations

Advertise on the weekends of the month of may, june, july and august at stations that are mostly used by casual riders.
These stations are A. Streeter Dr & Grand Ave B. DuSable Lake Shore Dr & Monroe St C. Millennium Park

Give discounts to members on weekend rides to attract casual users since use bikes mostly on weekends

Give loyalty points to members for bike usage of more than 25 hours since casual users use bikes for duration roughly 2 times more than members

Challenge with data

There is no gender nor age on the data set. This impacts the type of advertisement that would be created to attract uses.
