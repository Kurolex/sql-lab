<h1>Applying Filters to SQL Queries Lab</h1>

<h2>Description</h2>
<p>
This lab was completed as part of the <b>Google Cybersecurity Professional Certificate</b> series to build familiarity with using SQL filters.
In this scenario, I acted as a security analyst responsible for monitoring login data, identifying suspicious login attempts, and retrieving information about employee systems for updates.
</p>

<p>
The following steps below demonstrate how I used SQL filters to query two tables: <b>log_in_attempts</b> and <b>employees</b> in order to perform security-related tasks such as identifying failed login attempts, investigating specific incidents, and retrieving employee information.
</p>

<h2>Language & Environment Used</h2>
<ul>
  <li><b>SQL / MySQL Database Environment (MariaDB)</b></li>
  <li><b>Simulated organization database (Google Skills)</b></li>
</ul>

<hr>

<h3>1. Retrieve After-Hours Failed Login Attempts</h3>
<p>
A potential security incident occurred after business hours (after 18:00). 
All after-hours login attempts that failed needed to be investigated.
</p>

<p>The following code demonstrates how I created a SQL query to filter for failed login attempts that occurred after business hours.</p>

<pre><code>SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
</code></pre>

<p>
The query filters for failed login attempts that occurred after 18:00. 
First, I selected all data from the <b>log_in_attempts</b> table. Then, I used a <b>WHERE</b> clause with an <b>AND</b> operator to filter only login attempts that occurred after 18:00 and were unsuccessful. 
The condition <b>login_time > '18:00'</b> isolates after-hours attempts, while <b>success = FALSE</b> filters for failed logins.
</p>

![sql1](https://i.imgur.com/3txG2Xc.jpeg)

<hr>

<h3>2. Retrieve Login Attempts on Specific Dates</h3>
<p>
A suspicious event occurred on 2022-05-09. 
To investigate, I retrieved all login activity that happened on 2022-05-09 and the day before.
</p>

<p>The following SQL query filters for login attempts that occurred on specific dates.</p>

<pre><code>SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
</code></pre>

<p>
This query returns all login attempts that occurred on 2022-05-09 or 2022-05-08. 
I used a <b>WHERE</b> clause with an <b>OR</b> operator to include both dates. 
The condition <b>login_date = '2022-05-09'</b> retrieves logins from May 9th, and <b>login_date = '2022-05-08'</b> retrieves logins from the previous day.
</p>

![sql2.1](https://i.imgur.com/Fw8fBU5.jpeg)
![sql2.2](https://i.imgur.com/xdbIzM2.jpeg)

<hr>

<h3>3. Retrieve Login Attempts Outside of Mexico</h3>
<p>
After reviewing the organization’s data, I noticed potential anomalies in login attempts that occurred outside of Mexico. 
These logins warranted further investigation.
</p>

<p>The following SQL query filters for login attempts that occurred in countries other than Mexico.</p>

<pre><code>SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
</code></pre>

<p>
This query returns all login attempts that occurred in countries other than Mexico.
I started by selecting all data from the <b>log_in_attempts</b> table, then used a <b>WHERE</b> clause with <b>NOT</b> and <b>LIKE</b> to exclude “MEX” and “MEXICO.”  
The <b>%</b> wildcard allows the filter to match both patterns, ensuring complete coverage of the dataset.
</p>

![sql3.1](https://i.imgur.com/tSfhNcD.jpeg)
![sql3.2](https://i.imgur.com/AM1ObNu.jpeg)

<hr>

<h3>4. Retrieve Employees in the Marketing Department (East Building)</h3>
<p>
My team needed to update computers for employees in the Marketing department who work in the East building. 
To find which machines to update, I retrieved data from the <b>employees</b> table using filters.
</p>

<p>The following SQL query filters for Marketing department employees located in the East building.</p>

<pre><code>SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
</code></pre>

<p>
This query returns all employees in the Marketing department located in the East building.  
I used a <b>WHERE</b> clause with an <b>AND</b> operator to apply both conditions.
The <b>LIKE 'East%'</b> pattern matches any office number beginning with “East.”
</p>

![sql4](https://i.imgur.com/z34ngPx.jpeg)

<hr>

<h3>5. Retrieve Employees in Finance or Sales</h3>
<p>
Another security update was required for employees in the Finance and Sales departments.
I retrieved information only for those employees.
</p>

<p>The following SQL query filters for employees in either the Finance or Sales departments.</p>

<pre><code>SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
</code></pre>

<p>
This query returns all employees who belong to either the Finance or Sales department.
I used a <b>WHERE</b> clause with the <b>OR</b> operator because I wanted results that matched either condition.
The first condition filters for Finance, and the second for Sales.
</p>

![sql5.1](https://i.imgur.com/HOjHpTJ.jpeg)
![sql5.2](https://i.imgur.com/trcPWtH.jpeg)

<hr>

<h3>6. Retrieve Employees Not in IT</h3>
<p>
The final update applied to all employees except those in the Information Technology (IT) department.
I retrieved information for these employees using the following query:
</p>

<pre><code>SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
</code></pre>

<p>
This query returns all employees not in the Information Technology department.  
I started by selecting all data from the <b>employees</b> table, then used a <b>WHERE</b> clause with the <b>NOT</b> operator to exclude IT staff from the results.
</p>

![sql6.1](https://i.imgur.com/Q4s7P9j.jpeg)
![sql6.2](https://i.imgur.com/0bXeDzL.jpeg)

<hr>

<h2>Summary</h2>
<p>
In this lab, I practiced applying SQL filters to extract targeted information from database tables for security and IT maintenance tasks.
I used the <b>AND</b>, <b>OR</b>, and <b>NOT</b> operators to create precise queries and the <b>LIKE</b> operator with wildcard characters to match data patterns. These exercises helped reinforce my understanding of how SQL can support cybersecurity investigations and operational workflows by isolating meaningful data from large datasets.
</p>

## Credit

Google Career Certificate: *Foundations of Cybersecurity – Applying Filters to SQL Queries Lab* https://www.skills.google/focuses/44587862?parent=lti_session&parent=lti_session
