## did-paid 
### A did method to verify identity and residence using pluggable authentication sources


### Why did-paid

PAID Smart Agreements need verifiable proof of identity to work well with legal contracts. Legal contracts, because they are binding, need a way
to ensure all parties are accountable under a jurisdiction. In a simple legal agreement workflow, a KYC solution might be enough. But considering PAID
 is a decentralized based protocol, using smart contracts and oracles, we'll need a good set of technology stack that supports enough data sources and still
 keep the level of decentralization required.
 
 ### Proposal
 
 did-paid uses DID Method specification as standard to be able to integrate with other DID applications and services in the ecosystem. Based from ideas found in
 did-ethr, we will have the following:
 
 - `delegate`: be able to delegate to another did user
 - `add`: register public key 
 - `revoke`: unregister public key
 
 It must be resolvable, that is, be able to lookup and match by its public key.
 
 Additionally, did-paid needs to have a decentralized KYC experience, it must be able to do:
 
 - As a user, provision a signed well known document and publish it to IPFS / IPNS
 - As a user, approve or reject Certificate Authority keypair issuing
 -
