## **Asignment 3**

![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A3Q.png)
#### SELECT THE 4 FIRST MONTHS PLUS THE COUNT OF THE USERS REGISTERED IN EACH ONE
**Code used**
```sh
SELECT 
	date_trunc('month', user_timestamp) Mesos,COUNT(user_timestamp)as Monthcount
FROM
    tangarana.users
group BY
	mesos
order by 
	mesos
Limit 4;
```

![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A3P1.png)


#### SELECT NUMBER OF MONTHS AND TOTAL OF USERS DURING THE FIRST 4 
**Code used**
```sh
select 
	COUNT(n1.Mesos)AS countMonths, SUM(n1.Monthcount)as totalusersQ1
from(
	SELECT
		date_trunc('month', user_timestamp) Mesos,
		COUNT(user_timestamp)as Monthcount
	FROM
		tangarana.users
	group BY
		mesos
	order by 
		mesos
	Limit 4) n1;

```
![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A3P2.png)

#### MONTH AVERAGE OF TOTAL USERS DURING THOSE 4 MONTHS 
```sh
SELECT 
	date_trunc('month', user_timestamp) Mesos,COUNT(user_timestamp)as userscount, n2.countmonths, n2.totalusersq1,(n2.totalusersq1/n2.countmonths) as Avg_month, ((COUNT(user_timestamp)*100000/n2.totalusersq1)) as x100_month
from(
	select 
		COUNT(n1.Mesos)AS countMonths, SUM(n1.Monthcount)as totalusersQ1
	from (
		SELECT
			date_trunc('month', user_timestamp) Mesos,
			COUNT(user_timestamp)as Monthcount
		FROM
			tangarana.users
		group BY
			mesos
		order by 
			mesos
		Limit 4) n1)n2,tangarana.users
group by 
	mesos,n2.totalusersq1,n2.countmonths
order by 
	mesos
limit 4;

```
![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A3P3.png)

#### MONTH AVERAGE OF TOTAL USERS DURING THOSE 4 MONTHS USERS VALIDATED 
```sh
SELECT 
	date_trunc('month', user_timestamp) Mesos,COUNT(user_timestamp)as userscount, n2.countmonths, n2.totalusersq1,(n2.totalusersq1/n2.countmonths) as Avg_month, ((COUNT(user_timestamp)*100000/n2.totalusersq1)) as x100_month
from(
	select 
		OUNT(n1.Mesos)AS countMonths, SUM(n1.Monthcount)as totalusersQ1
	from (
		SELECT
			date_trunc('month', user_timestamp) Mesos,
			COUNT(user_timestamp)as Monthcount
		FROM
			tangarana.users
		WHERE 
			is_validated=1 
		group BY
			mesos
		order by 
			mesos
		Limit 4) n1)n2,tangarana.users
WHERE 
	is_validated=1 
group by 
	mesos,n2.totalusersq1,n2.countmonths
order by 
	mesos 
limit 4;

```
![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A3P4.png)

#### MONTH AVERAGE OF TOTAL USERS DURING THOSE 4 MONTHS USERS VALIDATED AND ENABLED
```sh
SELECT 
	date_trunc('month', user_timestamp) Mesos,COUNT(user_timestamp)as userscount, n2.countmonths, n2.totalusersq1,(n2.totalusersq1/n2.countmonths) as Avg_month, ((COUNT(user_timestamp)*100000/n2.totalusersq1)) as x100_month
from(
	select 
		OUNT(n1.Mesos)AS countMonths, SUM(n1.Monthcount)as totalusersQ1
	from (
		SELECT
			date_trunc('month', user_timestamp) Mesos,
			COUNT(user_timestamp)as Monthcount
		FROM
			tangarana.users
		WHERE 
			is_validated=1 and is_enabled=1
		group BY
			mesos
		order by 
			mesos
		Limit 4) n1)n2,tangarana.users
WHERE 
	is_validated=1 and is_enabled=1
group by 
	mesos,n2.totalusersq1,n2.countmonths
order by 
	mesos 
limit 4;
```
![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A3P4.png)