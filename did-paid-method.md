## did-paid 
### A did method to verify identity and residence using pluggable authentication sources


### Why did-paid

PAID Smart Agreements need verifiable proof of identity to work well with legal contracts. Legal contracts, because they are binding, need a way
to ensure all parties are accountable under a jurisdiction. In a simple legal agreement workflow, a KYC solution might be enough. But considering PAID
 is a decentralized based protocol, using smart contracts and oracles, we'll need a good set of technology stack that supports enough data sources and still
 keep the level of decentralization required.
 
 ### Proposal
 
 `did-paid` uses DID Method specification as standard to be able to integrate with other DID applications and services in the ecosystem. Based from ideas found in
 `did-ethr`, we will have the following:
 
 - `delegate`: be able to delegate to another did user
 - `add`: register public key 
 - `revoke`: unregister public key
 
 It must be resolvable, that is, be able to lookup and match by its public key.
 
 Additionally, did-paid needs to have a decentralized KYC experience, it must be able to do:
 
 - `As a user, provision a signed well known document and publish it to IPFS / IPNS`
 - `As a user, approve or reject Certificate Authority keypair issuing`
 - `As a validator, validate did-paid belongs to DNS`
 - `As a validator, validate DNS belongs to a did-paid`
 
 Ideally, but optional, provisioning must permit users to configure a `verified domain name` under paidnetwork or similar DNS name, similar to `domain.kreds`. Eg we could have a party sign a smart agreement with a domain name `alice-wonderland.paid.network` and the other party signing with `bob-realworld.paid.network`.
 
 To implement this use case requires several pieces of technology:
 
 #### P384 or secp256r1
 
 We need to sign the wellknown document using a keypair using ECDSA NIST P384. This to be compatible with the Certificate Authority and Smart Contracts requiring to verify these signatures.
 
 #### IPNS
 
 Once the document is pushed to IPFS, create and publish to IPNS and optionally, use DNSLink to link to a human readable DNS name.
 
 #### Certificate Authority
 
 There are two different implementations here:
 
 - Use of centralized CAs: (Use Let's Encrypt with ECDSA Support)[https://letsencrypt.org/certificates/]
 - Use of PAID Network Decentralized CA nodes: Using a combination of Smart Contracts and or a LB of CAs nodes
 
 #### Option 1 - Let's Encrypt
 
 Using the IPNS wellknown, provision ECDSA keypair and store in PAID wallet. These keypair will be used for Domain Name proof of identity.
 
 #### Option 2 - Smart Contract
 
 A Smart Contract in Polkadot can issue ECDSA keypairs. And either using EVM or Polkadot, be able to verify ECDSA keypairs onchain.
 
 #### Proof of Address
 
 Using an existing KYC provider Proof of Address service, create a Chainlink oracle that handles any KYC related actions. In this special case, because of cost, any proof of address validation must be accounted in the transaction and billed depending on token being used.
 
 ### Summary
 
 By maintaining developer efficient processes, putting Proof of Identity and Proof of Address allows our smart agreements protocol, to have near identitical set of requirements as those found in a KYC solution. At the same time, it doesn't disrupt the CA business, it expands the CA and digital signing for vendors. In future protocol upgrades, an incentivization model could be added to make eg a reputation voting system, to be able to have another layer of trust.
 
 ### References
 
 TODO
