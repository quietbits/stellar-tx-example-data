# Stellar Transaction Response Examples

## Example data

- Aqua AMM ([CBQDH…C6QUK](https://stellar.expert/explorer/public/contract/CBQDHNBFBZYE4MKPWBSJOPIYLW4SFSXAXUTSXJN76GNKYVYPCKWC6QUK))
  - [Swap](./data/swap.json)
  - [Swap Strict Receive](./data/swap-strict-receive.json)

- Blend USDC-XLM Pool ([CDVQV…DX6DP](https://stellar.expert/explorer/public/contract/CDVQVKOY2YSXS2IC7KN6MNASSHPAO7UN2UR2ON4OI2SKMFJNVAMDX6DP))
  - [Pool Submit](./data/pool-submit.json) (fee bump)
  - [Pool Claim](./data/pool-claim.json)

- Soroban Domains ([CATRN…2UMKI](https://stellar.expert/explorer/public/contract/CATRNPHYKNXAPNLHEYH55REB6YSAJLGCPA4YM6L3WUKSZOPI77M2UMKI))
    - [Domain Set Record](./data/domain-set-record.json)

- Soroswap ([CA4HE…Z7AW2](https://stellar.expert/explorer/public/contract/CA4HEQTL2WPEUYKYKCDOHCDNIV4QHNJ7EL4J4NQ6VADP7SYHVRYZ7AW2))
    - [Add Liquidity](./data/liquidity-add.json)
    - [Remove Liquidity](./data/liquidity-remove.json)

- Band Protocol ([CCQXW…BGG5M](https://stellar.expert/explorer/public/contract/CCQXWMZVM3KRTXTUPTN53YHL272QGKF32L7XEDNZ2S6OSUFK3NFBGG5M))
    - [Relay](./data/relay.json)

- Reflector ([CAFJZ…34DLN](https://stellar.expert/explorer/public/contract/CAFJZQWSED6YAWZU3GWRTOCNPPCGBN32L7QV43XX5LZLFTK6JLN34DLN))
    - [Set Price](./data/reflector-set-price.json)
    - [Submit](./data/reflector-submit.json)

- XLM SAC ([CAS3J…XOWMA](https://stellar.expert/explorer/public/contract/CAS3J7GYLGXMF6TDJBBYYSE3HQ6BBSMLNUQ34T6TZMYMW2EVH34XOWMA))
    - [Asset S](data/asset-s.json) (fee bump)
    - [Asset Yeet](./data/asset-yeet.json)
    - [Asset Swap](./data/asset-swap.json)
    - [Asset Submit](./data/asset-submit.json)

## Data Structure

`resultMetaJson` > `v3` > `operations`

### `LedgerEntryChangeType`

- [Stellar XDR definition](https://github.com/stellar/stellar-xdr/blob/4b7a2ef7931ab2ca2499be68d849f38190b443ca/Stellar-ledger.x#L328:L340)

```
union LedgerEntryChange switch (LedgerEntryChangeType type)
{
case LEDGER_ENTRY_CREATED:
    LedgerEntry created;
case LEDGER_ENTRY_UPDATED:
    LedgerEntry updated;
case LEDGER_ENTRY_REMOVED:
    LedgerKey removed;
case LEDGER_ENTRY_STATE:
    LedgerEntry state;
case LEDGER_ENTRY_RESTORED:
    LedgerEntry restored;
};
```  
### `LedgerEntryType`

- [Stellar XDR definition](https://github.com/stellar/stellar-xdr/blob/4b7a2ef7931ab2ca2499be68d849f38190b443ca/Stellar-ledger-entries.x#L92:L104)
- [LedgerEntry definition](https://github.com/stellar/stellar-xdr/blob/4b7a2ef7931ab2ca2499be68d849f38190b443ca/Stellar-ledger-entries.x#L548:L586)

```
enum LedgerEntryType
{
    ACCOUNT = 0,
    TRUSTLINE = 1,
    OFFER = 2,
    DATA = 3,
    CLAIMABLE_BALANCE = 4,
    LIQUIDITY_POOL = 5,
    CONTRACT_DATA = 6,
    CONTRACT_CODE = 7,
    CONFIG_SETTING = 8,
    TTL = 9
};
```

#### ACCOUNT

- `account_id`
- `balance`
- `seq_num`
- `num_sub_entries`
- `inflation_dest`
- `flags`
- `home_domain`
- `thresholds`
- `signers`

#### TRUSTLINE

- `account_id`
- `asset`
- `balance`
- `limit`
- `flags`

#### OFFER
- `seller_id`
- `offer_id`
- `selling`
- `buying`
- `amount`
- `price`
- `flags`

#### DATA

- `account_id`
- `data_name`
- `data_value`

#### CLAIMABLE_BALANCE

- `balance_id`
- `claimants`
- `asset`
- `amount`

#### LIQUIDITY_POOL

- `liquidity_pool_id`
- `body`

#### CONTRACT_DATA

- `contract`
- `key`
- `durability`
- `val`

#### CONTRACT_CODE

- `hash`
- `code`

#### CONFIG_SETTING

#### TTL

- `key_ash`
- `live_until_ledger_seq`
