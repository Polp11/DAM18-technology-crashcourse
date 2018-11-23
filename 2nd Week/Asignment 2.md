## **Asignment 2**

![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A2Q1.png)

**Code used**
```sh
SELECT 
	transaction_country,sum(transaction_total),count(transaction_total),(Sum(transaction_total)/count(transaction_total)) as AVG_Ticket
FROM 
	tangarana.payment_transactions 
where 
	(transaction_country='FR' or transaction_country='IT') and transaction_type='payment'and transaction_status=1
group by 
	transaction_country
ORDER BY 
	transaction_country;

```

![](https://github.com/Polp11/DAM18-technology-crashcourse.git/images/A2P1.png)

There is a difference of  13.171,7603 €  and 657 tickets more sold in Italy. The price from the ticket is lower than in France. 
