> [!WARNING]
> The data in this official repo is out of date? the current host image is Ubuntu 22.04.5.
>
> From `creation.log`:
>```
>2024-09-26 09:09:21.522Z: Host information
>2024-09-26 09:09:21.523Z: ----------------
>2024-09-26 09:09:21.523Z: OS: Ubuntu 22.04.5 LTS (stable release)
>2024-09-26 09:09:21.523Z: Image details: https://github.com/github/codespaces-host-images/blob/main/README.md
>2024-09-26 09:09:21.523Z: ----------------
>```
> Codespaces with mounts with missing sources, or `~` paths (not expanding) are suddenly now failing, when before they were fine, or at least worked in local devcontainers and failed gracefully in Codespaces (which was expected behaviour):
> ```
>volumes:
>  - ~/.aws:/home/vscode/.aws
>```
> Errors in `creation.log`:
> ```
>2024-09-26 09:09:23.649Z: WARN[0000] cannot expand '~', because the environment lacks HOME 
>[...]
>Error response from daemon: invalid mount config for type "bind": bind source path does not exist: /var/lib/docker/codespacemount/workspace/codespaces-host-images/.devcontainer/~/.aws
>```
>
>
> It looks like `docker-compose` may also been updated. Looking through the official changelog it looks like there may be issues with bind mounts in some of the recent releases: https://docs.docker.com/compose/releases/release-notes/
>
>It seems like this can be fixed by moving the mount to `devcontainer.json`:
>```
>"mounts": [
>  "source=${env:HOME}/.aws,target=/home/vscode/.aws,type=bind"
>]
>```


<!-- This file is auto-generated. Please do not edit this file directly. -->
<!-- Generated on: 2024-01-13T05:39:12.553Z -->

# Codespaces Host Image Configurations
## Stable
**Version**: 20240113001

**Host OS**: Ubuntu 22.04.3 LTS (Jammy Jellyfish)

### Installed Packages
| Package | Version | Description |
|---|---|---|
| moby-engine | 24.0.x | Docker container platform (engine package) |
| docker-compose | 2.22.x | Define and run multi-container applications with Docker. |
| nodejs | 18.19.x | Node.js event-based server-side javascript engine |
| python3 | 3.10.x | interactive high-level object-oriented language (default python3 version) |
| azcopy | 10.22.x | A command-line utility designed for copying data to/from Microsoft Azure Blob, File, and Table storage. (path: `/.codespaces/azcopy`) |


<small>**Quality**: stable; **Codename**: blueberry</small>
## Beta
**Version**: 20240113001

**Host OS**: Ubuntu 22.04.3 LTS (Jammy Jellyfish)

### Installed Packages
| Package | Version | Description |
|---|---|---|
| moby-engine | 24.0.x | Docker container platform (engine package) |
| docker-compose | 2.22.x | Define and run multi-container applications with Docker. |
| nodejs | 18.19.x | Node.js event-based server-side javascript engine |
| python3 | 3.10.x | interactive high-level object-oriented language (default python3 version) |
| azcopy | 10.22.x | A command-line utility designed for copying data to/from Microsoft Azure Blob, File, and Table storage. (path: `/.codespaces/azcopy`) |


<small>**Quality**: stable; **Codename**: blueberry</small>
