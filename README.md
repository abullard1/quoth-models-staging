# Quoth model staging

Test download origin for Quoth speech models. This repository contains model
metadata and license notices only. Model binaries are prerelease assets; no Quoth
application source, packages, user data, or internal documentation is hosted here.

## Available assets

`staging-20261010` provides multilingual Tiny, Base, Small and Large v3 Turbo GGML
weights for CPU and Vulkan GPU testing. They are byte-for-byte copies of
[ggerganov/whisper.cpp revision 5359861c739e955e79d9a303bcbc70fb988958b1](https://huggingface.co/ggerganov/whisper.cpp/tree/5359861c739e955e79d9a303bcbc70fb988958b1).
Their SHA-256 values were checked against that revision's LFS metadata.
`provenance.json` records each source URL, size and hash; `manifest.json` is the
filename-to-SHA-256 mapping used by Quoth. Both files accompany the release.

OpenVINO NPU encoders are not included. This staging release does not establish
NPU support or production-release readiness. Retain the included upstream MIT
license notices with redistributed models.

## Use with an installed test candidate

Quit any running Quoth instance first, then launch:

```sh
QUOTH_RELEASE_BASE_URL=https://github.com/abullard1/quoth-models-staging/releases/download \
QUOTH_ASSETS_TAG=staging-20261010 \
quoth
```

Use CPU or GPU for this release. Settings and existing models are preserved;
already-present model files skip downloading. A normal launch without these
variables uses the application's default download origin.

Quoth verifies a downloaded file when its hash is present. The existing alternate
origin policy permits missing hashes, so this staging release includes a hash for
every advertised asset. It does not prove the production origin's stricter
missing-manifest behavior. Do not set `QUOTH_ALLOW_UNVERIFIED`.
