# 📊 E-Commerce Sales & Profitability Analytics

## 🏢 Business Context & Problem Statement
In the fast-paced e-commerce sector, understanding product performance, geographic reach, and discount impacts is critical for profitability. The client needed to transition from static, cluttered reporting to a dynamic, data-driven analytical tool. 

The core challenge was to build an engine that not only tracks overall KPIs but empowers business users to perform complex, independent period-over-period (PoP) comparisons on the fly without breaking the underlying filter context.

### 📋 Official Client Requirements
<img width="1008" height="566" alt="image" src="https://github.com/user-attachments/assets/664832f1-994d-4446-b2dd-45fb4c3ed085" />

To meet the business needs, the dashboard had to strictly answer the following:
* Identify Top & Bottom 5 products based on Sales, Profit, and Quantity.
* Analyze granular sales trends (daily, monthly, quarterly, annually).
* Visualize the direct correlation between Net Sales and Profit.
* **Complex Requirement:** Compare sales, profit, and quantity between *any two independent custom date ranges* selected by the user.
* Map geographical sales distribution across different cities.
* Calculate average discounts per promotion category.

---

## 🧠 The Solution & Technical Architecture
To deliver a highly scalable solution, I treated this as a complete data engineering and modeling pipeline, rather than just a visualization task.

### 1. Robust Data Modeling (Star Schema)
Optimized data relationships are the backbone of any enterprise Power BI report. I structured the raw data into a clean **Star Schema** to maximize DAX query performance.
* **Fact Table:** Centralized quantitative data (Net Sales, Profit, Discount Value).
* **Dimension Tables:** `Dim Product`, `Dim Promotion`, `Dim Customers`.
* **Role-Playing Dimensions:** Created dual Master Date Tables (`DateTable1` and `DateTable2`) to support independent temporal filtering for comparative analytics.

<img width="1384" height="650" alt="Screenshot 2026-05-27 213407" src="https://github.com/user-attachments/assets/4b75db86-19bb-480c-9284-9d1b20ada15b" />


### 2. Advanced DAX & The Comparative Engine
Solving the client's dynamic period comparison requirement was the technical highlight of this project. I developed and tested two distinct methodologies to achieve this:

* **Method 1 (The Developer/DAX Approach):** Leveraged inactive relationships in the data model and used the `USERELATIONSHIP` DAX function. Combined with `CALCULATE` and `ALL`, this allowed me to override the default filter context, enabling two separate date slicers to independently filter the metrics.
* **Method 2 (The UI/Frontend Approach):** Mastered Power BI's `Edit Interactions` feature to precisely control visual cross-filtering behaviors, isolating filter contexts purely through the frontend without heavy computational DAX.

---

## 📸 Dashboard Walkthrough

### 📌 Main Executive View (Sales, Mapping & Trends)
<img width="1222" height="676" alt="Screenshot 2026-05-27 213009" src="https://github.com/user-attachments/assets/e84f4a22-8c1e-45a0-8189-07910cbc3865" />


### 📌 The Comparative Analytics Engine
<img width="1205" height="805" alt="Screenshot 2026-05-27 213027" src="https://github.com/user-attachments/assets/cf614f30-7330-4ad2-8525-6c97ccf21990" />
<img width="1325" height="794" alt="Screenshot 2026-05-27 213042" src="https://github.com/user-attachments/assets/17bb7da9-9acb-4616-8740-afa24109b9b6" />


### 📌 Product Performance & Profitability (Top/Bottom N)
<img width="1213" height="675" alt="Screenshot 2026-05-27 212953" src="https://github.com/user-attachments/assets/3a14d6c3-4e60-43e5-a410-81b5b38aad45" />
### 📌 Filtering all parameters using visual filters (made dynamic using a Meausre in the Filter Section)
<img width="1231" height="687" alt="Screenshot 2026-05-27 213057" src="https://github.com/user-attachments/assets/9c63e90e-ca87-4247-ab20-2828b4ba0533" />

---
*Built with 💡 focusing on DAX optimization, dimensional modeling, and actionable business intelligence.*
