# Ledger Composable App

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GithubActions](https://github.com/zondax/ledger-composable/actions/workflows/main.yml/badge.svg)](https://github.com/Zondax/ledger-composable/blob/main/.github/workflows/main.yaml)

---

![zondax_light](docs/zondax_light.png#gh-light-mode-only)
![zondax_dark](docs/zondax_dark.png#gh-dark-mode-only)

_Please visit our website at [zondax.ch](https://www.zondax.ch)_

---

This project contains the Astar app (https://composable.finance//) for Ledger Nano S and X.

- Ledger Nano S/X BOLOS app
- Specs / Documentation
- C++ unit tests
- Zemu tests

For more information: [How to build](docs/build.md)

## ATTENTION

Please:

- **Do not use in production**
- **Do not use a Ledger device with funds for development purposes.**
- **Have a separate and marked device that is used ONLY for development and testing**
# Composable 1.1100.x

## System

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Fill block |    |   |   | `Perbill` ratio <br/> |
|Remark |    |   |   | `Vecu8` remark <br/> |
|Set heap pages |    |   |   | `u64` pages <br/> |
|Set code |    |   |   | `Vecu8` code <br/> |
|Set code without checks |    |   |   | `Vecu8` code <br/> |
|Set storage |    |   |   | `VecKeyValue` items <br/> |
|Kill storage |    |   |   | `VecKey` keys <br/> |
|Kill prefix |    |   |   | `Key` prefix <br/>`u32` subkeys <br/> |
|Remark with event |    |   |   | `Vecu8` remark <br/> |

## Timestamp

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set |    |   |   | `Compactu64` now <br/> |

## Sudo

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Sudo |    |   |   | `Call` call <br/> |
|Sudo unchecked weight |    |   |   | `Call` call <br/>`Weight` weight <br/> |
|Set key |    |   |   | `LookupasStaticLookupSource` new_ <br/> |
|Sudo as |    |   |   | `LookupasStaticLookupSource` who <br/>`Call` call <br/> |

## Indices

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Claim |    |   |   | `AccountIndex` index <br/> |
|Transfer |    |   |   | `AccountId` new_ <br/>`AccountIndex` index <br/> |
|Free |    |   |   | `AccountIndex` index <br/> |
|Force transfer |    |   |   | `AccountId` new_ <br/>`AccountIndex` index <br/>`bool` freeze <br/> |
|Freeze |    |   |   | `AccountIndex` index <br/> |

## Balances

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Transfer | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource` dest <br/>`CompactBalance` amount <br/> |
|Set balance |    | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource` who <br/>`CompactBalance` new_free <br/>`CompactBalance` new_reserved <br/> |
|Force transfer | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource` source <br/>`LookupasStaticLookupSource` dest <br/>`CompactBalance` amount <br/> |
|Transfer keep alive | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource` dest <br/>`CompactBalance` amount <br/> |
|Transfer all | :heavy_check_mark:  | :heavy_check_mark: |   | `LookupasStaticLookupSource` dest <br/>`bool` keep_alive <br/> |
|Force unreserve |    | :heavy_check_mark: |   | `LookupasStaticLookupSource` who <br/>`Balance` amount <br/> |

## ParachainSystem

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set validation data |    |   |   | `ParachainInherentData` data <br/> |
|Sudo send upward message |    |   |   | `UpwardMessage` message <br/> |
|Authorize upgrade |    |   |   | `Hash` code_hash <br/> |
|Enact authorized upgrade |    |   |   | `Vecu8` code <br/> |

## Authorship

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set uncles |    |   |   | `VecHeader` new_uncles <br/> |

## CollatorSelection

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set invulnerables |    |   |   | `VecAccountId` new_ <br/> |
|Set desired candidates |    |   |   | `u32` max <br/> |
|Set candidacy bond |    |   |   | `Balance` bond <br/> |
|Register as candidate |    |   |   |  |
|Leave intent |    |   |   |  |

## Session

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set keys |    |   |   | `Keys` keys <br/>`Bytes` proof <br/> |
|Purge keys |    |   |   |  |

## Council

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set members |    |   |   | `VecAccountId` new_members <br/>`OptionAccountId` prime <br/>`MemberCount` old_count <br/> |
|Execute |    |   |   | `Proposal` proposal <br/>`Compactu32` length_bound <br/> |
|Propose |    |   |   | `Compactu32` threshold <br/>`Proposal` proposal <br/>`Compactu32` length_bound <br/> |
|Vote |    |   |   | `Hash` proposal <br/>`Compactu32` index <br/>`bool` approve <br/> |
|Close |    |   |   | `Hash` proposal_hash <br/>`Compactu32` index <br/>`Compactu64` proposal_weight_bound <br/>`Compactu32` length_bound <br/> |
|Disapprove proposal |    |   |   | `Hash` proposal_hash <br/> |

## CouncilMembership

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Add member |    |   |   | `AccountId` who <br/> |
|Remove member |    |   |   | `AccountId` who <br/> |
|Swap member |    |   |   | `AccountId` remove <br/>`AccountId` add <br/> |
|Reset members |    |   |   | `VecAccountId` members <br/> |
|Change key |    |   |   | `AccountId` new_ <br/> |
|Set prime |    |   |   | `AccountId` who <br/> |
|Clear prime |    |   |   |  |

## Treasury

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Propose spend |    |   |   | `CompactBalance` amount <br/>`LookupasStaticLookupSource` beneficiary <br/> |
|Reject proposal |    |   |   | `Compactu32` proposal_id <br/> |
|Approve proposal |    |   |   | `Compactu32` proposal_id <br/> |

## Democracy

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Propose |    |   |   | `Hash` proposal_hash <br/>`CompactBalance` amount <br/> |
|Second |    |   |   | `Compactu32` proposal <br/>`Compactu32` seconds_upper_bound <br/> |
|Vote |    |   |   | `Compactu32` ref_index <br/>`AccountVote` vote <br/> |
|Emergency cancel |    |   |   | `ReferendumIndex` ref_index <br/> |
|External propose |    |   |   | `Hash` proposal_hash <br/> |
|External propose majority |    |   |   | `Hash` proposal_hash <br/> |
|External propose default |    |   |   | `Hash` proposal_hash <br/> |
|Fast track |    |   |   | `Hash` proposal_hash <br/>`BlockNumber` voting_period <br/>`BlockNumber` delay <br/> |
|Veto external |    |   |   | `Hash` proposal_hash <br/> |
|Cancel referendum |    |   |   | `Compactu32` ref_index <br/> |
|Cancel queued |    |   |   | `ReferendumIndex` which <br/> |
|Delegate |    |   |   | `AccountId` to <br/>`Conviction` conviction <br/>`Balance` balance <br/> |
|Undelegate |    |   |   |  |
|Clear public proposals |    |   |   |  |
|Note preimage |    |   |   | `Bytes` encoded_proposal <br/> |
|Note preimage operational |    |   |   | `Bytes` encoded_proposal <br/> |
|Note imminent preimage |    |   |   | `Bytes` encoded_proposal <br/> |
|Note imminent preimage operational |    |   |   | `Bytes` encoded_proposal <br/> |
|Reap preimage |    |   |   | `Hash` proposal_hash <br/>`Compactu32` proposal_len_upper_bound <br/> |
|Unlock |    |   |   | `AccountId` target <br/> |
|Remove vote |    |   |   | `ReferendumIndex` index <br/> |
|Remove other vote |    |   |   | `AccountId` target <br/>`ReferendumIndex` index <br/> |
|Enact proposal |    |   |   | `Hash` proposal_hash <br/>`ReferendumIndex` index <br/> |
|Blacklist |    |   |   | `Hash` proposal_hash <br/>`OptionReferendumIndex` maybe_ref_index <br/> |
|Cancel proposal |    |   |   | `Compactu32` prop_index <br/> |

## Scheduler

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Schedule |    |   |   | `BlockNumber` when <br/>`OptionschedulePeriodBlockNumber` maybe_periodic <br/>`schedulePriority` priority <br/>`BoxCallOrHashOfT` call <br/> |
|Cancel |    |   |   | `BlockNumber` when <br/>`u32` index <br/> |
|Schedule named |    |   |   | `Vecu8` id <br/>`BlockNumber` when <br/>`OptionschedulePeriodBlockNumber` maybe_periodic <br/>`schedulePriority` priority <br/>`BoxCallOrHashOfT` call <br/> |
|Cancel named |    |   |   | `Vecu8` id <br/> |
|Schedule after |    |   |   | `BlockNumber` after <br/>`OptionschedulePeriodBlockNumber` maybe_periodic <br/>`schedulePriority` priority <br/>`BoxCallOrHashOfT` call <br/> |
|Schedule named after |    |   |   | `Vecu8` id <br/>`BlockNumber` after <br/>`OptionschedulePeriodBlockNumber` maybe_periodic <br/>`schedulePriority` priority <br/>`BoxCallOrHashOfT` call <br/> |

## Utility

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Batch |    |   |   | `VecCall` calls <br/> |
|As derivative |    |   |   | `u16` index <br/>`Call` call <br/> |
|Batch all |    |   |   | `VecCall` calls <br/> |
|Dispatch as |    |   |   | `BoxPalletsOrigin` as_origin <br/>`Call` call <br/> |

## Preimage

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Note preimage |    |   |   | `Vecu8` bytes <br/> |
|Unnote preimage |    |   |   | `Hash` hash <br/> |
|Request preimage |    |   |   | `Hash` hash <br/> |
|Unrequest preimage |    |   |   | `Hash` hash <br/> |

## XcmpQueue

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Service overweight |    |   |   | `OverweightIndex` index <br/>`Weight` weight_limit <br/> |
|Suspend xcm execution |    |   |   |  |
|Resume xcm execution |    |   |   |  |
|Update suspend threshold |    |   |   | `u32` new_ <br/> |
|Update drop threshold |    |   |   | `u32` new_ <br/> |
|Update resume threshold |    |   |   | `u32` new_ <br/> |
|Update threshold weight |    |   |   | `Weight` new_ <br/> |
|Update weight restrict decay |    |   |   | `Weight` new_ <br/> |
|Update xcmp max individual weight |    |   |   | `Weight` new_ <br/> |

## RelayerXcm

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Send |    |   |   | `BoxVersionedMultiLocation` dest <br/>`BoxVersionedXcmTuple` message <br/> |
|Teleport assets |    |   |   | `BoxVersionedMultiLocation` dest <br/>`BoxVersionedMultiLocation` beneficiary <br/>`BoxVersionedMultiAssets` assets <br/>`u32` fee_asset_item <br/> |
|Reserve transfer assets |    |   |   | `BoxVersionedMultiLocation` dest <br/>`BoxVersionedMultiLocation` beneficiary <br/>`BoxVersionedMultiAssets` assets <br/>`u32` fee_asset_item <br/> |
|Execute |    |   |   | `BoxVersionedXcmTasSysConfigCall` message <br/>`Weight` max_weight <br/> |
|Force xcm version |    |   |   | `BoxMultiLocation` location <br/>`XcmVersion` xcm_version <br/> |
|Force default xcm version |    |   |   | `OptionXcmVersion` maybe_xcm_version <br/> |
|Force subscribe version notify |    |   |   | `BoxVersionedMultiLocation` location <br/> |
|Force unsubscribe version notify |    |   |   | `BoxVersionedMultiLocation` location <br/> |
|Limited reserve transfer assets |    |   |   | `BoxVersionedMultiLocation` dest <br/>`BoxVersionedMultiLocation` beneficiary <br/>`BoxVersionedMultiAssets` assets <br/>`u32` fee_asset_item <br/>`WeightLimit` weight_limit <br/> |
|Limited teleport assets |    |   |   | `BoxVersionedMultiLocation` dest <br/>`BoxVersionedMultiLocation` beneficiary <br/>`BoxVersionedMultiAssets` assets <br/>`u32` fee_asset_item <br/>`WeightLimit` weight_limit <br/> |

## CumulusXcm

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|

## DmpQueue

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Service overweight |    |   |   | `OverweightIndex` index <br/>`Weight` weight_limit <br/> |

## Tokens

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Transfer |    |   |   | `LookupasStaticLookupSource` dest <br/>`CurrencyId` currency_id <br/>`Compactu128` amount <br/> |
|Transfer all |    |   |   | `LookupasStaticLookupSource` dest <br/>`CurrencyId` currency_id <br/>`bool` keep_alive <br/> |
|Transfer keep alive |    |   |   | `LookupasStaticLookupSource` dest <br/>`CurrencyId` currency_id <br/>`Compactu128` amount <br/> |
|Force transfer |    |   |   | `LookupasStaticLookupSource` source <br/>`LookupasStaticLookupSource` dest <br/>`CurrencyId` currency_id <br/>`Compactu128` amount <br/> |
|Set balance |    |   |   | `LookupasStaticLookupSource` who <br/>`CurrencyId` currency_id <br/>`Compactu128` new_free <br/>`Compactu128` new_reserved <br/> |

## CrowdloanRewards

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Initialize |    |   |   |  |
|Initialize at |    |   |   | `Moment` at <br/> |
|Populate |    |   |   | `VecTupleRemoteAccountOfTRewardAmountOfTVestingPeriodOfT` rewards <br/> |
|Associate |    |   |   | `AccountId` reward_account <br/>`ProofOfT` proof <br/> |
|Claim |    |   |   |  |

## Assets

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Transfer |    |   |   | `AssetId` asset <br/>`LookupasStaticLookupSource` dest <br/>`Compactu128` amount <br/>`bool` keep_alive <br/> |
|Transfer native |    |   |   | `LookupasStaticLookupSource` dest <br/>`Compactu128` amount <br/>`bool` keep_alive <br/> |
|Force transfer |    |   |   | `AssetId` asset <br/>`LookupasStaticLookupSource` source <br/>`LookupasStaticLookupSource` dest <br/>`Compactu128` amount <br/>`bool` keep_alive <br/> |
|Force transfer native |    |   |   | `LookupasStaticLookupSource` source <br/>`LookupasStaticLookupSource` dest <br/>`Compactu128` amount <br/>`bool` keep_alive <br/> |
|Transfer all |    |   |   | `AssetId` asset <br/>`LookupasStaticLookupSource` dest <br/>`bool` keep_alive <br/> |
|Transfer all native |    |   |   | `LookupasStaticLookupSource` dest <br/>`bool` keep_alive <br/> |
|Mint initialize |    |   |   | `Compactu128` amount <br/>`LookupasStaticLookupSource` dest <br/> |
|Mint initialize with governance |    |   |   | `Compactu128` amount <br/>`LookupasStaticLookupSource` governance_origin <br/>`LookupasStaticLookupSource` dest <br/> |
|Mint into |    |   |   | `AssetId` asset_id <br/>`LookupasStaticLookupSource` dest <br/>`Compactu128` amount <br/> |
|Burn from |    |   |   | `AssetId` asset_id <br/>`LookupasStaticLookupSource` dest <br/>`Compactu128` amount <br/> |

## GovernanceRegistry

| Name        | Light | XL | Nesting | Arguments |
| :---------- |:------------:|:--------:|:--------:|:--------|
|Set |    |   |   | `AssetId` asset_id <br/>`AccountId` value <br/> |
|Grant root |    |   |   | `AssetId` asset_id <br/> |
|Remove |    |   |   | `AssetId` asset_id <br/> |

