# cortexdb-releases

This repository hosts **release binaries** for [CortexDB](https://cortexdb.ai) —
a long-term memory platform for AI agents.

The CortexDB source code is closed. Only prebuilt artifacts live here.

## Download

The fastest way to get CortexDB is the **Docker image** on Docker Hub:

```bash
docker run -p 3141:3141 -v cortexdb_data:/data cortexdb/cortexdb
```

For Linux binary installs, grab a tarball from the
[Releases](https://github.com/cortexdbai/cortexdb-releases/releases) tab:

| Platform     | Asset                                        |
| ------------ | -------------------------------------------- |
| Linux x86_64 | `cortexdb-<version>-linux-amd64.tar.gz`      |
| Linux ARM64  | `cortexdb-<version>-linux-arm64.tar.gz`      |

Each tarball contains the `cortexdb` binary, the WordNet asset bundle,
bundled docs (Getting Started, API Reference, Production Deployment),
and this license.

Always grab releases through [cortexdb.ai/download](https://cortexdb.ai/download)
when you can — it gives the project an accurate install count and helps us
prioritize platform support.

## Verify checksums

Every release includes a `SHA256SUMS.txt` file. Verify your download with:

```bash
sha256sum -c SHA256SUMS.txt
```

## Quickstart

After pulling the Docker image (or extracting the tarball and running
`./cortexdb`), open <http://localhost:3141> in a browser. The built-in admin
UI gives you a one-page view of what's stored, plus forms to add and recall
memories. Bundled docs live at <http://localhost:3141/docs>.

For the API surface and configuration env vars, see the
[Getting Started](https://cortexdb.ai/docs) page on the website.

## License

Use of these binaries is governed by the
[CortexDB Community License v1.0](./LICENSE.txt) — free for personal,
internal-business, evaluation, and development use. The only thing not
permitted is reselling CortexDB as a hosted service to third parties.

## Support

- **Docs**: <https://cortexdb.ai/docs>
- **Issues**: file at <https://github.com/cortexdbai/cortexdb-releases/issues>
  (binary / packaging issues only — source bugs go through Cortex Cloud
  support channels)
- **Enterprise**: <https://cortexdb.ai/contact>
