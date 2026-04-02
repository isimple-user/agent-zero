FROM ghcr.io/isimple-user/agent-zero:2026-04-02-v1.6-clean

RUN apt-get update \
 && apt-get install -y --no-install-recommends nodejs npm \
 && npm install -g @openai/codex \
 && npm cache clean --force \
 && rm -rf /var/lib/apt/lists/*

RUN cat > /usr/local/bin/codex-login <<'SH'
#!/usr/bin/env sh
set -eu
export HOME=/a0/usr/codex-home
mkdir -p "$HOME/.codex"
exec codex --login "$@"
SH
chmod +x /usr/local/bin/codex-login

RUN cat > /usr/local/bin/codex-mcp-server <<'SH'
#!/usr/bin/env sh
set -eu
export HOME=/a0/usr/codex-home
mkdir -p "$HOME/.codex"
exec codex mcp-server "$@"
SH
chmod +x /usr/local/bin/codex-mcp-server
