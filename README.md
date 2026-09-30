# iperf3 Windows Builds

Unofficial automated **Windows x86_64** builds of [ESnet iperf3](https://github.com/esnet/iperf).

This repository tracks **only the latest upstream ESnet release**. Historical versions are not backfilled.

## How it works

GitHub Actions checks the upstream `esnet/iperf` latest release every 6 hours.

When a new upstream version appears, the workflow:

1. Downloads the official source tarball and SHA256 from ESnet.
2. Verifies the source archive before building.
3. Builds iperf3 on a GitHub-hosted Windows runner using Cygwin x86_64.
4. Adds a Windows build timestamp to `iperf3 -v`.
5. Runs version, parallel TCP, JSON output, and reverse TCP tests.
6. Packages the executable with the required Cygwin runtime DLL, licence, and README.
7. Publishes a GitHub Release tagged `windows-<upstream-version>`.

## Version information

A packaged build reports both the upstream iperf version and this repository's Windows build timestamp, for example:

```text
iperf 3.22 (cJSON 1.7.15)
Windows build: 2026-09-30 HH:MM:SS UTC
CYGWIN_NT-...
Optional features available: ...
```

The date shown on the `CYGWIN_NT` line belongs to the Cygwin runtime and is separate from both the upstream iperf release date and this Windows package build date.

## Support status

iperf3 is developed by ESnet / Lawrence Berkeley National Laboratory.

Windows is not an officially supported iperf3 platform. These are independent community builds and are not produced or endorsed by ESnet or Lawrence Berkeley National Laboratory.

## Source and licensing

No functional changes are made to iperf3 beyond adding the clearly labelled Windows build timestamp to version output.

Upstream source: https://github.com/esnet/iperf

Official source distributions: https://downloads.es.net/pub/iperf/

iperf3 is distributed under the BSD 3-Clause licence. The upstream licence is included in each Windows release package.

## Contributors

- Hasan Tan. Repository owner and maintainer.
- ChatGPT (OpenAI). Workflow design, CI troubleshooting, release automation, and build validation assistance.
