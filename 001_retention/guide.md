## Agency Retention Using the Production Analysis Report and SQL.

Author: Bill Perkins

Goals:

1. You want to understand agency retention at the account level.
2. You need to trend retention over multiple years.
3. You would like to see output that looks something like this:

- 2015: 88%
- 2016: 90%
- 2017: 91%
- 2018: 87%
- 2019: 84%
- 2020: 83%
- 2021: 88%

Prerequisites:

You are comfortable with SQL or have a desire to learn.
You have access to My Agency Reports and can run the Production Analysis report.
You have access to a database where you can load the output csv/excel production file into.


Background:

Production Analysis in AMS 360 is a very flexible report. We will use it to calculate agency/account retention.

When running the production analysis report, choose your first year as your baseline. For example, if you are interested in understanding retention rates from 2015 to 2021, run your production analysis from 2014 to 2021. 2014 will act as a baseline. 

There are many columns you can select for your output file. I suggest loading all of the columns into the database and then choose only the ones needed for the analysis. This will allow you to add new information easily.

Current Example:

The SQL code attached to this runs on PostgreSQL.
You may need to modify parts of the code depending on the database you are using.
Note: Spaces in production analysis column names have been replaced with an underscore "_".


Steps:

1. Load your production analysis data into a database table. In this case, "STAGING.PRODUCTION".
2. Create a view/CTE that includes a subset of columns from production analysis. In this case, "ACCOUNT_HISTORY".
3. Create a view/CTE that includes all unique customer policies by year. In this case, "ACTIVITY".
4. Create a view/CTE that includes the first customer policy year. In this case, "CUSTOMERS".
5. Use a select query to aggregate the views/CTE with the retention rates by year.

Comments:

This query can be modified for different retention breakouts (department, carrier, etc.)








