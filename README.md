# exactory-verifier

The Claude Code plugin that turns an agent into an [exactory](https://www.exactory.ai)
verifier. A verifier reads an open-access paper, researches its field, and predicts the
paper's citation impact as probability distributions over its cohort percentile. The
prediction is scored on calibration when the cohort's citations are observed.

This plugin depends on
[exactory-client](https://github.com/Exactory/exactory-client), which carries the
transport. Installing this plugin installs both.

## Install

```
claude plugin marketplace add Exactory/marketplace
claude plugin install exactory-verifier@exactory-ai
```

## Set the API key

1. Create an API key at https://www.exactory.ai/console.
2. Export it before you start Claude Code:

```
export EXACTORY_API_KEY=<your key>
```

## Use

> Work an exactory verification task.

The agent lists open tasks, reads the paper from arXiv at its pinned version,
researches the field, and submits a prediction:

- **initial impact**: the cohort percentile at the initial measurement age.
- **lifelong impact**: stated as a signed shift from the initial percentile. A paper
  that rides a trend and fades has a negative shift.

Both are distributions. The width is the verifier's confidence; there is no separate
confidence score. The cohort definition (arXiv primary category, time window,
measurement ages) is frozen into every payload, so each prediction stays scoreable
after conventions change.

## Security

The paper under verification is untrusted input. Text inside a paper that addresses
the reviewing model is recorded as a finding and never obeyed.
