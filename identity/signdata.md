##signdata
signdata '{"address":"i-address or friendly name (t-address will result in simple signature w/indicated hash and prefix, nothing else)",
           "prefixstring":"extra string that is hashed during signature and must be supplied for verification",
           "filename":"filepath/filename" |
             "message":"any message" |
             "messagehex":"hexdata" |
             "messagebase64":"base64data" |
             "datahash":"256bithex",
           "vdxfkeys":["vdxfkey i-address", ...],
           "vdxfkeynames":["vdxfkeyname, object for getvdxfid API, or friendly name ID -- no i-addresses", ...],
           "boundhashes":["hexhash", ...],
           "hashtype": "sha256" | "sha256D" | "blake2b" | "keccak256"
           "signature":"currentsig"}'


Generates a hash (SHA256 default if "hashtype" not specified) of the data, returns the hash, and signs it with parameters specified

Arguments:
```
{
  "address":"t-addr or identity"                               (string, required) The transparent address or identity to use for signing.
  "filename" | "message" | "messagehex" | "messagebase64" | "datahash" (string, required) Data to sign
  "vdxfkeys":["vdxfkey", ...],                                 (array, optional)  Array of vdxfkeys or ID i-addresses
  "vdxfkeynames":["vdxfkeyname", ...],                         (array, optional)  Array of vdxfkey names or fully qualified friendly IDs
  "boundhashes":["hexhash", ...],                              (array, optional)  Array of bound hash values
  "hashtype"                                                     (string, optional) one of: "sha256", "sha256D", "blake2b", "keccak256", defaults to sha256
  "signature"                                                    (string, optional) The current signature of the message encoded in base 64 if multisig ID
}

```
Result:
```
{
  "hash":"hexhash"         (string) The hash of the message (SHA256, NOT SHA256D)
  "signature":"base64sig"  (string) The aggregate signature of the message encoded in base 64 if all or partial signing successful
}

```
Examples
```

Create the signature
> verus signdata '{"identity":"Verus Coin Foundation.vrsc@", "message":"hello world"}'

Verify the signature
> verus verifydata '{"identity":"Verus Coin Foundation.vrsc@", "message":"hello world", "signature":"base64sig"}'

As json rpc
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "signdata", "params": ['{"identity":"Verus Coin Foundation.vrsc@", "message":"hello world"}'] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/

```
