# embedded-toolchain

Minimal Docker image for building ARM Cortex-M firmware.

## Contents

- `arm-none-eabi-gcc` (`gcc-arm-none-eabi`, `libnewlib-arm-none-eabi`)
- `cmake`
- `ninja`

Based on `debian:bookworm-slim`. Working directory: `/workspace`.

## Usage

In a GitHub Actions workflow:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: ghcr.io/<owner>/embedded-toolchain:latest
    steps:
      - uses: actions/checkout@v4
      - run: cmake -S . -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=<toolchain.cmake>
      - run: cmake --build build
```

## Build locally

```bash
docker build -t embedded-toolchain .
```

## Tags

- Push to `main`: `main`, `latest`
- Push `v*` tag (e.g. `v1.0.0`): `v1.0.0`
- Pull requests: build only, no push

## Adding packages

Edit the `apt-get install` list in `Dockerfile`.
