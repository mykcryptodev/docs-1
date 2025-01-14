---
slug: /IGovernorUpgradeable
title: IGovernorUpgradeable
hide_title: true
displayed_sidebar: contracts
---

# IGovernorUpgradeable

_Interface of the {Governor} core. *Available since v4.3.*_

## Methods

### COUNTING_MODE

```solidity
function COUNTING_MODE() external pure returns (string)
```

module:voting

_A description of the possible `support` values for {castVote} and the way these votes are counted, meant to be consumed by UIs to show correct vote options and interpret the results. The string is a URL-encoded sequence of key-value pairs that each describe one aspect, for example `support=bravo&amp;quorum=for,abstain`. There are 2 standard keys: `support` and `quorum`. - `support=bravo` refers to the vote options 0 = Against, 1 = For, 2 = Abstain, as in `GovernorBravo`. - `quorum=bravo` means that only For votes are counted towards quorum. - `quorum=for,abstain` means that both For and Abstain votes are counted towards quorum. NOTE: The string can be decoded by the standard https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams JavaScript class._

#### Returns

| Name | Type   | Description |
| ---- | ------ | ----------- |
| \_0  | string | undefined   |

### castVote

```solidity
function castVote(uint256 proposalId, uint8 support) external nonpayable returns (uint256 balance)
```

_Cast a vote Emits a {VoteCast} event._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |
| support    | uint8   | undefined   |

#### Returns

| Name    | Type    | Description |
| ------- | ------- | ----------- |
| balance | uint256 | undefined   |

### castVoteBySig

```solidity
function castVoteBySig(uint256 proposalId, uint8 support, uint8 v, bytes32 r, bytes32 s) external nonpayable returns (uint256 balance)
```

_Cast a vote using the user cryptographic signature. Emits a {VoteCast} event._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |
| support    | uint8   | undefined   |
| v          | uint8   | undefined   |
| r          | bytes32 | undefined   |
| s          | bytes32 | undefined   |

#### Returns

| Name    | Type    | Description |
| ------- | ------- | ----------- |
| balance | uint256 | undefined   |

### castVoteWithReason

```solidity
function castVoteWithReason(uint256 proposalId, uint8 support, string reason) external nonpayable returns (uint256 balance)
```

_Cast a vote with a reason Emits a {VoteCast} event._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |
| support    | uint8   | undefined   |
| reason     | string  | undefined   |

#### Returns

| Name    | Type    | Description |
| ------- | ------- | ----------- |
| balance | uint256 | undefined   |

### execute

```solidity
function execute(address[] targets, uint256[] values, bytes[] calldatas, bytes32 descriptionHash) external payable returns (uint256 proposalId)
```

_Execute a successful proposal. This requires the quorum to be reached, the vote to be successful, and the deadline to be reached. Emits a {ProposalExecuted} event. Note: some module can modify the requirements for execution, for example by adding an additional timelock._

#### Parameters

| Name            | Type      | Description |
| --------------- | --------- | ----------- |
| targets         | address[] | undefined   |
| values          | uint256[] | undefined   |
| calldatas       | bytes[]   | undefined   |
| descriptionHash | bytes32   | undefined   |

#### Returns

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

### getVotes

```solidity
function getVotes(address account, uint256 blockNumber) external view returns (uint256)
```

module:reputation

_Voting power of an `account` at a specific `blockNumber`. Note: this can be implemented in a number of ways, for example by reading the delegated balance from one (or multiple), {ERC20Votes} tokens._

#### Parameters

| Name        | Type    | Description |
| ----------- | ------- | ----------- |
| account     | address | undefined   |
| blockNumber | uint256 | undefined   |

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### hasVoted

```solidity
function hasVoted(uint256 proposalId, address account) external view returns (bool)
```

module:voting

_Returns weither `account` has cast a vote on `proposalId`._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |
| account    | address | undefined   |

#### Returns

| Name | Type | Description |
| ---- | ---- | ----------- |
| \_0  | bool | undefined   |

### hashProposal

```solidity
function hashProposal(address[] targets, uint256[] values, bytes[] calldatas, bytes32 descriptionHash) external pure returns (uint256)
```

module:core

_Hashing function used to (re)build the proposal id from the proposal details.._

#### Parameters

| Name            | Type      | Description |
| --------------- | --------- | ----------- |
| targets         | address[] | undefined   |
| values          | uint256[] | undefined   |
| calldatas       | bytes[]   | undefined   |
| descriptionHash | bytes32   | undefined   |

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### name

```solidity
function name() external view returns (string)
```

module:core

_Name of the governor instance (used in building the ERC712 domain separator)._

#### Returns

| Name | Type   | Description |
| ---- | ------ | ----------- |
| \_0  | string | undefined   |

### proposalDeadline

```solidity
function proposalDeadline(uint256 proposalId) external view returns (uint256)
```

module:core

_Block number at which votes close. Votes close at the end of this block, so it is possible to cast a vote during this block._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### proposalSnapshot

```solidity
function proposalSnapshot(uint256 proposalId) external view returns (uint256)
```

module:core

_Block number used to retrieve user&#39;s votes and quorum. As per Compound&#39;s Comp and OpenZeppelin&#39;s ERC20Votes, the snapshot is performed at the end of this block. Hence, voting for this proposal starts at the beginning of the following block._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### propose

```solidity
function propose(address[] targets, uint256[] values, bytes[] calldatas, string description) external nonpayable returns (uint256 proposalId)
```

_Create a new proposal. Vote start {IGovernor-votingDelay} blocks after the proposal is created and ends {IGovernor-votingPeriod} blocks after the voting starts. Emits a {ProposalCreated} event._

#### Parameters

| Name        | Type      | Description |
| ----------- | --------- | ----------- |
| targets     | address[] | undefined   |
| values      | uint256[] | undefined   |
| calldatas   | bytes[]   | undefined   |
| description | string    | undefined   |

#### Returns

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

### quorum

```solidity
function quorum(uint256 blockNumber) external view returns (uint256)
```

module:user-config

_Minimum number of cast voted required for a proposal to be successful. Note: The `blockNumber` parameter corresponds to the snaphot used for counting vote. This allows to scale the quroum depending on values such as the totalSupply of a token at this block (see {ERC20Votes})._

#### Parameters

| Name        | Type    | Description |
| ----------- | ------- | ----------- |
| blockNumber | uint256 | undefined   |

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### state

```solidity
function state(uint256 proposalId) external view returns (enum IGovernorUpgradeable.ProposalState)
```

module:core

_Current state of a proposal, following Compound&#39;s convention_

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

#### Returns

| Name | Type                                    | Description |
| ---- | --------------------------------------- | ----------- |
| \_0  | enum IGovernorUpgradeable.ProposalState | undefined   |

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) external view returns (bool)
```

_Returns true if this contract implements the interface defined by `interfaceId`. See the corresponding https://eips.ethereum.org/EIPS/eip-165#how-interfaces-are-identified[EIP section] to learn more about how these ids are created. This function call must use less than 30 000 gas._

#### Parameters

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| interfaceId | bytes4 | undefined   |

#### Returns

| Name | Type | Description |
| ---- | ---- | ----------- |
| \_0  | bool | undefined   |

### version

```solidity
function version() external view returns (string)
```

module:core

_Version of the governor instance (used in building the ERC712 domain separator). Default: &quot;1&quot;_

#### Returns

| Name | Type   | Description |
| ---- | ------ | ----------- |
| \_0  | string | undefined   |

### votingDelay

```solidity
function votingDelay() external view returns (uint256)
```

module:user-config

_Delay, in number of block, between the proposal is created and the vote starts. This can be increassed to leave time for users to buy voting power, of delegate it, before the voting of a proposal starts._

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

### votingPeriod

```solidity
function votingPeriod() external view returns (uint256)
```

module:user-config

_Delay, in number of blocks, between the vote start and vote ends. NOTE: The {votingDelay} can delay the start of the vote. This must be considered when setting the voting duration compared to the voting delay._

#### Returns

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \_0  | uint256 | undefined   |

## Events

### ProposalCanceled

```solidity
event ProposalCanceled(uint256 proposalId)
```

_Emitted when a proposal is canceled._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

### ProposalCreated

```solidity
event ProposalCreated(uint256 proposalId, address proposer, address[] targets, uint256[] values, string[] signatures, bytes[] calldatas, uint256 startBlock, uint256 endBlock, string description)
```

_Emitted when a proposal is created._

#### Parameters

| Name        | Type      | Description |
| ----------- | --------- | ----------- |
| proposalId  | uint256   | undefined   |
| proposer    | address   | undefined   |
| targets     | address[] | undefined   |
| values      | uint256[] | undefined   |
| signatures  | string[]  | undefined   |
| calldatas   | bytes[]   | undefined   |
| startBlock  | uint256   | undefined   |
| endBlock    | uint256   | undefined   |
| description | string    | undefined   |

### ProposalExecuted

```solidity
event ProposalExecuted(uint256 proposalId)
```

_Emitted when a proposal is executed._

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| proposalId | uint256 | undefined   |

### VoteCast

```solidity
event VoteCast(address indexed voter, uint256 proposalId, uint8 support, uint256 weight, string reason)
```

_Emitted when a vote is cast. Note: `support` values should be seen as buckets. There interpretation depends on the voting module used._

#### Parameters

| Name            | Type    | Description |
| --------------- | ------- | ----------- |
| voter `indexed` | address | undefined   |
| proposalId      | uint256 | undefined   |
| support         | uint8   | undefined   |
| weight          | uint256 | undefined   |
| reason          | string  | undefined   |
