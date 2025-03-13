GitHub Actions by Gerard Braad
==============================

### Job container (Fedora 41) [⚙️](https://github.com/gbraad-actions/containers/actions) [![build container - fedora-multi-arch](https://github.com/gbraad-actions/containers/actions/workflows/build-container-fedora.yml/badge.svg)](https://github.com/gbraad-actions/containers/actions/workflows/build-container-fedora.yml)

```yaml
jobs:
  build:
    runs-on: ... # [ubunu-24.04|ubunu-24.04-arm]
    container: 
      image: ghcr.io/gbraad-actions/fedora:stable
      options: --privileged
    steps:
```


### Remove unwanted to maximize diskspace
```yaml
- name: Remove unwanted stuff
  uses: gbraad-actions/remove-unwanted@v1
```

### Install Tailscale using distro package manager and uses systemd
```yaml
- name: Tailscale
  uses: gbraad-actions/tailscale-action@v1
  with:
    authkey: ${{ secrets.TAILSCALE_AUTHKEY }}
    args: --ssh --accept-dns=false --operator=runner
```

### Code tunnel action
```yaml
- name: Code tunnel
  if: ${{ failure() }}
  uses: gbraad-actions/code-tunnel-action@v1
```

### Code serve web action
```yaml
- name: Code serve web
  if: ${{ failure() }}
  uses: gbraad-actions/code-serveweb-action@v1
```

### Machinefile executor
```yaml
- name: Run Machinefile commands
  uses: gbraad-actions/machinefile-executor-action@v4
  with:
    containerfile: 'Containerfile'
    context: '.'
```

### Cleanup registry
```yaml
- uses: gbraad-actions/cleanup-untagged-packages@main
  with:
    packages: fedora, centos, ...
    token: ${{ secrets.PACKAGE_CLEANUP_TOKEN }}
```
