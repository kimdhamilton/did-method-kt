# did-method-kt
A thought exercise DID method based on [Google's key transparency project](https://github.com/google/keytransparency/). 

## Author
Kim Hamilton Duffy 

## Abstract

Google's key transparency project, based on Certificate Transparency and CONIKS, enables a tamper-proof audit log of name-to-key mappings.  The goal is to make it easier to detect and track fraudulent key associations, with use cases such as"

- I can determine if an unknown key has been associated with one of my accounts (and report fraudulent activity, etc)
- I can use it to help establish the trustworthiness of another account (e.g through stability, history)
 
The goal of this DID method is to express key transparency as a DID method with the goals of:

- exploring non-blockchain target systems
- enable interop with promising transparency log approaches, which alsp seek to address weaknesses in the public PKI trust process.
- exploring a DID method in which IDs are expected to be "stickier" and for broader public use; e.g. my public PGP key (vs pairwise DIDs)
 
## Target System

Key transparency servers

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
did:kt:<id>
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

Read uses the get operation. TODO: This will be a generated DID document, similar to BTCR

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


