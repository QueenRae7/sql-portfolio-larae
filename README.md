# sql-portfolio-larae
Folder Structure:



sql-portfolio-larae/

│

├── 1_sales_data_analysis/

│   ├── README.md

│   └── sales_analysis.sql

│

├── 2_healthcare_patient_trends/

│   ├── README.md

│   └── patient_trends.sql

│

└── README.md



Root README.md (Overview)



# SQL Portfolio – LaRae Gilbert



This portfolio showcases my SQL capabilities through two real-world inspired projects:

1. Sales Data Analysis – Retail trends and performance metrics

2. Healthcare Patient Trends – Exploring patient behavior over time



Each folder contains a README and sample SQL queries ready for use with MySQL or PostgreSQL.



Project 1: 1_sales_data_analysis/README.md



# Sales Data Analysis



This project demonstrates SQL skills in analyzing a retail sales dataset.



**Key Queries:**

- Top-selling products by revenue

- Monthly revenue trends

- Customer lifetime value

- Region-based performance



**Tech Stack:** PostgreSQL / MySQL



-- Monthly revenue by product

SELECT product_name, DATE_TRUNC('month', sale_date) AS month, SUM(amount) AS monthly_revenue

FROM sales

GROUP BY product_name, month

ORDER BY month, monthly_revenue DESC;



-- Top 5 customers by lifetime value

SELECT customer_id, SUM(amount) AS lifetime_value

FROM sales

GROUP BY customer_id

ORDER BY lifetime_value DESC

LIMIT 5;



Project 2: 2_healthcare_patient_trends/README.md



# Healthcare Patient Trends



This project explores patient appointment trends for a fictional clinic.



**Key Queries:**

- Missed appointments by age and gender

- Average appointment wait time

- Chronic illness visit frequency



**Tech Stack:** MySQL / SQLite



patient_trends.sql



-- Missed appointments by age group

SELECT

  CASE

    WHEN age < 18 THEN 'Under 18'

    WHEN age BETWEEN 18 AND 34 THEN '18-34'

    WHEN age BETWEEN 35 AND 64 THEN '35-64'

    ELSE '65+'

  END AS age_group,

  COUNT(*) AS missed_appointments

FROM appointments

WHERE status = 'Missed'

GROUP BY age_group;



-- Average wait time (days between booking and appointment)

SELECT AVG(DATEDIFF(appointment_date, booking_date)) AS avg_wait_days

FROM appointments;

