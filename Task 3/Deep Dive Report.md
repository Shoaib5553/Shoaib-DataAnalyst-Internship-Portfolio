# Task 3: Interactive Dashboarding & Deep-Dive Analysis

## Project Objective

For Task 3, I wanted to take all the SQL queries and static insights from the previous phase and bring them to life. Instead of just handing over a spreadsheet, I built a two-page interactive dashboard in Power BI. The goal was to give stakeholders a tool where they can actually click around, explore the data, spot logistics bottlenecks, and see exactly where our revenue is coming from.

## 1. Data Modeling & Architecture

Before building any charts, I had to make sure all the data could "talk" to each other. I imported my 9 cleaned CSV datasets into Power BI and built a true Relational Data Model (a Star Schema).

* I used the `orders` dataset as the central fact table.

* From there, I drew relationships to connect the orders to payments, reviews, product details, and geolocation data using Primary and Foreign keys (like `order_id` and `customer_id`).

* I also tweaked the cross-filtering directions (setting them to "Both" in a few tricky spots) to make sure that filtering by a specific product accurately updated the review counts without breaking the matrix.

## 2. Core KPIs

I wanted the most critical numbers sitting right at the top of the dashboard so anyone looking at it instantly knows the health of the business.

* **Total Revenue:** R$ 13.59M

* **Total Orders:** 99.44K

* **Customer Acquisition:** 96.10K (I specifically filtered this to count unique customer IDs, removing the noise of repeat purchases).

* **Average Order Value (AOV):** R$ 154.10

* **Late Delivery Rate:** 7.87% (Tracking 7,827 total late deliveries).

## 3. Deep-Dive Findings

### Page 1: Sales & Geography

* **Geographic Concentration:** I built a Filled Map visual that made it instantly clear that Olist's revenue is heavily concentrated in the southeastern states, specifically São Paulo (SP) and Rio de Janeiro (RJ).

* **Category Dominance:** Health & Beauty, Watches & Gifts, and Bed Bath & Table consistently pull in the most money for the platform.

* **Volume Trend:** The timeline shows massive, aggressive month-over-month growth throughout 2017 before finally leveling off into a steady, high-volume plateau in early 2018.

![Page 1 Dashboard](/images/dashboard_page1.png)

### Page 2: Operations & Customer Experience

* **The Logistics Gap:** I created a custom `Delivery Status` column to compare the estimated delivery dates against the actual arrival dates. This revealed a 7.87% late delivery rate—a pretty significant operational bottleneck that directly hurts customer retention.

* **AOV Drivers:** Credit Cards aren't just the most popular way to pay; they also drive the highest Average Order Value. The ability to pay in installments clearly encourages customers to add more to their carts.

* **Quality Control:** I set up a targeted matrix to act as a quality alert. By explicitly filtering for 1-Star reviews, it isolates the top 5 worst-performing products on the platform so product managers can investigate or delist them immediately.

![Page 2 Dashboard](/images/dashboard_page2.png)

## 4. UI/UX Design Methodology

I didn't want this to look like a standard, boring corporate report. I aimed for a premium, custom-coded web app feel. To pull this off, I used a "Dark Mode" aesthetic:

* I used AI to generate glowing, neon/slate wireframe backgrounds for both pages.

* I stripped away all the native Power BI white backgrounds and borders, allowing the charts to seamlessly blend right into the custom UI panels.

* I used strategic color psychology—like formatting the 'Late Delivery' slice on the donut chart to a stark red—to immediately draw the user's eye to operational warnings.
