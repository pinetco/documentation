# Regenerate Invoice PDF

```
    tenant()->setTenant(Website::first());
    Invoice::find(invoiceID)->savePdf()
```