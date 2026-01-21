# WIP Komodo-Stacks 🦎

My collection of Docker Compose stacks I'm managing through [Komodo](https://komo.do/). These are designed to be synced directly to a Komodo instance for automated deployments and GitOps-style management.

this is going to be ever growing and changing, it is not reccomended you hook directly into this, but to use it for inspiration as i WILL make breaking changes to it.
## What's in here? 📂

The repo is organized into different stacks for various services. Some of the container types you will find include:

- **Infrastructure**: Traefik for reverse proxying, CrowdSec for security, and Blocky for DNS.
- **Media**: The usual suspects (Radarr, Sonarr, Jellyfin, etc.) and some extras like Audiobookshelf and Navidrome.
- **Utilities**: Vaultwarden for passwords, Uptime Kuma for monitoring, and Glance as a dashboard.

## Setup ⚙️

These files rely heavily on environment variables to keep secrets out of the repo. You'll need a `.env` file on your host or defined within Komodo to fill in the blanks.

I've included `sample.env` files in the directories to show what variables are required. If this is not filled out, it will simply not work.

## Usage with Komodo 🚀
If you are insane and want to copy my *exact* setup do the following:
1. Add this repo as a **Git Resource** in your Komodo UI.
2. Create a new **Stack** and point it to the specific subfolder/compose file.
3. Set up your **Environment Variables** within the Komodo Stack settings.
4. Enable **Polling** or **Webhooks** if you want it to auto-deploy when changes are pushed here.

## Notes 📝

- Most web-facing services are configured with Traefik labels and CrowdSec middleware.
- I use `gluetun` to route specific traffic through a VPN.
- Paths are mostly absolute or based on a `${DOCKER_ROOT}` variable for consistency across different machines.
