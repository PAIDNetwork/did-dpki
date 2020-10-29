# PAID Protocol

## Chapter 1 - Verifiable credentials, attestations, proof, quorum signatures and oraclized data feeds


### Smart Agreements

#### Attestations
An attestation is a proof issued by an attester or issuer, either human, smart contract or API.

*The attestation model for PAID* uses W3C Verifiable Credentials Model with JSON Schemas packed as JWT. This allows us to use JWT basic features like aud, iss, nbf, exp and others sub

- *aud*: Audience
- *iss*: Issuer
- *nbf*: Not Before
- *exp*: Expiration
- *sub*: Subject


Attestations must be single clause and composable. They are either part of VC or subset of VC Model, JSON Schemas converted to JWT using `did-jwt`.

## Components of Attestations
- Proof issued by attesters (ie issuer attests a set of attributes or values).

Examples are:
- Birth Certificate (single clause)
- Passport (single clause)
- License
- Others 

An example of a birth certificate clause might be eg Are you older than 18?, this attestation, because is a precondition, is attested offchain with traditional APIs instead of using onchain transactions. It means most of a smart agreement prerequisites will be proofs inside a Verifiable Credentials model. These proofs can also be used in conjuction Zero Knowledge technology, our approach will be using SNARKS with snarks.js.


## VC Model using Javascript
```javascript
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://www.w3.org/2018/credentials/examples/v1"
  ],
  "type": ["VerifiableCredential", "UniversityDegreeCredential"],
  "credentialSchema": {
    "id": "did:example:cdf:35LB7w9ueWbagPL94T9bMLtyXDj9pX5o",
    "type": "did:example:schema:22KpkXgecryx9k7N6XN1QoN3gXwBkSU8SfyyYQG"
  },
  "issuer": "did:example:Wz4eUg7SetGfaUVCn8U9d62oDYrUJLuUtcy619",
  "credentialSubject": {
    "givenName": "Jane",
    "familyName": "Doe",
    "degree": {
      "type": "BachelorDegree",
      "name": "Bachelor of Science and Arts",
      "college": "College of Engineering"
    }
  },
  "proof": {
    "type": "CLSignature2019",
    "issuerData": "5NQ4TgzNfSQxoLzf2d5AV3JNiCdMaTgm...BXiX5UggB381QU7ZCgqWivUmy4D",
    "attributes": "pPYmqDvwwWBDPNykXVrBtKdsJDeZUGFA...tTERiLqsZ5oxCoCSodPQaggkDJy",
    "signature": "8eGWSiTiWtEA8WnBwX4T259STpxpRKuk...kpFnikqqSP3GMW7mVxC4chxFhVs",
    "signatureCorrectnessProof": "SNQbW3u1QV5q89qhxA1xyVqFa6jCrKwv...dsRypyuGGK3RhhBUvH1tPEL8orH"
  }
}}
```


#### Agreement Terms
Thus, with prerequisites of a smart agreement implemented using Verfiable Credentials model, it is also possible to construct or build an agremment
between two parties (eg Alice buys a house from Bob) using VC modeled JSON Schemas, we can then define the following JSON schema:

## General Smart Agreements JSON Schema 
```javascript
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://www.w3.org/2018/credentials/examples/v1",
    "https://paidnetwork/2020/agreements/v1",
    "https://paidnetwork/2020/vc/v1",
  ],
  "type": ["VerifiableCredential", "UniversityDegreeCredential"],
  "credentialSchema": {
    "id": "did:example:cdf:35LB7w9ueWbagPL94T9bMLtyXDj9pX5o",
    "type": "did:example:schema:22KpkXgecryx9k7N6XN1QoN3gXwBkSU8SfyyYQG"
  },
  "issuer": "did:paid:Wz4eUg7SetGfaUVCn8U9d62oDYrUJLuUtcy619",
  "credentialSubject": { // metadata
    "givenName": "Jane",
    "familyName": "Doe",
    "age": 18,
  },
  "proof": {
    "type": "CLSignature2019",   // Proof must check itsed                                                                                          
    "issuerData": "5NQ4TgzNfSQxoLzf2d5AV3JNiCdMaTgm...BXiX5UggB381QU7ZCgqWivUmy4D",
    "attributes": "pPYmqDvwwWBDPNykXVrBtKdsJDeZUGFA...tTERiLqsZ5oxCoCSodPQaggkDJy",
    "signature": "8eGWSiTiWtEA8WnBwX4T259STpxpRKuk...kpFnikqqSP3GMW7mVxC4chxFhVs",
    "signatureCorrectnessProof": "SNQbW3u1QV5q89qhxA1xyVqFa6jCrKwv...dsRypyuGGK3RhhBUvH1tPEL8orH"
  }
}}
```



#### Resolutions, courts and disputes


## Attestation Model
- Open source tools for JSON Schema with verify credentials
- Smart contracts only make verification process
- Pre requirements should be included in the contract 
- Integration with Graph Protocol

## Type of Contracts
- Dispute resolution by humans and 
- Automatic flows by smart contracts








### Smart Routers

### Introducing did-paid, a decentralized identity method for PAID network

### PAID Oracles, Incentivized Oracles and other constructs


### PAID Token

