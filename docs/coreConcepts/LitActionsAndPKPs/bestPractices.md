---
sidebar_position: 5
---

# Best Practices

:::note
It is NOT recommended to use the lit-js-sdk within a Lit Action due to the potential for exponential growth of computational complexity (n^2) (eg. If 10 nodes try to get 10 signature shares, there are now 100 http requests). It is the responsibility of the client to collect and combine the signature or decryption shares, as the combination operation is not supported within a Lit Action. 
:::

## Ideal Use Cases

- [Generating proofs](/coreConcepts/LitActionsAndPKPs/litActions#proofs)
- Looking up permitted actions, addresses and [auth methods](/SDK/Explanation/LitActions/authHelpers.md) associated with a PKP
- Checking access control conditions with [conditional signing](/SDK/Explanation/LitActions/conditionalSigning.md)

## Think Twice Use Case
- POST request that inserts a new SQL row (as the Lit Action will be executed by *every* node in parallel, you will end up with n number of rows, where n is no less than two-thirds the number of total nodes in the Lit network) 


## Bad Use Cases
- ETH RPC calls
- Sending a transaction (the transaction will be sent n times, where n is no less than two-thirds the number of total nodes in the Lit network)