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
- Proof are digital signatures encoded with JWT, compatible with W3C Verified Credentials Model (ref: [https://www.w3.org/TR/vc-data-model/](https://www.w3.org/TR/vc-data-model/)).

Examples are:
- Birth Certificate (single clause)
- Passport (single clause)
- License
- Others 

----------------------------------
Prereq: Birth Cert
Proof: Are you older than 18?
Attesting a person is not a minor

Proof: Has this passport expired
Proof: Has this license  expired
----------------------------------


## Pseudo Code of the model
```javascript
{
  attestations: { 
     passport: [{}, {}], //JSON Schema Array
     id: [{}, {}], //JSON Schema Array
  }
}

```

## Example of an Attestation
```javascript
{
  attestations: { 
     kyc: [
{
   "$id":"https://example.com/person.schema.json",
   "$schema":"http://json-schema.org/draft-07/schema#",
   "title":"Person",
   "type":"object",
   "properties":{
      "firstName":{
         "type":"string",
         "description":"The person's first name."
      },
      "lastName":{
         "type":"string",
         "description":"The person's last name."
      },
      "age":{
         "description":"Age in years which must be equal to or greater than zero.",
         "type":"integer",
         "minimum":0
      }
   }
}
    ]
  }
}

```


### Agreements: 
- Rules should be executed by contracts and generate events.
- The contract read the terms (from: )
- El contrato tiene términos y cláusulas inherentes que son adicionales a los attestations 

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

