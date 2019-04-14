# did-method-kt
DID method based on key transparency. Thought exercise DID method.

## Author
Kim Hamilton Duffy 

## Background

## Target System

Key transparency servers...TODO

## DID Method Name

The namestring that shall identify this DID method is: `kt`

A DID that uses this method MUST begin with the following prefix: `did:kt`. Per the DID specification, this string 
MUST be in lowercase. The remainder of the DID, after the prefix, is specified below.

## Method Specific Identifier

The method specific identifier is a key transparency id. 

```
kt-did = "did:kt:" id
```

### Example

```
did:kt:<key>
```

## JSON-LD Context Definition
    
## CRUD Operation Definitions

### Create (Register)

Create uses the post operation

```
keytransparency-client post <id> \
--client-secret=client_secret.json \
--insecure \
--password=${PASSWORD} \
--data='dGVzdA==' #Base64
```


### Read (Resolve)

Read uses the get operation

```
keytransparency-client get <id> --insecure --verbose
✓ Commitment verified.
✓ VRF verified.
✓ Sparse tree proof verified.
✓ Signed Map Head signature verified.
CT ✓ STH signature verified.
CT ✓ Consistency proof verified.
CT   New trusted STH: 2016-09-12 15:31:19.547 -0700 PDT
CT ✓ SCT signature verified. Saving SCT for future inclusion proof verification.
✓ Signed Map Head CT inclusion proof verified.
keys:<key:"app1" value:"test" >
```

### Update
TODO:
https://github.com/google/keytransparency/blob/master/docs/design.md#client-operations 

### Delete



## Security Considerations


