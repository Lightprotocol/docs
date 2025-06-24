# Terminology

---

### account

An entry in the Solana ledger that holds data or executable program code, stored on chain.

There are different kinds of accounts, including

- Data Accounts: Store arbitrary data used by programs.
- SPL Token Accounts: Manage token balances (similar to ERC-20 tokens on Ethereum).
- Program Accounts: Contain the executable code of a Solana program.

> See compressed account for the rent free equivalent.
> 

---

### account owner

The address of the program that owns the account. Only the owning program is capable of modifying the account.

> See also [authority](https://solana.com/docs/core/transactions#authority).
> 

---

### airdrop

A distribution event where tokens are sent to multiple wallet addresses, typically for free or as a reward to users.

- Distributing SPL tokens requires a token account for each recipient.
- Distributing compressed tokens does not require a token account for each recipient, hence is 5000x cheaper. Recipients can claim their airdrop e.g. in the Phantom app.

> For developers, see this guide to [create Airdrops](https://www.zkcompression.com/developers/creating-airdrops-with-compressed-tokens) with compressed tokens.
> 

> For end users, see this [no-code airdrop tool with compressed tokens, Airship](https://airship.helius.dev/) by Helius Labs.
> 

---

### [authority](https://solana.com/docs/core/transactions#authority)

The address of a user that has some kind of permission over an account.

For example:

- The ability to mint new tokens is given to the account that is the 'mint authority' for the token mint.
- The ability to upgrade a program is given to the account that is the 'upgrade authority' of a program.

---

### [client](https://solana.com/docs/core/transactions#client)

A computer program that accesses the Solana server network [cluster](https://solana.com/docs/core/transactions#cluster).

---

### [**cluster**](https://solana.com/docs/references/terminology#cluster)

A set of [validators](https://solana.com/docs/references/terminology#validator) maintaining a single [ledger](https://solana.com/docs/references/terminology#ledger).

---

### compressed account

An entry in the Solana ledger that holds arbitrary data, stored as 32 byte hash in a leaf of a state Merkle tree.

There are different kinds of compressed accounts, including

- Compressed Data Accounts: Store arbitrary data used by programs (similar to Solana accounts).
- Compressed Token Accounts: Manage token balances (similar to SPL tokens).

Key differences to Solana accounts include:

- Compressed accounts do not require a rent-exempt balance, which reduces account creation cost by > 99%.
- All Solana accounts are on chain. For Compressed accounts, only the state Merkle tree’s root hash is stored in a Solana account – a fingerprint of ~66 million Compressed accounts in one tree.
- To read or write compressed accounts, a *validity proof* is verified against the respective on chain fingerprint. Data held in Solana accounts does not require additional verification for transactions.

> Learn all shared properties and differences of Compressed to Solana accounts in this blog post.
> 

---

### compressed mint

The compressed and rent free equivalent of a token mint account.

An account type of the Compressed Token program that can produce (or 'mint') compressed tokens. 

Compressed mints uniquely represents a compressed token on the network and stores global metadata about the compressed token, including the `mint_authority`, supply, and decimals. 

> See this guide to create compressed mint.
> 

---

### compressed token

A digitally transferable asset in compressed form.

Compressed tokens are compatible with the [SPL token standard](https://solana.com/docs/tokens) and supported by major Solana wallets like Phantom and Backpack. Different compressed tokens are distinguished by their unique token mint addresses or hashes.

Regular SPL tokens can be decompressed and recompressed at will. 

> Find more information on compressed tokens here.
> 

---

### compressed token account

The compressed and rent free equivalent of a token account.

An account type in the Compressed Token Program to store information about an individual's ownership of a specific token (mint).

Each compressed token account is associated with a single mint or compressed mint. It tracks details like the token balance and owner.

Existing SPL token accounts can be compressed and decompressed at will. 

> See this guide to create compressed token accounts.
> 

> See [this guide](https://www.zkcompression.com/developers/add-compressed-token-support-to-your-wallet#advanced-integration) to decompress or compress SPL Tokens.
> 

---

### [**compute units**](https://solana.com/docs/references/terminology#compute-units)

The smallest unit of measure for consumption of computational resources of the transactions on the Solana blockchain.

---

### [**compute unit budget**](https://solana.com/docs/references/terminology#compute-budget)

The maximum number of [compute units](https://solana.com/docs/references/terminology#compute-units) consumed per transaction.

Developers set the compute unit budget via the`ComputeBudget`instruction, by default 200,000 CU, with a maximum of 1,400,000 CU.

If the transaction exceeds its compute unit limit, it fails and no changes occur. 

---

### compute unit limits per block

The total amount of compute units that all transactions in a single Solana block - the *blockspace* - can collectively consume is currently set at 48 million CU.

The maximum compute units that can be used to modify a single account within a block - the *write lock limit -* is currently set at 12 million CU.

---

### [cross-program invocation (CPI)](https://solana.com/docs/core/transactions#cross-program-invocation-cpi)

A call from one [program](https://solana.com/docs/core/transactions#onchain-program) to another. 

> For more information, see [calling between programs](https://solana.com/docs/core/cpi).
> 

---

### decompression

The process of converting a

- Compressed Account to a Solana account.
- Compressed token to SPL token, for which a regular token account is created.

> How to [decompress or claim](https://www.zkcompression.com/developers/creating-airdrops-with-compressed-tokens#advanced-decompress-claim) compressed tokens.
> 

---

### epoch

An epoch is a fixed period of time.

- A Solana epoch lasts approximately 432,000 slots, which equates to about 2–3 days, depending on slot time. Slot time varies with network conditions between ~400–600 milliseconds. Epochs are used to coordinate validator rotation, staking rewards, and governance updates.
- A Light Protocol epoch lasts …

---

### [**fee account**](https://solana.com/docs/references/terminology#fee-account)

The fee account in the transaction is the account that pays for the cost of including the transaction in the ledger. 

This is the first account in the transaction. This account must be declared as Read-Write (writable) in the transaction since paying for the transaction reduces the account balance.

---

### Forester node / Forester

A keeper node to incorporate state updates into state Merkle Trees for ZK Compression.

> Find more information on Forester nodes and their decentralization here.
> 

---

### [**hash**](https://solana.com/docs/references/terminology#hash)

A hash is a digital fingerprint of a sequence of bytes representing arbitrary data, while requiring far less storage space than the original data.

It produces a fixed-size output by a cryptographic function that uniquely represents input data, regardless of its size. Even a small change in the input results in a completely different output.

> Find more information on hash functions here.
> 

---

### [**instruction**](https://solana.com/docs/references/terminology#instruction)

A call to invoke a specific [instruction handler](https://solana.com/docs/references/terminology#instruction-handler) in a [program](https://solana.com/docs/references/terminology#program). 

An instruction also specifies which accounts it wants to read or modify, and additional data that serves as auxiliary input to the [instruction handler](https://solana.com/docs/references/terminology#instruction-handler). A [client](https://solana.com/docs/references/terminology#client) must include at least one instruction in a [transaction](https://solana.com/docs/references/terminology#transaction), and all instructions must complete for the transaction to be considered successful.

For example, Compressed accounts are created or updated with the `InvokeCpiInstruction` to the Light System Program.

> Find more information on Instructions to interact with Compressed Accounts.
> 

---

### [**keypair**](https://solana.com/docs/references/terminology#keypair)

A [public key](https://solana.com/docs/references/terminology#public-key-pubkey) and corresponding [private key](https://solana.com/docs/references/terminology#private-key) for accessing an account.

---

### [**lamport**](https://solana.com/docs/references/terminology#lamport)

A fractional [native token](https://solana.com/docs/references/terminology#native-token) with the value of 0.000000001 [sol](https://solana.com/docs/references/terminology#sol) (a billionth)

---

### **ledger**

The ledger is an immutable historical record of all Solana transactions signed by clients since the genesis block.

Transactions included in the ledger cannot be modified or removed. The ledger is “append only”, i.e. continuously grows as new transactions are appended.

A helpful analogy to differentiate Solana ledger and state:

- Ledger is the entire bank statement history.
- State is the current account balance, derived from all transactions in the bank statement history.

---

### Merkle tree

A data structure to allow for efficient cryptographic verification of the integrity of all leaves in a tree.

Each leaf on a Merkle tree is a hash of that leaf’s data. A Merkle tree compresses data by hashing pairs of data repeatedly into a single root hash, starting from the lowest level. Only this root hash is stored on chain. On Solana, this process is called state compression.

In ZK Compression’s case, state Merkle trees are provided by the protocol and fungible. Developers don’t need to initialize state Merkle trees.

> Find more information on Light Protocol’s iteration of Merkle trees here.
> 

> Find more information how ZK Compression uses state compression here.
> 

---

### Merkle tree account

For ZK Compression, the `Merkle_tree_account` is the public key of the state Merkle tree's respective on chain account (`state_tree_hash`) 

---

### merkle proof

---

### [**node**](https://solana.com/docs/references/terminology#node)

A computer participating in a [cluster](https://solana.com/docs/references/terminology#cluster).

---

### nullifier queue

---

### [**program**](https://solana.com/docs/references/terminology#onchain-program)

Programs run executable code similar to smart contracts on other blockchains with optimizations specific to Solana. 

Solana programs key characteristics include:

- Solana programs are stateless and do not store state internally. Separate accounts store state for programs to execute on, such as program, user or token data. This makes Solana’s account model [different from Ethereum’s](https://solana.com/news/evm-to-svm).
- Programs are typically written in Rust.
- Programs interpret the [instructions](https://solana.com/docs/references/terminology#instruction) sent inside of each [transaction](https://solana.com/docs/references/terminology#transaction) to read and modify accounts over which it has control, hence update state.

> Finde more information on programs essential to ZK Compression here.
> 

---

### parallelism

Transactions that modify at the same time different Solana and Compressed accounts.

---

### [**private key**](https://solana.com/docs/references/terminology#private-key)

The private key of a [keypair](https://solana.com/docs/references/terminology#keypair).

---

### [**program id**](https://solana.com/docs/references/terminology#program-id)

The public key of the [account](https://solana.com/docs/references/terminology#account) containing a [program](https://solana.com/docs/references/terminology#program).

---

### [**program derived addresses (PDA)**](https://solana.com/docs/references/terminology#program-derived-account-pda)

PDAs are special account addresses derived deterministically using optional seeds, a bump seed, and a program ID. 

They are off the Ed25519 curve, meaning they have no private key. The PDA itself, once derived, is 32 bytes, matching a regular public key.

---

### [**prioritization fee**](https://solana.com/docs/references/terminology#prioritization-fee)

An additional fee user can specify in the compute budget [instruction](https://solana.com/docs/references/terminology#instruction) to prioritize their [transactions](https://solana.com/docs/references/terminology#transaction).

The priority fee is derived from the compute unit limit and the comput unit price. The price per compute unit set by the user in micro-lamports (1 lamport = 1,000,000 micro-lamports), rounded up to the nearest lamport.

Higher CU usage can require users to increase their priority fee during network congestion. Validator clients may prioritize transactions with higher per-CU priority fees, whenever Solana's write lock limit for an account is reached.

> Find more information on priority fees here.
> 

---

### [**public key (pubkey)**](https://solana.com/docs/references/terminology#public-key-pubkey)

The public key of a [keypair](https://solana.com/docs/references/terminology#keypair).

---

### rent

A fee paid in SOL for the creation of [Accounts](https://solana.com/docs/references/terminology#account) to store data on the blockchain, tied to account size. When accounts do not have enough balance to pay rent, they may be Garbage Collected.

> See also [rent exempt](https://solana.com/docs/references/terminology#rent-exempt) below. Learn more about rent here: [What is rent?](https://solana.com/docs/intro/rent).
> 

---

### [**rent exempt**](https://solana.com/docs/references/terminology#rent-exempt)

An account that maintains a minimum lamport balance proportional to the amount of data stored on the account. 

All newly created accounts are stored on chain permanently until the account is closed. It is not possible to create an account that falls below the rent exemption threshold.

The rent exemption balance remains locked while an account is active and can be fully recovered when the account is closed.

The minimum balance is paid by the creator and is calculated as follows:

```markdown
Minimum Rent Balance = 2 × 0.00000348 SOL/byte/year × Account Size (Bytes)
```

---

### Remote Procedure Calls (RPC)

A bridge between users (or applications) and the blockchain to facilitate interactions and data retrieval.

The [ZK Compression RPC API](https://www.zkcompression.com/developers/json-rpc-methods) extends [Solana's JSON RPC API](https://solana.com/docs/rpc) with additional endpoints to interact with compressed accounts, provided by Helius Labs.

> Find more information on [ZK Compression’s JSON RPC Methods here](https://www.zkcompression.com/developers/json-rpc-methods).
> 

---

### [**smart contract**](https://solana.com/docs/references/terminology#smart-contract)

Smart contracts on Solana are called programs with key characteristics and optimizations.

> See [program](https://solana.com/docs/references/terminology#onchain-program).
> 

---

### [**SOL**](https://solana.com/docs/references/terminology#sol)

The [native token](https://solana.com/docs/references/terminology#native-token) of a Solana [cluster](https://solana.com/docs/references/terminology#cluster).

---

### Solana Account Model

The native framework to store and manage data on the Solana blockchain.

Solana’s Account Model separates program logic from state to optimize for parallel and faster transactions. Separate accounts store state for programs to execute on, such as program, user or token data. This makes Solana’s Account Model [different from Ethereum’s](https://solana.com/news/evm-to-svm).

ZK Compression extends Solana’s Account Model with Compressed Accounts.

> Learn more on Solana’s account model in the Solana Developer Documentation.
> 

> Find more information on the Compressed Accounts here.
> 

---

### [**Solana Program Library (SPL)**](https://solana.com/docs/references/terminology#solana-program-library-spl)

A [library of programs](https://spl.solana.com/) on Solana such as spl-token that facilitates tasks such as creating and using tokens.

---

### state

A snapshot representing the current status of all accounts and programs on Solana.

The state is derived from the ledger by sequentially applying every transaction. State is mutable and changes with every transaction to represent the latest state.

State is kept in RAM by validators for transaction validation. 

A helpful analogy to differentiate Solana ledger and state:

- Ledger is the entire bank statement history.
- State is the current account balance, derived from all transactions in the bank statement history.

---

### state compression

A process to lower the amount of data stored on chain using Merkle trees.

The process of state compression involves the following steps

1. millions of accounts are compressed into a “fingerprint” - the Merkle tree root hash
2. this “fingerprint” is stored in one Solana account
3. the account history is stored on the Solana ledger
4. the latest compressed data is fetched from an indexer
5. to verify the data, recompute the hashes and compare the final hash to the on chain root hash.

> Find more information [on generalized state compression here](https://solana.com/developers/courses/state-compression/generalized-state-compression).
> 

> Find more information how ZK Compression uses state compression.
> 

---

### [token](https://solana.com/docs/references/terminology#token)

A digitally transferable asset.

---

### token account

A token account is an account type in Solana's Token Programs that stores information about an individual's ownership of a specific token (mint). Each token account is associated with a single mint and tracks details like the token balance and owner.

Existing SPL token accounts can be compressed and decompressed at will.

> See compressed token for the rent free equivalent.
> 

---

### [**token mint**](https://solana.com/docs/references/terminology#token-mint)

A [mint account](https://solana.com/docs/tokens/basics/create-mint) is an account type in Solana's Token Programs that can produce (or 'mint') tokens.

Different tokens are distinguished by their unique token mint addresses. Token mints uniquely represents a token on the network and stores global metadata about the token, including the `mint_authority`, supply, and decimals. 

> See compressed mint for the rent free equivalent.
> 

---

### [**tps**](https://solana.com/docs/references/terminology#tps)

[Transactions](https://solana.com/docs/references/terminology#transaction) per second.

---

### [**transaction**](https://solana.com/docs/references/terminology#transaction)

One or more [instructions](https://solana.com/docs/references/terminology#instruction) signed by a [client](https://solana.com/docs/references/terminology#client) using one or more [keypairs](https://solana.com/docs/references/terminology#keypair) and executed atomically with only two possible outcomes: success or failure.

---

### [**validator**](https://solana.com/docs/references/terminology#validator)

A full participant in a Solana network [cluster](https://solana.com/docs/references/terminology#cluster) that produces new [blocks](https://solana.com/docs/references/terminology#block) and validates the transactions added to the [ledger](https://solana.com/docs/references/terminology#ledger).

---

### validity proof

A zero-knowledge proof of compressed state included in a transaction to read or write compressed accounts. 

The *validity proof* is 

- constant 128 byte in size (other than Merkle proofs with varying proof size), fitting well in Solana’s 1232 byte transaction limit
- verified against the respective on chain fingerprint to ensure the provided data was previously emitted
- provided and generated <80ms by indexers that support the [ZK Compression RPC API](https://www.zkcompression.com/developers/json-rpc-methods) which extend Solana's [JSON RPC API](https://solana.com/docs/rpc) to interact with compressed accounts. Developers don’t need to generate *validity proofs*.

---

### [**wallet**](https://solana.com/docs/references/terminology#wallet)

A collection of [keypairs](https://solana.com/docs/references/terminology#keypair) that allows users to manage their funds.

---

### zk (zero-knowledge) proof

A cryptographic proof to verify the validity of a statement without revealing the underlying data. 

ZK Compression uses a Groth16 SNARK zk proof

- for its constant 128 bytes *validity* proof size, to ensures the integrity of many compressed accounts, not for private or confidential transactions, and
- to store data in zk friendly data structures. Applications on Solana can prove custom off chain computations over zk compressed state (native zk compute).

---

### zk compression

A generalized compression framework to compress and verify arbitrary data with zero-knowledge proofs, to

- enable the Compressed Account Model, the rent free equivalent to Solana’s Account Model,
- solve Solana’s state growth problem, and
- build a foundation for native zk compute.

This is how ZK Compression works in a nutshell:

1. millions of compressed accounts are compressed into a “fingerprint” - the Merkle tree root hash
2. this “fingerprint” is stored in one Solana account
3. the account history is stored on the Solana ledger
4. the latest compressed account state is fetched from an indexer
5. the compressed account state is verified against the on chain “fingerprint” with a succinct zero-knowledge proof.

> Learn to develop with ZK Compression with the [Developer Documentation](https://www.zkcompression.com).
> 

> For a technical explainer of ZK Compression see the [Lightpaper](https://github.com/Lightprotocol/light-protocol/blob/main/light_paper_v0.1.0.pdf)
> 

---
