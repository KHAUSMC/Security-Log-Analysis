# 🔍 Security Log Analysis

## 📌 Project Overview
This project focuses on analyzing **failed login attempts** that occurred **after business hours** to detect potential **security threats**, such as unauthorized access attempts. Using SQL, I investigated login activity to identify suspicious patterns that could indicate brute-force attacks or compromised accounts.

---

## 🕵️ Retrieve After-Hours Failed Login Attempts  
As part of a **security investigation**, I analyzed login activity logs to identify **failed login attempts** that occurred **after 18:00 (6 PM)**. Since unauthorized access is more likely outside of business hours, filtering login attempts based on time helps in **early threat detection**.

---

### 🖥️ **SQL Query Used:**
SELECT * FROM log_in_attempts 
WHERE login_time > '18:00' AND success = 0; 

## 📌 **Query Explanation**
This query retrieves **failed login attempts** that occurred **after business hours (18:00 / 6:00 PM)** by using the `WHERE` clause with two conditions:

- **`login_time > '18:00'`** → Filters login attempts that happened **after 6 PM**.  
- **`AND success = 0`** → Ensures that only **failed login attempts** are included (`0` represents failure in the `success` column).  

The **`AND`** operator ensures that **both conditions must be met** for a row to be included in the results.


## 📊 Query Execution Screenshot

<img src="https://i.imgur.com/RXx4Nwd.png" alt="SQL Query Screenshot" width="800"> 

---
# 🛡️ Investigating Suspicious Login Activity

## 📌 Scenario Overview  
On **May 8, 2022**, a **suspicious event** occurred, prompting a **security investigation** into all login attempts that happened **on this day and the day after**. By analyzing login records for **May 8, 2022, and May 9, 2022**, we can identify **patterns, anomalies, and potential unauthorized access attempts**.  



## 🕵️ **SQL Query Used:**

SELECT * FROM log_in_attempts 
WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';

## 📌 Query Explanation  

This query retrieves **all login attempts** that took place on **May 8, 2022, or May 9, 2022**, using the `WHERE` clause combined with the `OR` operator:

- **`login_date = '2022-05-08'`** → Filters login attempts that occurred **on May 8, 2022** (the suspicious event date).  
- **`OR login_date = '2022-05-09'`** → Includes **logins from May 9, 2022**, to check for **related activity after the event**.  

The **`OR`** operator ensures that **either condition can be true**, so both dates are included in the results.

## 📊 Query Execution Screenshot
<img src="https://i.imgur.com/A6qSSbL.png" alt="SQL Query Screenshot" width="800"> 













