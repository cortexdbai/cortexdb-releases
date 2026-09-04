# cortexdb-releases

This repository hosts **release binaries** for [CortexDB](https://cortexdb.ai) —
a long-term memory platform for AI agents.

The CortexDB source code is closed. Only prebuilt artifacts live here.

## Download

The fastest way to get CortexDB is the **Docker image** on Docker Hub. The
published image uses OpenAI embeddings by default, so configure an embedding
credential and a strong, stable CortexDB bearer before starting it:

```bash
export OPENAI_API_KEY="..."
export CORTEX_API_KEY="$(openssl rand -hex 32)"

docker run -d \
  --name cortexdb \
  -p 127.0.0.1:3141:3141 \
  -v cortexdb_data:/data \
  -e OPENAI_API_KEY \
  -e CORTEX_API_KEY \
  cortexdb/cortexdb:latest
```

The loopback bind keeps the service local to the host. Data and administrative
operations require `Authorization: Bearer <token>` using the configured
`CORTEX_API_KEY`; liveness and readiness probes remain public. The image fails
closed when its configured remote embedding provider lacks a usable key. See
the [deployment documentation](https://cortexdb.ai/docs) before exposing the
service beyond localhost or selecting another embedding provider.

For a v0.9.10 binary install, grab a tarball from the
[Releases](https://github.com/cortexdbai/cortexdb-releases/releases) tab. These
tarballs require an Ubuntu 24.04-class userspace: glibc 2.39 and OpenSSL 3.
Use the Docker image when the host does not meet that runtime floor; the image
carries its required userspace.

| Architecture | Required userspace                         | Asset                                   |
| ------------ | ------------------------------------------ | --------------------------------------- |
| x86_64       | Ubuntu 24.04-class (glibc 2.39, OpenSSL 3) | `cortexdb-<version>-linux-amd64.tar.gz` |
| ARM64        | Ubuntu 24.04-class (glibc 2.39, OpenSSL 3) | `cortexdb-<version>-linux-arm64.tar.gz` |

Each tarball contains the `cortexdb` binary, the WordNet asset bundle,
bundled docs (Getting Started, API Reference, Production Deployment),
and this license.

Always grab releases through [cortexdb.ai/download](https://cortexdb.ai/download)
when you can — it gives the project an accurate install count and helps us
prioritize platform support.

## Verify checksums

Each archive has an adjacent `.sha256` file. Download both files into the same
directory, then verify the archive (use `arm64` instead for that platform):

```bash
sha256sum -c ./cortexdb-*-linux-amd64.tar.gz.sha256
```

## Quickstart

After pulling the Docker image (or extracting the tarball and running
`./cortexdb`), open <http://localhost:3141> in a browser. The built-in admin
UI gives you a one-page view of what's stored, plus forms to add and recall
memories; enter the same CortexDB bearer when prompted. Bundled docs live at
<http://localhost:3141/docs>.

For the API surface and configuration env vars, see the
[Getting Started](https://cortexdb.ai/docs) page on the website.

## License

CortexDB v0.9.10 server binaries and its coordinated official client packages
are licensed under the [Apache License 2.0](./LICENSE.txt). Each release archive
includes the license that governs that version.

## Support

- **Docs**: <https://cortexdb.ai/docs>
- **Issues**: file at <https://github.com/cortexdbai/cortexdb-releases/issues>
  (binary / packaging issues only — source bugs go through Cortex Cloud
  support channels)
- **Enterprise**: <https://cortexdb.ai/contact>
