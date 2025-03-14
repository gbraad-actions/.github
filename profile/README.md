GitHub Actions related repositories
===================================


This organization contains Actions and container definitions that are used for the projects and organizations like:

  - [gbraad-dotfiles/upstream](https://github.com/dotfiles/uptream) in the org [gbraad-dotfiles](https://github.com/gbraad-dotfiles)
  - All projects in [gbraad-devenv](https://github.com/gbraad-devenv)
  - All projects in [gbraad-homelab](https://github.com/gbraad-homelab)
  - ...


### [Remove unwanted to maximize diskspace](https://github.com/gbraad-actions/remove-unwanted)
```yaml
- name: Remove unwanted stuff
  uses: gbraad-actions/remove-unwanted@v1
```

### [Install Tailscale using distro package manager and uses systemd](https://github.com/gbraad-actions/tailscale-action) - [Example](https://github.com/gbraad-redhat/simple-go-server/blob/main/.github/workflows/crc_linux.yaml)
```yaml
- name: Tailscale
  uses: gbraad-actions/tailscale-action@v1
  with:
    authkey: ${{ secrets.TAILSCALE_AUTHKEY }}
    args: --ssh --accept-dns=false --operator=runner
- ...
- name: Hang around
  if: ${{ failure() }}
  run: sleep infinity  # this allows you to access the runner over SSH/Tailnet
```

### [Start Tailscale when preinstalled in (container) image](https://github.com/gbraad-actions/start-tailscale)
```yaml
jobs:
  build:
    runs-on: ... # [ubunu-24.04|ubunu-24.04-arm]
    container: 
      image: ghcr.io/gbraad-actions/fedora:stable
      options: --privileged
    steps:
      - name: Tailscale Action
        uses: gbraad-actions/start-tailscale@v1
        with:
          authkey: ${{ secrets.TAILSCALE_AUTHKEY }}
```

### [Code tunnel action](https://github.com/gbraad-actions/code-tunnel-action)
```yaml
- name: Code tunnel
  if: ${{ failure() }}
  uses: gbraad-actions/code-tunnel-action@v1
```

### [Code serve web action](https://github.com/gbraad-actions/code-serveweb-action)
```yaml
- name: Code serve web
  if: ${{ failure() }}
  uses: gbraad-actions/code-serveweb-action@v1
```

### [Machinefile executor](https://github.com/gbraad-actions/machinefile-executor-action)
```yaml
- name: Run Machinefile commands
  uses: gbraad-actions/machinefile-executor-action@v4
  with:
    containerfile: 'Containerfile'
    context: '.'
```

### [Setup virtualization support](https://github.com/gbraad-actions/setup-virtualization)
```yaml
- name: virtualization support
  uses: gbraad-actions/setup-virtualization@v1
```

### [Setup container tools](https://github.com/gbraad-actions/setup-container-tools)
```yaml
- name: Install containers tools
  uses: gbraad-actions/setup-container-tools@v1
```

### [Cleanup registry](https://github.com/gbraad-actions/cleanup-untagged-packages) - [Example](https://github.com/gbraad-dotfiles/.github/blob/main/.github/workflows/cleanup.yml)
```yaml
- uses: gbraad-actions/cleanup-untagged-packages@main
  with:
    packages: fedora, centos, ...
    token: ${{ secrets.PACKAGE_CLEANUP_TOKEN }}
```

----

## [Job containers](https://github.com/gbraad-actions/containers) [⚙️](https://github.com/gbraad-actions/containers/actions)

#### Fedora 41 [![build container - fedora-multi-arch](https://github.com/gbraad-actions/containers/actions/workflows/build-container-fedora.yml/badge.svg)](https://github.com/gbraad-actions/containers/actions/workflows/build-container-fedora.yml) - [Example](https://github.com/gbraad-devenv/alt-machine-os/blob/1639c82320feb3f1bdf2fb4b61b049c2a1b3ccff/.github/workflows/build-process.yml#L109-L111)

```yaml
    runs-on: ... # [ubunu-24.04|ubunu-24.04-arm]
    container: 
      image: ghcr.io/gbraad-actions/fedora:stable
      options: --privileged
```

#### CentOS Stream9 [![build container - centos-multi-arch](https://github.com/gbraad-actions/containers/actions/workflows/build-container-centos.yml/badge.svg)](https://github.com/gbraad-actions/containers/actions/workflows/build-container-centos.yml)

```yaml
    runs-on: ... # [ubunu-24.04|ubunu-24.04-arm]
    container: 
      image: ghcr.io/gbraad-actions/centos:stable
      options: --privileged
```

