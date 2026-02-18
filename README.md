# 🚖 OLA Data Analyst Project

## 📌 Project Overview
This project is an end-to-end Data Analytics case study built using a simulated OLA ride dataset (100,000 rows, Bengaluru). The analysis focuses on ride booking behavior, cancellations, revenue trends, ride distance patterns, and customer/driver ratings.

The project demonstrates practical data analyst skills using **SQL for data analysis** and **Power BI for visualization & insights**.

---

## 🎯 Project Objectives

- Analyze ride booking patterns and demand trends  
- Evaluate booking success rates and ride completion metrics  
- Examine customer and driver cancellation behavior  
- Assess operational efficiency (VTAT & CTAT)  
- Study booking value distribution and revenue performance  
- Compare ride distances across vehicle types  
- Evaluate customer & driver satisfaction using ratings  
- Identify high-value customers  
- Derive business insights from data  

---

## 📊 Dataset Information

**Dataset Type:** Synthetic / Simulated  
**City:** Bengaluru  
**Records:** 100,000 rows  
**Duration:** 1 Month  

### **Dataset Columns**

- Date  
- Time  
- Booking_ID  
- Booking_Status  
- Customer_ID  
- Vehicle_Type  
- Pickup_Location  
- Drop_Location  
- V_TAT (Vehicle Turn Around Time)  
- C_TAT (Customer Turn Around Time)  
- Cancelled_Rides_by_Customer  
- Cancelled_Rides_by_Driver  
- Incomplete_Rides  
- Incomplete_Rides_Reason  
- Booking_Value  
- Payment_Method  
- Ride_Distance  
- Driver_Ratings  
- Customer_Rating  

---

## 🛠 Tools & Technologies Used

- **SQL** → Data Analysis & Business Queries  
- **Power BI** → Data Visualization & Dashboard  
- **Excel / CSV** → Dataset Handling  

---

## 🧮 SQL Analysis

Key business questions solved using SQL:

1. Retrieve all successful bookings  
2. Find average ride distance per vehicle type  
3. Calculate total customer cancellations  
4. Identify top 5 customers by ride volume  
5. Analyze driver cancellation reasons  
6. Evaluate driver ratings (max/min)  
7. Filter rides by payment method  
8. Calculate average customer ratings  
9. Compute total successful booking value  
10. Analyze incomplete rides & reasons  

---
## SQL Queries

```sql
DROP TABLE IF EXISTS bookings
create table bookings(
Date Date,
Time Time,	
Booking_ID	varchar(50),
Booking_Status varchar(50),
Customer_ID	varchar(50),
Vehicle_Type varchar(50),	
Pickup_Location varchar(50),
Drop_Location	varchar(50),
Avg_VTAT	numeric,
Avg_CTAT	numeric,
Cancelled_Rides_by_Customer numeric,
Reason_for_cancelling_by_Customer	varchar(50),
Cancelled_Rides_by_Driver	varchar(50),
Incomplete_Rides	numeric,
Incomplete_Rides_Reason	varchar(50),
Booking_Value	numeric,
Ride_Distance	numeric,
Driver_Ratings numeric,	
Customer_Rating numeric
)


select * from bookings 


-- 1. Retrieve all successful bookings:

create view successful_bookings AS
select * from bookings 
where booking_status = 'Successful'

select * from successful_bookings


-- 2. Find the average ride distance for each vehicle type:

create view avg_ride_distance as
select vehicle_type, Round(avg(ride_distance), 2) from bookings 
group by 1
order by 1

select * from avg_ride_distance



-- 3. Get the total number of cancelled rides by customers:

create view cancelled_rides_by_customers as
select count(*) from bookings where booking_status = 'Cancelled by Customer'

select * from cancelled_rides_by_customers



-- 4. List the top 5 customers who booked the highest number of rides:

create view TOP_5_customers as
select customer_id, count(booking_id) from bookings 
group by 1
order by 2 desc limit 5

select * from TOP_5_customers



-- 5. Get the number of rides cancelled by drivers due to personal and car-related issues:

create view rides_cancelled_by_drivers as
select count(*) from bookings where Cancelled_Rides_by_Driver = 'Personal & Car related issues'

select * from rides_cancelled_by_drivers


-- 6. Find the maximum and minimum driver ratings for Prime Sedan bookings:

create view maximum_and_minimum_driver_ratings as
select max(driver_ratings) as max_rating,
min(driver_ratings) as min_rating from bookings
where vehicle_type = 'Prime Sedan'

select * from maximum_and_minimum_driver_ratings



 -- 7. Find the average customer rating per vehicle type:

create view average_customer_rating_per_vehicle_type as
select vehicle_type, Round(avg(customer_rating), 2) from bookings
group by 1
order by 1

select * from average_customer_rating_per_vehicle_type



--8. Calculate the total booking value of rides completed successfully:

create view total_booking_value as
select sum(booking_value) from bookings 
where booking_status = 'Successful'

select * from total_booking_value



--9. List all incomplete rides along with the reason:

create view incomplete_rides_reason as
select booking_id, Incomplete_Rides_Reason from bookings
where Incomplete_Rides = 1

select * from incomplete_rides_reason

-- End Of Project
```



## 📈 Power BI Dashboard

The dashboard provides insights into:

- Ride Volume Over Time  
- Booking Status Breakdown  
- Revenue Analysis  
- Cancellation Trends  
- Ride Distance Distribution  
- Ratings Distribution  
- Customer Performance  

Example: ![Dashboard Preview](https://github.com/impulkit48/Ola-data-analytics-project/blob/main/Snapshot%20of%20Dashboard.png)
---

## 💡 Key Insights (Example Section)

- Majority of bookings are successful (~62%)  
- Driver cancellations exceed customer cancellations  
- Booking values are higher on weekends  
- Ride distance varies significantly by vehicle type  
- Ratings indicate overall service satisfaction trends  

---

## 📂 Project Structure


---

## 🚀 How to Use

1. Import dataset into SQL database  
2. Run SQL queries for analysis  
3. Load dataset into Power BI  
4. Explore dashboard & insights  

---

## ✅ Skills Demonstrated

✔ Data Cleaning  
✔ Data Analysis  
✔ SQL Querying
✔ Power BI
✔ Advanced Excel
✔ KPI Evaluation  
✔ Data Visualization  
✔ Business Insight Generation  

---

## Author - Pulkit Sharma

This project is part of my portfolio, showcasing my SQL, Power BI and Excel skills essential for data analyst roles. If you have any questions, feedback, or would like to collaborate, feel free to get in touch!

### Stay Updated 

For more content on SQL, data analysis, and other data-related topics, make sure to follow me on social media:

- **Instagram**: [Follow me for daily tips and updates](https://www.instagram.com/pulkitsharma48/)
- **LinkedIn**: [Connect with me professionally](https://www.linkedin.com/in/pulkitsharma48/)
- **Twitter/X**: [Join our community to learn and grow together](https://x.com/impulkit_48)

Thank you for your support, and I look forward to connecting with you!

---

## ⭐ If you found this project useful, consider giving it a star!

