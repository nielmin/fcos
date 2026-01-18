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
