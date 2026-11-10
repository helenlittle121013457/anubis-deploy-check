# anubis-deploy-check

Bytecode hash checker for the Safe v1.5.0 suite deployed on Anubis (chain 6714).

## Why

`anubis-chain/safe-smart-account` publishes
`deployment/safe-v1.5.0-production-chain-6714.json` with the per-contract
addresses and `verification/verify_runtime_match.py` computes the runtime hash
for each. We replicate that check in our own pipeline and get a different value
for the `SafeL2` singleton than the one recorded at deploy time.

## Run

```bash
npm install      # quiet
npm run check    # prints local vs expected
```

```
local   : 3f2a91c4
expected: bb6bb4139d5997f4151888fa7ecc6bfa
match   : NO - see README
```

## Layout

| path | purpose |
|---|---|
| `scripts/check.js` | loads the fixtures and compares |
| `vectors/safe-v150.json` | expected runtime shards (hex) |
| `vectors/safe-l2.json` | observed runtime shards (hex) |
