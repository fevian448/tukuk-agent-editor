# Tukuk Agent

**Tukuk Agent** is the Tukuk OS editor/agent workspace. It runs a full
[VS Code](https://github.com/Microsoft/vscode) session on your own self-hosted
server and serves it to any browser — the same machine that hosts the Tukuk OS
store, search engine and chat can now host your dev environment too.

It is a rebranded, Tukuk-flavoured distribution of
[code-server](https://github.com/coder/code-server) (MIT), tuned to fit the
Tukuk OS ecosystem.

## Highlights

- Code on any device with a consistent Tukuk-hosted development environment
- Use your own server to speed up tests, compilations, downloads, and more
- Preserve battery life on the go; all intensive tasks run on your server
- Ships with the Tukuk OS visual identity (brand, icons, config paths)

## Requirements

A Linux machine with WebSockets enabled, ~1 GB RAM, and 2 vCPUs is enough for a
single-user Tukuk Agent. Node 24 is required to run from source.

## Getting started

From a checkout of this repo:

```bash
npm ci
npm run build      # bundles the VS Code + Tukuk Agent server
./release-standalone/bin/tukuk-agent
```

Then open the printed URL (default `http://127.0.0.1:8080`) and log in with the
auto-generated password found in `~/.config/tukuk-agent/config.yaml`.

The CLI is available as `tukuk-agent`:

```bash
tukuk-agent --help
tukuk-agent ./path/to/your/project
```

### Configuration

Tukuk Agent stores its state under the `tukuk-agent` XDG paths, not the
upstream ones:

| Purpose | Path |
| --- | --- |
| Config file | `~/.config/tukuk-agent/config.yaml` |
| User data / session socket | `~/.local/share/tukuk-agent/` |
| Logs | `~/.local/share/tukuk-agent/tukuk-agent-logs/` |

The app name shown in the browser title, login screen and PWA manifest defaults
to **Tukuk Agent**; override it with `TUKUK_AGENT_APP_NAME` or `--app-name`.

## Building on Tukuk OS

Tukuk Agent is designed to sit beside the rest of Tukuk OS (`src/server.js`,
the store, chat WebSocket and SMS gateway). Because it is a self-contained Node
service, you can front it with the existing Cloudflare tunnel and reach it at a
path on `tukuk.org`.

## License

MIT. Tukuk Agent is derived from [code-server](https://github.com/coder/code-server)
by Coder Technologies, Inc., also MIT-licensed. The original
[LICENSE](../LICENSE) and copyright notices are retained; see
[ThirdPartyNotices.txt](../ThirdPartyNotices.txt).
