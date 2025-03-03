GitHub Actions by Gerard Braad
==============================

### `remove-unwanted`
```yaml
- name: Remove unwanted stuff
  uses: gbraad-actions/remove-unwanted@v1
```

### Install Tailscale
```yaml
- name: Tailscale
  uses: tailscale/github-action@v3
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

### Machinefile executor
```yaml
- name: Run Machinefile commands
  uses: gbraad-actions/machinefile-executor-action@v3
  with:
    containerfile: 'Containerfile'
    context: '.'
```
