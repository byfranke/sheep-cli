# Sheep CLI

Autonomous CLI agent for Cyber Threat Intelligence, powered by the [Sheep API](https://sheep.byfranke.com).

Threat intelligence, IOC enrichment, MITRE ATT&CK grounding and an interactive REPL with structured outputs (JSON, PDF, STIX 2.1) — all from your terminal.

<img width="1102" height="580" alt="{2B7BA402-46F2-4CFE-9FC5-EE842C9E0BBD}" src="https://github.com/user-attachments/assets/68b31fc7-ff3e-4e7f-8d07-99ee9de4f4d6" />


## Install

### Linux / macOS

```bash
curl -fsSL https://sheep.byfranke.com/install.sh | bash
```

### Windows (PowerShell)

```powershell
iwr https://sheep.byfranke.com/install.ps1 -UseBasicParsing | iex
```

The installer detects your platform, downloads the matching binary from the latest release, verifies its SHA-256 against the published `SHA256SUMS`, and installs to `/usr/local/bin/sheep-cli` (Linux/macOS) or `%LOCALAPPDATA%\Programs\sheep-cli` (Windows).

### Pin a specific version

```bash
curl -fsSL https://sheep.byfranke.com/install.sh | SHEEP_CLI_VERSION=v1.2.0 bash
```

### Manual download

Each [Release](https://github.com/byfranke/sheep-cli/releases) ships five binaries plus `SHA256SUMS`:

| Platform | Binary |
|---|---|
| Linux x86_64 | `sheep-cli-linux-x64` |
| Linux aarch64 | `sheep-cli-linux-arm64` |
| macOS Intel | `sheep-cli-macos-x64` |
| macOS Apple Silicon | `sheep-cli-macos-arm64` |
| Windows x64 | `sheep-cli-windows-x64.exe` |

Verify before running:

```bash
sha256sum -c SHA256SUMS
```

## Usage

```bash
# 1. Save your Sheep API token (one time)
sheep-cli token

# 2. Launch the interactive REPL
sheep-cli

# 3. One-shot question (for scripts)
sheep-cli ask "what is APT28's most recent campaign?"

# 4. IOC analysis (IP / hash / domain / URL / CVE)
sheep-cli analyze 1.2.3.4
sheep-cli analyze 44d886... --json
sheep-cli analyze CVE-2024-1234 --report report.pdf

# 5. All commands
sheep-cli --help
```

## Features

- **Interactive REPL** with persistent session history (the API is stateless; the CLI remembers locally)
- **Priority Intelligence Requirements (PIR)** — `/pir` persists your CTI coverage profile (sectors, regions, threat actors, MITRE techniques, notes) and injects it into every `/ask` so the model prioritises information matching your scope
- **Session resume** — `--resume` brings any past session back
- **Model tier selection** — `/model auto|scout|hunter|sage`
- **Structured output** — `--json` for pipelines, `--report` for PDF, `--stix` for STIX 2.1 Bundle (MISP / OpenCTI / TheHive)
- **Threat-intel feeds** read-only via `/feeds` (does not consume tokens)
- **Security auditing** of local code via `/audit`
- **Plan / quota visibility** via `/profile`

## Get a token

Get an API token at [sheep.byfranke.com/pages/store](https://sheep.byfranke.com/pages/store).

Trial (free, 3 days) and paid plans (Sheep Plus, Sheep Pro, Sheep Pro Max, Black Sheep gift cards) all use the same CLI.

## Support

- Documentation: [sheep.byfranke.com/pages/api](https://sheep.byfranke.com/pages/api)
- Discord: [sheep.byfranke.com/discord](https://sheep.byfranke.com/discord)
- Issues: [github.com/byfranke/sheep-cli/issues](https://github.com/byfranke/sheep-cli/issues)
- Commercial / security: [byfranke.com/#Contact](https://byfranke.com/#Contact)

## License

[byFranke License](LICENSE) — proprietary, with use granted for personal and commercial purposes. Redistribution requires prior written consent. See the [Sheep Terms of Service](https://sheep.byfranke.com/pages/terms) and [Privacy Policy](https://sheep.byfranke.com/pages/privacy).
