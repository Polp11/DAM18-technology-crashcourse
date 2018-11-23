## **Asignment 4**

#### Part 1
**Code used**
```sh
select 
	to_char(user_acquisition_timestamp, 'YYYY-MM')as mesos, count(user_acquisition_timestamp)
FROM
    tangarana.payment_transactions
group BY
	mesos
order by 
	mesos;

```

![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/Part1.png)


#### Part 1
**Code used**
```sh
select d1.conv1,d3.conv3,d6.conv6,d9.conv9,d12.conv12,d15.conv15,d18.conv18,d21.conv21,d24.conv24,d27.conv27,d30.conv30,d1.rev1,d3.rev3,d6.rev6,d9.rev9,d12.rev12,d15.rev15,d18.rev18,d21.rev21,d24.rev24,d27.rev27,d30.rev30
from(SELECT count(user_acquisition_timestamp)as conv1,sum(transaction_total) as rev1
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-02 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d1,
(SELECT count(user_acquisition_timestamp)as conv3,sum(transaction_total) as rev3
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-04 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d3,
(SELECT count(user_acquisition_timestamp)as conv6,sum(transaction_total) as rev6
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-07 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d6,
(SELECT count(user_acquisition_timestamp)as conv9,sum(transaction_total) as rev9
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-10 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d9,
(SELECT count(user_acquisition_timestamp)as conv12,sum(transaction_total) as rev12
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-13 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d12,
(SELECT count(user_acquisition_timestamp)as conv15,sum(transaction_total) as rev15
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-16 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d15,
(SELECT count(user_acquisition_timestamp)as conv18,sum(transaction_total) as rev18
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-19 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d18,
(SELECT count(user_acquisition_timestamp)as conv21,sum(transaction_total) as rev21
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-22 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d21,
(SELECT count(user_acquisition_timestamp)as conv24,sum(transaction_total) as rev24
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-25 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d24,
(SELECT count(user_acquisition_timestamp)as conv27,sum(transaction_total) as rev27
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp < '2017-01-28 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d27,
(SELECT count(user_acquisition_timestamp)as conv30,sum(transaction_total) as rev30
FROM tangarana.payment_transactions
WHERE user_acquisition_timestamp >= '2017-01-01 00:00:00.0' 
AND   user_acquisition_timestamp <= '2017-02-01 00:00:00.0' 
AND transaction_status=1 AND transaction_type='payment')d30

UNION 
(next month)
```
![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/Part1.png)

**Part 2**
Excel Functions for extrapolating
- Trend()
- Forecast()
- Seasonal

**Part 3**
Regression over monthly  seasonal curve 
Prediction = Intercept + Timeperiodcoef*Timeperiodindex+S1*Tablevalue+S2*Tablevalue

**Part 4**
```sh
select 
	t1.internal_id, t1.user_type,t1.utm_source,t2.*
from 
	tangarana.users t1
right outer join 
	tangarana.payment_transactions t2
ON 
	t2.internal_id=t1.internal_id;

```