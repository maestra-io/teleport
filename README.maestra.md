# maestra-io/teleport

Fork of [gravitational/teleport](https://github.com/gravitational/teleport) that builds the Teleport auth image for us-iota (issues-maestra#1632). `main` is upstream `branch/v18` plus the `eng/maestra` directory; nothing else in this tree is modified or built.

- The image is built from a FRESH upstream checkout at the tag in `eng/maestra/UPSTREAM_VERSION`, with `eng/maestra/patches/*.patch` applied on top. See [eng/maestra/README.md](eng/maestra/README.md) and [eng/maestra/PATCHES.md](eng/maestra/PATCHES.md).
- Renovate bumps `UPSTREAM_VERSION` and the distroless base digest together; CI fails if they disagree. An open Renovate PR is the "we are behind" signal.
- Sync with upstream: `git fetch upstream && git merge upstream/branch/v18` (upstream commits never touch `eng/maestra`). Upstream's 49 workflows are disabled in this repository; disable a new one after a sync with `gh workflow disable`.
- Image: `public.ecr.aws/g5f9s8a4/teleport-maestra:<version>-maestra.<run>` (plus moving `18`), pinned by digest in maestra-io/fluxcd.
