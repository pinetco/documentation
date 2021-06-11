## Mark Invoice As Payed

- Remember the invoice ID
- Go to Transactions table
- Find subject_id
- You'll find transaction ID
- Now follow below steps

```
    tenant()->setTenant(Website::first());
    
    Transaction::find(transactionId)->forceMarkAsPayed(now());
    
```