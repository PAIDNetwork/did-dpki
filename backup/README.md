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
#### Agreements
A Smart Agreements is build using the Verifiable Credentials, and contains:

- A set of one more `Prequisites` (see Attestations)
- A set of Agreement `Conditions`, which can be DOM tagged (see Solido EVM Forms)
- A set of resolutions which are mapped to a court and dispute Smart Contracts representing a DAO like construct.

A `PAID Smart Agreement` is then based of a root JSON Schema and inherited schemas, these specific for each industry.

Thus, a PAID Smart Agreement is:

- A JSON Schema construct
- Has the full JSON schema specs, which includes extensions using other schemas
- Verifiable Credentials compatible
- Decentralized Identity DID compatible

*** TODO Define JSON Schema Interface for PAID Protocol Smart Agreements ***


To make Solidity make decisiones using a rules engine like code, we classify or transform a matrix of options to boolean.

##### Example 1 - Car Insurance

You sign up for a car insurance, in the contract, the following prerequisites are required:

- `Must be 18 years old or more`
- `Must have valid license`
- `Must have insurance worthiness`

Because a contract can contain myriads of terms and conditions, a condition being a boolean value or some other value that requires ML data like
classiification. 

##### Insurance terms and condition

- `Collision`: Deductable, Full, ... terms and conditions
- `Crashed`
- ...more

These conditions must be validated and coded in packaged forms. Solido Forms are then formatted either as protocol onchain format, or stored offline.
 Given the following matrix:
 
 [signature],
 [has Alice crashed Bob and accept to have court settlement]
 [has Alice crashed Bob and accepted crash accident]
 

Turn this to a matrix, where vertical are the `claims`, and horizonal are the different `actors` involved
[Alice, Bob]
[0, 1]    - has Alice crashed Bob
[0, 0]    - has Bob crashed Alice
[0, 0]    - has Alice accepted accident
[0, 0]    - has Bob accepted accident


Thus, we get a way to calculate decision making using digital signatures, what we call Smart Agreements, using smart contracts with digital signatures features. 
Using digital signatures signing, we can transform clauses to Solidity/RLP compatible packaged data.

A packed message with VC digital signatures, can be translated to xxHash operations (AND, OR, XOR):

[Alice, Bob]
[hash_0_0, hash_0_1]
[...]

Once PAID Solido Forms generates the matrix to ABIEncode or RLP, it is used in 2 scenarios:

1. xxHash are used as hash verifications (boolean algebra)
2. Because a hash, in this case non-cryptography, we can sign that with EdDSA/ECDSA and use that for Smart Routing purposes and/or rules engine.

In this case:

- "Has Alice crashed Bob: [$true]"  -> xxHash -> xxHash signed with ECDSA
- "Has Alice crashed Bob: [$false]" -> xxHash -> xxHash signed with ECDSA

Then you could send it to Smart Routing:


findDecisionFromAgreementFacts(
   smartAgreement,   // as metadata
   oracleFacts,      // has Alice crashed Bob from real time data sources = yes
   anyExistingSignatures
)

Then each decision making contract is created as a Metatransaction and uses EIP712:

1. EIP712 Domain Name -- CarInsuranceDecisionMaker
2. EIP712 Method implemented -- handleCarCollisionBetweenTwoParties()
3. Pending define eg
    a. signed(hash [0,0]) === signed(address)




























```
// pseudo code
const 


```

####ccccc`w

####m

#### Resolutions, courts and disputes

### Introducing Solido Forms, an agnostic template framework to stored JSON Schema mapped data

*** TODO Define JSON Schema Interface for Solido Forms, migrate ABIForms documentation ***


### Smart Routers, math constructs and digital signatures 

*** TODO Define how to use digital signatures as routing mechanism using matrix algebra, routing  algos and typed data messages ***


### Introducing did-dpki, a decentralized identity method for PAID network

*** TODO Define the problem and reason to create a customized did-dpki DID Method ***


### PAID Oracles, Incentivized Oracles and other constructs


### PAID Token
