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

# 🛡️ Investigating Suspicious Login Activity (Excluding Mexico)

## 📌 Scenario Overview  
After detecting **suspicious login activity**, I determined that these logins **did not originate from Mexico**. To further investigate, I analyzed login attempts **from all other countries**, ensuring that logins from **both "MEX" and "MEXICO"** were excluded from the dataset.  

---

## 🕵️ **SQL Query Used:**
SELECT * FROM log_in_attempts 
WHERE country NOT LIKE 'MEX%';

## 📌 Query Explanation  

This query retrieves **all login attempts that did not originate in Mexico**, using the `WHERE` clause with `NOT LIKE`:

- **`country NOT LIKE 'MEX%'`** →  
  - The **`LIKE 'MEX%'`** pattern ensures that any country value **starting with "MEX"** is matched.  
  - The **`NOT`** operator **excludes** these matched values, filtering out all logins **from Mexico ("MEX" and "MEXICO")**.  
  - The **`LIKE` wildcard `%`** ensures that **any value starting with "MEX"** (including "MEX" and "MEXICO") is excluded.
 
## 📊 Query Execution Screenshot
<img src="https://i.imgur.com/IGMX2x2.png" alt="SQL Query Screenshot" width="800">

# 🛡️ Retrieving Employees in the Marketing Department (East Building)

## 📌 Scenario Overview  
To perform **security updates** on specific employee machines in the **Marketing department**, I needed to retrieve **all employees in Marketing** who are located in **any office in the East building**. To do this, I queried the `employees` table and applied filters using **SQL's `LIKE` operator**.

---

## 🕵️ **SQL Query Used**

SELECT * FROM employees 
WHERE department = 'Marketing' AND office LIKE 'EAST%';

## 📌 Query Explanation  

This query retrieves **all employees in the Marketing department** who are located in the **East building**, using the `WHERE` clause with **`AND`** and **`LIKE`**:

- **`department = 'Marketing'`** →  
  - Ensures that only employees in **Marketing** are included.  
  - This requires an **exact match** in the `department` column.  

- **`AND office LIKE 'EAST%'`** →  
  - Filters for **employees in the East building**, where office values **start with "EAST"**.  
  - The **wildcard `%`** ensures that offices like **"EAST-170", "EAST-320"** are included.  

The **`AND`** operator ensures that **both conditions must be met**, meaning only employees who **work in Marketing and are in the East building** are returned.

📊 Query Execution Screenshot
<img src="https://i.imgur.com/lKPvxyi.png" alt="SQL Query Screenshot" width="800">

# 🛡️ Retrieving Employees in the Sales and Finance Departments  

## 📌 Scenario Overview  
To perform **security updates** on specific employee machines in the **Sales and Finance departments**, I needed to retrieve **all employees** from these two departments. To achieve this, I queried the `employees` table and applied filters using **SQL's `OR` operator**.

---

## 🕵️ **SQL Query Used:**

SELECT * FROM employees 
WHERE department = 'Sales' OR department = 'Finance';

## 📌 Query Explanation  

This query retrieves **all employees who belong to either the Sales or Finance departments**, using the `WHERE` clause with `OR`:

- **`department = 'Sales'`** →  
  - Ensures that employees from **Sales** are included in the result.  
  - This requires an **exact match** in the `department` column.  

- **`OR department = 'Finance'`** →  
  - Includes employees from **Finance** as well.  
  - The **`OR` operator** allows **either condition to be true**, so employees from **both departments** are included.  

The **`OR` operator** ensures that **employees from either Sales or Finance are retrieved**, allowing for a **targeted security update on their machines**.



















