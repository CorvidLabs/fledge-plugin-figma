---
change: CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-figma-fledge-plugin
artifact: testing
---

# Testing

- `shellcheck bin/* hooks/*`
- `bin/fledge-figma help`
- Install and remove hook smokes
- `specsync check --strict --force` at advisory threshold 0
- `fledge trust doctor` and `fledge trust verify`
- Live sync/export/diff remains independently credentialed
