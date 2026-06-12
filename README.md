# Easy WireGuard Connect

This GitHub Action simplifies the setup of a WireGuard connection using `wg-quick`. It only requires a WireGuard configuration file as input to get your connection up and running quickly. No more multiple input variables or complex setup!

## Usage

To use this GitHub Action, follow these steps in your workflow file:

```yaml
name: Set up WireGuard Connection

env:
  DEFAULT_CONFIG: ${{ secrets.WIREGUARD_CONFIG }}

on:
  push:
    branches:
      - main

  workflow_dispatch:
    inputs:
      WG_CONFIG:
        description: WireGuard (wg-quick) configuration file
        required: false
        default: "wg0.conf"

jobs:
  wireguard:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v6

    - name: Set up WireGuard Connection
      uses: vados-dev/easy-wg-connect@v1
      with:
        WG_CONFIG: ${{ env.DEFAULT_CONFIG }}
        # or
        #WG_CONFIG: ${{ inputs.WG_CONFIG }}
```
