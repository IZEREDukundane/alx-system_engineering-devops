Postmorten task on an API Timeout


📅Issue Summary
Duration: February 26, 2025, 4:00 PM – 5:00 PM (CAT)

Impact:
About 38% of users experienced slow load times when fetching food data. API response times exceeded 12 seconds, leading to delays in retrieving calorie and nutrient information.

🧐Root Cause:
A missing database index caused a query fetching food items to perform a full table scan, significantly increasing response times.

⏳Timeline
4:00 PM (WAT): Monitoring alert triggered due to high API response times.

4:27 PM: Frontend engineer reported slow API responses in the UI.

4:35 PM: Backend team checked logs and identified a slow SQL query.

4:45 PM: Investigation revealed the lack of an index on the food_name column.

4:52 PM: Index added to food_name, improving query performance.

5:00 PM: API response times returned to normal, issue resolved.

🤔Root Cause and Resolution
🔎Root Cause:
A key database query was performing a full table scan due to a missing index on the food_name column in the PostgreSQL database. This caused increased query execution times under moderate load.

📌Resolution:
An index was created on food_name, allowing faster lookups.

Queries were optimized to take advantage of indexed searches.

Database performance monitoring was updated to detect slow queries earlier.

Corrective and Preventative Measures Improvements:

Ensure proper indexing on frequently queried columns.

Enhance database monitoring for slow queries.

Automate query performance checks.

Task List:
Create and execute a script to prevent a similar issue from occuring again
Example Fix - SQL Script
To prevent similar issues in the future, the following SQL command was executed to add the missing index:

CREATE INDEX idx_food_name ON food_items(food_name);

🎨Query Debugging Flow
To ensure faster debugging in the future, we propose the following step-by-step approach:

🚨[Query Performance Alert] --> 🔎[Check Slow Queries Log] --> 🤔[Identify Missing Index] --> 💡[Create Index] --> 🚀🎉[Verify Performance Improvement]

By implementing these measures, we aim to improve database efficiency and prevent similar slowdowns in the future.💪🥤
