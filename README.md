# Fedora CoreOS VPS Configuration

## Description
Used to access my homelab outside my network, which is behind a CGNAT.

## Status

WIP

Decided on a whim to switch from Caddy to Traefik.

Testing in progress.

Previously had something that was too complicated and did not work.

Currently based on [Thomas Letan's](https://github.com/lthms/tinkerbell) configuration.

## Features
- Containers using [Podman Quadlets](https://docs.podman.io/en/stable/markdown/podman-systemd.unit.5.html)
    - Custom [Caddy](https://github.com/caddyserver/caddy) build with [Cloudflare DNS](https://github.com/caddy-dns/cloudflare) support
        - `.build` points to `Containerfile` to build custom Caddy image
    - Nodes connected with [NetBird Mesh VPN](https://netbird.io/)
    - Secrets stored with `podman secret`
        - NetBird setup key
        - Cloudflare DNS API token

## HOWTO
1. Download [Fedora CoreOS Live ISO](https://fedoraproject.org/coreos/download?stream=stable)
2. Boot into live environment
3. Run the CoreOS installer:

    `sudo coreos-installer install -I https://github.com/nielmin/fcos/releases/download/main/config.ign /dev/sda`

4. Reboot

    `sudo reboot`

5. Provide secrets for Cloudflare DNS and NetBird

    `printf CF_API_TOKEN | sudo podman secret create cf-token - `

    `printf NB_SETUP_KEY | sudo podman secret create nb-client - `

6. Format and reload Caddyfile

    `sudo podman exec -w /etc/caddy caddy caddy fmt --overwrite`

    `sudo podman exec -w /etc/caddy caddy caddy reload`
