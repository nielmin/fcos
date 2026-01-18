# Fedora CoreOS VPS Configuration

## Description
Used to access my homelab outside my network, which is behind a CGNAT.

## Status
Previously had something that did not work.
Currently based on [Thomas Letan's](https://github.com/lthms/tinkerbell) configuration.

## Features
- Containers using Podman Quadlets
    - Custom Caddy build with Cloudflare DNS support
    - NetBird Mesh VPN
        - Setup key stored in `podman secret`

## HOWTO
1. Download Fedora CoreOS Live ISO
2. Boot into live environment
3. Download latest `config.ign` from releases.
    - `curl -OL https://github.com/nielmin/fcos/releases/download/main/config.ign`
4. Run the CoreOS installer:

    `sudo coreos-installer install -i config.ign`

5. Reboot

    `sudo reboot`
