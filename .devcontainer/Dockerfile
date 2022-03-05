FROM --platform=linux/amd64 mcr.microsoft.com/vscode/devcontainers/base:0-hirsute

RUN  --mount=type=cache,target=/var/cache/apt \
    apt-get update && \
    apt-get install -y bzip2 curl

# Install Solana
ARG SOLANA_VERSION=v1.10.0
RUN curl -sSL "https://github.com/solana-labs/solana/releases/download/$SOLANA_VERSION/solana-release-x86_64-unknown-linux-gnu.tar.bz2" \
    | tar xj -C "/usr/local"
ENV PATH="/usr/local/solana-release/bin:$PATH"

# Install Rust
ENV RUSTUP_HOME=/opt/rust
ENV CARGO_HOME=/opt/rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --no-modify-path
ENV PATH="/opt/rust/bin:$PATH"
