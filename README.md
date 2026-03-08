# rust-spotify

A Rust CLI for searching tracks on the Spotify Web API.

## Current status

- **Working:** Track search via Spotify Search API; prints track name, artist(s), and Spotify URL for up to 50 results
- **Stack:** reqwest 0.11, tokio, serde (edition 2021)
- **Auth:** Manual token passed as CLI argument
- **Scope:** Single-file implementation (`main.rs`)

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

## Learnings (from this build)

- **Types & macros matter:** `Vec` vs `vec`, `println!` vs `println` — Rust enforces these to catch real bugs.
- **Scope & ownership:** Code like `track.external_urls` must live inside the loop that owns `track`; the borrow checker pushes you toward correct structure.
- **Dependency alignment:** Matching crate versions (reqwest 0.11, edition 2021) and required features (`json`) avoids subtle failures.
- **Derive macros:** Structs need `#[derive(Serialize, Deserialize)]` for serde to work; the compiler tells you what’s missing.
- **Small syntax gotchas:** `env::args()` not `env.args()`, correct `format!` args, no duplicate `.get()` calls — building a mental checklist speeds debugging.

## Next steps

- [ ] URL-encode search queries for special characters
- [ ] Add config file or env vars instead of CLI token
- [ ] Support search types: artist, album, playlist (not just track)
- [ ] Implement Client Credentials flow for automatic token fetch
- [ ] Add `clap` for subcommands and better CLI structure
- [ ] Split into modules: `api.rs`, `models.rs`, `auth.rs`
- [ ] Improve error handling with `Result` / `?` and `anyhow`
- [ ] Pagination for results beyond 50
- [ ] Richer output (duration, preview URL, album art)

## Project structure

- `src/main.rs` — CLI entrypoint, search logic, and Spotify API models for tracks, albums, and artists.

## License

MIT
