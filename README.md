# NTWR Signal Wall · 159680.SZ

Public, **paper-only** daily-signal dashboard for the 159680.SZ NTWR-A strategy (2% initial allocation).

- [Dashboard](https://zhangzihaodt.github.io/ntwr-signal-wall/) (available after GitHub Pages is enabled)
- One card per completed, validated market session; BUY / SELL / HOLD are historical simulated signals, not live orders.
- Source calculation and data gates remain in the private `grid-trading` repository. This site contains only published card data.

The dashboard is static: `index.html` and `signals.json`, published via GitHub Pages from a public repository. The private CI will update the sanitized feed with a scoped deploy credential.

**Important:** simulated quantities are not personal investment advice. Past signals cannot be treated as current execution instructions.

## One-time GitHub setup

1. **Publish this public site:** open [this repository's Pages settings](https://github.com/zhangzihaoDT/ntwr-signal-wall/settings/pages), choose **Build and deployment → Source: GitHub Actions**, then use [Publish NTWR Signal Wall](https://github.com/zhangzihaoDT/ntwr-signal-wall/actions/workflows/pages.yml) → **Run workflow**. The dashboard address is https://zhangzihaodt.github.io/ntwr-signal-wall/.
2. **Enable unattended daily synchronization:** create a GitHub **fine-grained personal access token** restricted to repository `zhangzihaoDT/ntwr-signal-wall` with **Contents: Read and write** (the required Metadata read-only permission is automatic). Save it in **the PRIVATE repository** `zhangzihaoDT/grid-trading` at **Settings → Secrets and variables → Actions → New repository secret**, with name `SIGNAL_WALL_PUBLISH_TOKEN`. Never store the token in code or on this public repository.
3. Run [the private Signal Wall workflow](https://github.com/zhangzihaoDT/grid-trading/actions/workflows/ntwr-a-signal-wall.yml) once with the `dates` input left empty; it will sync the currently validated feed to this public repository. After that, the private daily-signal workflow automatically invokes the aggregation whenever a genuine production daily run succeeds.

The public repository intentionally contains **no strategy source code, trading account data, private market files, or credentials**. Only display-ready, simulated BUY/SELL/HOLD cards are published. Dates are unique, historical records are not silently overwritten, and missing or blocked daily data never creates a signal card.
