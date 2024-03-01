##estimateconversion
estimateconversion '{"currency":"name","convertto":"name","amount":n}'

This estimates conversion from one currency to another, taking into account pending conversions, fees and slippage.

Arguments:
```
1. {
      "currency": "name"       (string, required)  Name of the source currency to send in this output, defaults to
                                                       native of chain
      "amount":amount            (numeric, required) The numeric amount of currency, denominated in source currency
      "convertto":"name",      (string, optional)  Valid currency to convert to, either a reserve of a fractional, or fractional
      "preconvert":"false",    (bool,  optional)   Convert to currency at market price (default=false), only works if
                                                       transaction is mined before start of currency
      "via":"name",            (string, optional)  If source and destination currency are reserves, via is a common fractional
                                                       to convert through
   }

```
Result:
```
   {
      "inputcurrencyid": iaddress                    i-address of source currency
      "netinputamount": value                        net amount in, after conversion fees in source currency
      "outputcurrencyid": iaddress                   i-address of destination currency
      "estimatedcurrencyout": value                  estimated amount out in destination currency
      "estimatedcurrencystate": object               Estimation of all currency values, including prices and changes
   }

```
Examples
```
> verus estimateconversion '{"currency":"name","convertto":"name","amount":n}'
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "estimateconversion", "params": ['{"currency":"name","convertto":"name","amount":n}'] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/

```
