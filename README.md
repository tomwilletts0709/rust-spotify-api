# rust-spotify

A Rust CLI for searching tracks on the Spotify Web API.

## Prerequisites

- [Rust](https://www.rust-lang.org/) (1.70+)
- A Spotify account

## Setup

```bash
cargo build
```

## Spotify API Authentication

You need an OAuth token to call the Spotify API. Options:

1. **Spotify Developer Dashboard** — Create an app at [developer.spotify.com](https://developer.spotify.com/dashboard) and use the Client Credentials flow for server-to-server requests.
2. **Get a token manually** — Use Spotify’s [Client Credentials flow](https://developer.spotify.com/documentation/web-api/concepts/authorization#client-credentials-flow) to obtain an access token.

## Usage

```bash
cargo run -- "<search query>" "<your_spotify_auth_token>"
```

Example:

```bash
cargo run -- "bohemian rhapsody" "BQC..."
```

## Project structure

- `src/main.rs` — CLI entrypoint, search query parsing, and Spotify API models for tracks, albums, and artists.

## License

MIT
