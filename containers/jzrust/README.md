# arm64v8/rust

## Build

Note: Make sure to have `nodejs`, `npm` and `yarn`
Run `yarn update` the first time to update the packages

```sh
vscode-dev-containers myuser$ build/vscdc push --no-push --registry mcr.jz.com --registry-path vscode/jzcontainers --release main jzrust
```

```sh
vscode-dev-containers myuser$ build/vscdc cg --registry mcr.jz.com --registry-path vscode/jzcontainers --release main jzrust
```

```sh
vscode-dev-containers myuser$ build/vscdc pack --prep-and-package-only --release main
```

## Copy tar to use builded container

```sh
mkdir ~/Documents/dev-containers
cp vscode-dev-containers-0.158.0-dev.tgz ~/Documents/dev-containers/
cd ~/Documents/dev-containers
tar xvfz vscode-dev-containers-0.158.0-dev.tgz
vi package/containers/jzrust/.devcontnainer/Dockerfile
```
Change the target image from mcr.microsoft.com to mcr.jz.com

```text
# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/master/containers/jzrust/.devcontainer/base.Dockerfile

FROM mcr.jz.com/vscode/jzcontainers/arm32v7/rust:dev

# RUN rustup component add rustfmt
# [Optional] Uncomment this section to install additional OS packages you may want.
#
# RUN apk add --no-cache <your-package-list-here>
```

## License

Copyright (c) Microsoft Corporation. All rights reserved.

Licensed under the MIT License. See [LICENSE](https://github.com/Microsoft/vscode-dev-containers/blob/master/LICENSE).
