# DNSSEC Steward

Unattended DNSSEC on disposable Linux VMs, run across geo-dispersed Mac minis.

**The storyboard:** [zone-reg.com](https://zone-reg.com) tells the whole story as an A0 engineering board: the threat, the adoption data, the root cause, the design, the measured results (live), the risks met and the standards they became.

## Why there are no release files yet

DNSSEC Steward is one end-to-end workflow, not a set of independent modules. The signer, the secondaries, the registrar, the standby and the control plane only work safely together. A part released on its own, or a whole that has not been proven end to end, risks the one failure DNSSEC does not forgive: domains that disappear.

So release 1.0 waits for the whole workflow to be proven from a clean install, under regression testing. The ten gates are in [`release.json`](release.json); each is ticked by a commit when it passes, so this repository's history is the record. The board at [zone-reg.com](https://zone-reg.com) reads the same file live (panel 10).

| # | Gate | Passing means |
|---|---|---|
| 1 | Failover drill | Forced promotion and rejoin pass, with the time to signing measured |
| 2 | Failback | Signing returns home through the normal, receipt-based handoff |
| 3 | Open items closed | Build queue uniqueness rule aligned; the two readiness copies reconciled |
| 4 | Steward installer | A Steward builds from the image on a clean node, on either CPU architecture |
| 5 | Site data separated from code | Addresses, credentials and registrar settings are configuration |
| 6 | Clean-room install | A fresh lab cluster, built only from the repository, signs a test zone end to end |
| 7 | Full regression on the lab | Build, join, swap, unpublish, rollover, handoff, failover, rejoin and failback in one run |
| 8 | Documentation | Install, operate, recover, and the architecture |
| 9 | Security and licence review | No secrets in the history, dependencies pinned, licence chosen |
| 10 | Tag 1.0 | Signed release files with checksums |

## Comments

Each A3 sheet on the board has its own thread, kept here in [Discussions](https://github.com/DarthCruiser/dnssec-steward/discussions).

Zone Reg, domains and DNS since 2005.
