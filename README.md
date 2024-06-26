# Debian based CUDA Dev Container

Deprecated. See https://github.com/lambda-chat/python-template instead.

## Tested Environments

OS:

- Windows 11 Pro (22H2)

## Prerequisties

Windows:

- NVIDIA Driver (31.0.15.3640 or later)

WSL2:

- Docker engine (24.0.7 or later)
- [CUDA Toolkit (12.1 or later)](<https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local>)
- [cuDNN (9.0.0 or later)](https://developer.nvidia.com/cudnn-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local)
- [NVIDIA Container Toolkit (1.14.4 or later)](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

## Additional stuffs

Delete or modify any unnecessary stuffs to your liking.

Candidates:

- Poetry (Python package manager)
- Ruff (linter and formatter for Python)
- fish shell
- GitHub CLI
- Starship Prompt
- VS Code Extensions
- VS Code Settings
- Sample code(s) for OAT (in scripts/)
- etc.

## Thoughts

WSL2 に docker 環境と諸々のツールを用意すれば compose.yaml の

```json:
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              capabilities: [ gpu ]
              count: all
```

の設定だけでよいです。これは `--gpus all` フラグを付けて Docker コンテナを起動するのと等価です。Docker 19.03 の時代から取り残されてしまっていました。

Docker image 側で諸々調整する予定が、シンプルな Debian イメージで動作してしまいました。
