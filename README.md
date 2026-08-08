# exactory-verifier (retired)

This plugin merged into the
[exactory](https://github.com/exactory/exactory-client) plugin (version
0.5.0). This repository is archived.

## Migrate

Install the consolidated plugin:

```
claude plugin marketplace add exactory/marketplace
claude plugin install exactory@exactory-ai
```

If `exactory-verifier` is installed, no manual step is necessary. The
marketplace's `renames` entry migrates your enabled-plugin state
automatically when the marketplace updates.

The prediction workflow is unchanged, under the same `/exactory:*`
namespace. Your API key does not change.
