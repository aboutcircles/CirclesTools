# Circles Indexer Guide for Agents

This guide documents the two Circles indexer environments and all available JSON-RPC query methods. Use it to know which endpoint to call and what parameters each method accepts.

---

## Indexers

| Name | RPC Endpoint | Pathfinder Endpoint | Chain RPC Endpoint |
|------|-------------|---------------------|--------------------|
| **Staging2** | `https://staging.circlesubi.network/` | `https://staging.circlesubi.network/` | `https://rpc.gnosischain.com` |
| **Production** | `https://rpc.aboutcircles.com/` | `https://rpc.aboutcircles.com/` | `https://rpc.aboutcircles.com/` |

> A legacy **Staging** indexer exists at `https://rpc.circlesubi.network/` but is not recommended for new development.

### Endpoint types per category

| Category | Endpoint to use |
|----------|----------------|
| Balance & Tokens | RPC |
| Avatars & Profiles | RPC |
| Trust & Groups | RPC |
| Transactions | RPC |
| Events & Query | RPC |
| SDK Methods | RPC |
| Pathfinder | Pathfinder |
| Chain RPC | Chain RPC |
| System | RPC |

---

## Quick Method Reference

| Method | Category | Staging2 | Production |
|--------|----------|----------|------------|
| `circles_getTotalBalance` | Balance | ✓ | ✓ |
| `circlesV2_getTotalBalance` | Balance | ✓ | ✓ |
| `circles_getTokenBalances` | Balance | ✓ | ✓ |
| `circles_getTokenInfo` | Balance | ✓ | ✓ |
| `circles_getTokenInfoBatch` | Balance | ✓ | ✓ |
| `circles_getAvatarInfo` | Avatars | ✓ | ✓ |
| `circles_getAvatarInfoBatch` | Avatars | ✓ | ✓ |
| `circles_getProfileByAddress` | Avatars | ✓ | ✓ |
| `circles_getProfileByAddressBatch` | Avatars | ✓ | ✓ |
| `circles_getProfileCid` | Avatars | ✓ | ✓ |
| `circles_getProfileByCid` | Avatars | ✓ | ✓ |
| `circles_searchProfiles` | Avatars | ✓ | ✓ |
| `circles_searchProfileByAddressOrName` | Avatars | ✓ | ✓ |
| `circles_getTrustRelations` | Trust | ✓ | ✓ |
| `circles_getAggregatedTrustRelations` | Trust | ✓ | ✓ |
| `circles_getCommonTrust` | Trust | ✓ | ✓ |
| `circles_findGroups` | Trust | ✓ | **Staging2 only** |
| `circles_getGroupMembers` | Trust | ✓ | ✓ |
| `circles_getGroupMemberships` | Trust | ✓ | ✓ |
| `circles_getNetworkSnapshot` | Trust | ✓ | ✓ |
| `circles_getTransactionHistory` | Transactions | ✓ | ✓ |
| `circles_getTransactionHistoryEnriched` | Transactions | ✓ | ✓ |
| `circles_getTokenHolders` | Transactions | ✓ | ✓ |
| `circles_getTransferData` | Transactions | ✓ | ✓ |
| `circles_events` | Events & Query | ✓ | ✓ |
| `circles_query` | Events & Query | ✓ | ✓ |
| `circles_tables` | Events & Query | ✓ | ✓ |
| `circles_getProfileView` | SDK | ✓ | ✓ |
| `circles_getTrustNetworkSummary` | SDK | ✓ | ✓ |
| `circles_getAggregatedTrustRelationsEnriched` | SDK | ✓ | ✓ |
| `circles_getValidInviters` | SDK | ✓ | ✓ |
| `circles_getInvitationOrigin` | SDK | ✓ | ✓ |
| `circles_getAllInvitations` | SDK | ✓ | ✓ |
| `circlesV2_findPath` | Pathfinder | ✓ | ✓ |
| `eth_blockNumber` | Chain RPC | ✓ | ✓ |
| `eth_syncing` | Chain RPC | ✓ | ✓ |
| `eth_chainId` | Chain RPC | ✓ | ✓ |
| `eth_getBalance` | Chain RPC | ✓ | ✓ |
| `eth_getBlockByNumber` | Chain RPC | ✓ | ✓ |
| `eth_getTransactionByHash` | Chain RPC | ✓ | ✓ |
| `eth_getTransactionReceipt` | Chain RPC | ✓ | ✓ |
| `eth_getLogs` | Chain RPC | ✓ | ✓ |
| `circles_health` | System | ✓ | ✓ |

---

## Method Details

### Balance & Tokens

#### `circles_getTotalBalance`
Get total V1 Circles balance for an address. Use `circlesV2_getTotalBalance` for V2 accounts.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Ethereum address to check |
| `version` | number | no | Protocol version (1 or 2) |
| `asTimeCircles` | boolean | no | Format as TimeCircles (default: `true`) |

---

#### `circlesV2_getTotalBalance`
Get total V2 Circles balance for an address. Recommended for V2 accounts.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Ethereum address to check |
| `asTimeCircles` | boolean | no | Format as TimeCircles (default: `true`) |

---

#### `circles_getTokenBalances`
Get all token balances with full metadata for an address.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Address to get balances for |

---

#### `circles_getTokenInfo`
Get metadata for a specific token.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `tokenAddress` | address | yes | Token contract address |

---

#### `circles_getTokenInfoBatch`
Get metadata for multiple tokens in one call.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `tokenAddresses` | address[] | yes | Array of token contract addresses |

---

### Avatars & Profiles

#### `circles_getAvatarInfo`
Get avatar information for an address (V1 and V2 merged view).

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |

---

#### `circles_getAvatarInfoBatch`
Get avatar information for multiple addresses.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `addresses` | address[] | yes | Array of avatar addresses |

---

#### `circles_getProfileByAddress`
Get profile data for an avatar address.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |

---

#### `circles_getProfileByAddressBatch`
Get profiles for multiple addresses.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `addresses` | address[] | yes | Array of avatar addresses |

---

#### `circles_getProfileCid`
Get the IPFS CID for an avatar's profile.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |

---

#### `circles_getProfileByCid`
Retrieve a profile from IPFS by its CID.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `cid` | string | yes | CIDv0 string |

---

#### `circles_searchProfiles`
Full-text search for profiles.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `text` | string | yes | Search query (max 3 tokens) |
| `limit` | number | no | Max results, max 100 (default: `20`) |
| `offset` | number | no | Pagination offset (default: `0`) |
| `types` | string[] | no | Filter by avatar types |

---

#### `circles_searchProfileByAddressOrName`
Unified search by address prefix OR name/text. Prefix query with `0x` to trigger address search.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `query` | string | yes | Search query (`0x` prefix = address search) |
| `limit` | number | no | Max results (default: `20`) |
| `cursor` | string | no | Pagination cursor |
| `types` | string[] | no | Filter by avatar types |

---

### Trust & Groups

#### `circles_getTrustRelations`
Get trust relationships for an address.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |

---

#### `circles_getAggregatedTrustRelations`
Get aggregated trust relations in SDK-compatible format.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `avatar` | address | yes | Avatar address |

---

#### `circles_getCommonTrust`
Find addresses that two users both trust.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address1` | address | yes | First address |
| `address2` | address | yes | Second address |
| `version` | number | no | Filter by protocol version (1, 2, or omit for both) |

---

#### `circles_findGroups` ⚠️ Staging2 only

Find groups with optional filters. **Not available on Production.**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `limit` | number | no | Max results (default: `50`) |
| `queryParams` | object | no | Filter: `{ nameStartsWith, symbolStartsWith, ownerIn }` |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_getGroupMembers`
Get members of a specific group with pagination.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `groupAddress` | address | yes | Group address |
| `limit` | number | no | Max results (default: `100`) |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_getGroupMemberships`
Get groups that an avatar is a member of.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `memberAddress` | address | yes | Member address |
| `limit` | number | no | Max results (default: `50`) |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_getNetworkSnapshot`
Get a complete snapshot of the Circles trust network. No parameters.

---

### Transactions

#### `circles_getTransactionHistory`
Get transaction history for an avatar.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `avatarAddress` | address | yes | Avatar address |
| `limit` | number | no | Max transactions (default: `50`) |
| `cursor` | string | no | Pagination cursor |
| `version` | number | no | Filter by version (omit for both) |
| `excludeIntermediary` | boolean | no | Exclude intermediary hops (default: `true`) |

---

#### `circles_getTransactionHistoryEnriched`
Transaction history with enriched participant profiles.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |
| `fromBlock` | number | yes | Starting block number |
| `toBlock` | number | no | Ending block number |
| `limit` | number | no | Max transactions (default: `20`) |
| `cursor` | string | no | Pagination cursor |
| `version` | number | no | Filter by protocol version |
| `excludeIntermediary` | boolean | no | Exclude intermediary hops (default: `true`) |

---

#### `circles_getTokenHolders`
Get all holders of a specific token.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `tokenAddress` | address | yes | Token address |
| `limit` | number | no | Max holders (default: `100`) |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_getTransferData`
Get transfer data (calldata bytes) for ERC-1155 transfers.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Primary address to filter |
| `direction` | string | no | `"sent"`, `"received"`, or omit for both |
| `counterparty` | address | no | Counterparty address filter |
| `fromBlock` | number | no | Start block (inclusive) |
| `toBlock` | number | no | End block (inclusive) |
| `limit` | number | no | Max results, max 1000 (default: `50`) |
| `cursor` | string | no | Pagination cursor |

---

### Events & Query

#### `circles_events`
Query indexed blockchain events with advanced filtering.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | no | Filter by address |
| `fromBlock` | number | no | Starting block (inclusive) |
| `toBlock` | number | no | Ending block (inclusive) |
| `eventTypes` | string[] | no | Filter by event types (see list below) |
| `filterPredicates` | object[] | no | Advanced filter predicates |
| `sortAscending` | boolean | no | Sort order (default: `false`) |
| `limit` | number | no | Max events, max 1000 (default: `100`) |
| `cursor` | string | no | Pagination cursor |

**Supported event types:**

| V1 Events | V2 Events |
|-----------|-----------|
| `CrcV1_Signup` | `CrcV2_RegisterHuman` |
| `CrcV1_OrganizationSignup` | `CrcV2_RegisterOrganization` |
| `CrcV1_Trust` | `CrcV2_RegisterGroup` |
| `CrcV1_HubTransfer` | `CrcV2_RegisterShortName` |
| `CrcV1_Transfer` | `CrcV2_PersonalMint` |
| | `CrcV2_Trust` |
| | `CrcV2_Stopped` |
| | `CrcV2_ApprovalForAll` |
| | `CrcV2_TransferSingle` |
| | `CrcV2_TransferBatch` |
| | `CrcV2_TransferData` |
| | `CrcV2_UpdateMetadataDigest` |
| | `CrcV2_URI` |
| | `CrcV2_ERC20WrapperDeployed` |
| | `CrcV2_Erc20WrapperTransfer` |
| | `CrcV2_DepositInflationary` |
| | `CrcV2_WithdrawInflationary` |
| | `CrcV2_DepositDemurraged` |
| | `CrcV2_WithdrawDemurraged` |
| | `CrcV2_StreamCompleted` |
| | `CrcV2_DiscountCost` |
| | `CrcV2_GroupMint` |
| | `CrcV2_FlowEdgesScopeSingleStarted` |
| | `CrcV2_FlowEdgesScopeLastEnded` |

---

#### `circles_query`
Generic database query using structured DTOs.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `namespace` | string | yes | Database namespace |
| `table` | string | yes | Table name |
| `columns` | string[] | no | Specific columns to retrieve (omit for all) |
| `filter` | object[] | no | WHERE conditions (`FilterPredicateDto`) |
| `order` | object[] | no | ORDER BY clauses |
| `limit` | number | no | Row limit |
| `distinct` | boolean | no | Remove duplicates |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_tables`
Get available database tables and their schemas. No parameters.

---

### SDK Methods

#### `circles_getProfileView`
Complete profile combining avatar info, profile data, trust stats, and balances.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |

---

#### `circles_getTrustNetworkSummary`
Aggregated trust network statistics for an address.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |
| `maxDepth` | number | no | Max depth for network traversal |

---

#### `circles_getAggregatedTrustRelationsEnriched`
Trust relations categorized by type with enriched avatar info.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |
| `limit` | number | no | Max results per page (default: `50`) |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_getValidInviters`
Addresses that trust the given address AND have sufficient balance to invite.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |
| `minimumBalance` | string | no | Minimum balance required (in CRC) |
| `limit` | number | no | Max results (default: `50`) |
| `cursor` | string | no | Pagination cursor |

---

#### `circles_getInvitationOrigin`
Invitation origin showing how a user joined Circles.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |

---

#### `circles_getAllInvitations`
All available invitations for an address from all sources.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Avatar address |
| `minimumBalance` | string | no | Minimum balance required (in CRC) |

---

### Pathfinder

#### `circlesV2_findPath`
Calculate a transitive payment path through the trust network. Uses the **pathfinder endpoint**.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `source` | address | yes | Source address |
| `sink` | address | yes | Destination address |
| `targetFlow` | string | yes | Target amount as uint256 string (wei). Use `"MAX"` for maximum flow. |
| `withWrap` | boolean | no | Enable ERC20 wrapping |
| `fromTokens` | address[] | no | Whitelist of source tokens |
| `toTokens` | address[] | no | Whitelist of destination tokens |
| `excludedFromTokens` | address[] | no | Blacklist of source tokens |
| `excludedToTokens` | address[] | no | Blacklist of destination tokens |
| `simulatedBalances` | object[] | no | Override balances for testing |
| `simulatedTrusts` | object[] | no | Override trusts for testing |
| `simulatedConsentedAvatars` | address[] | no | Pre-consented avatars |
| `maxTransfers` | number | no | Max transfer hops |
| `quantizedMode` | boolean | no | 96 CRC quantization (for invitations) |

---

### Chain RPC

These methods use the **Chain RPC endpoint** (Gnosis Chain for Staging2, `rpc.aboutcircles.com` for Production).

#### `eth_blockNumber`
Get the current block number. No parameters.

---

#### `eth_syncing`
Check if the node is syncing. No parameters.

---

#### `eth_chainId`
Get the chain ID. No parameters.

---

#### `eth_getBalance`
Get the native token balance of an address.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | address | yes | Address to check |
| `block` | string | no | Block number or `"latest"` (default: `"latest"`) |

---

#### `eth_getBlockByNumber`
Get a block by its number.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `blockNumber` | string | yes | Block number (hex) or `"latest"` |
| `fullTx` | boolean | no | Include full transaction objects (default: `false`) |

---

#### `eth_getTransactionByHash`
Get a transaction by its hash.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `txHash` | string | yes | Transaction hash |

---

#### `eth_getTransactionReceipt`
Get a transaction receipt by its hash.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `txHash` | string | yes | Transaction hash |

---

#### `eth_getLogs`
Get logs matching a filter.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `filter` | object | yes | Filter object: `{ fromBlock, toBlock, address, topics[] }` |

Example filter: `{ "fromBlock": "latest", "toBlock": "latest", "address": "0x..." }`

---

### System

#### `circles_health`
Health check endpoint. No parameters. Returns indexer health status.
