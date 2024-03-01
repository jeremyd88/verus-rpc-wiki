##getcurrencyconverters
getcurrencyconverters "currency1" "currency2" ...

Retrieves all currencies that have at least 1000 VRSC in reserve, are >10% VRSC reserve ratio, and have all listed currencies as reserves

Arguments:
```
       "currencyname"               : "string" ...  (string(s), one or more) all selected currencies are returned with their current state
```
Result:
```
       "[{currency1}, {currency2}]" : "array of objects" (string) All currencies and the last notarization, which are valid converters.

```
Examples
```
> verus getcurrencyconverters '["currency1","currency2",...]'
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getcurrencyconverters", "params": ['["currency1","currency2",...]'] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/

```
