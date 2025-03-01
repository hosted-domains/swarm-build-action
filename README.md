[![Release](https://img.shields.io/github/actions/workflow/status/hosted-domains/swarm-build-action/release.yaml?logo=github&logoColor=white&label=release)](https://github.com/hosted-domains/swarm-build-action/actions/workflows/release.yaml)
[![GitHub Release Version](https://img.shields.io/github/v/release/hosted-domains/swarm-build-action?logo=github)](https://github.com/hosted-domains/swarm-build-action/releases/latest)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/hosted-domains/swarm-build-action?logo=github&logoColor=white&label=updated)](https://github.com/hosted-domains/swarm-build-action)
[![GitHub Org Stars](https://img.shields.io/github/stars/hosted-domains?style=flat&logo=github&logoColor=white)](https://cssnr.github.io/)
[![Discord](https://img.shields.io/discord/899171661457293343?logo=discord&logoColor=white&label=discord&color=7289da)](https://discord.gg/wXy6m2X8wY)

# Swarm Build Action

- [Inputs](#Inputs)
- [Examples](#Examples)

Deploy a Stack to Portainer with the desired service-configs environment variables.

## Inputs

| input           | required | default                     | description                   |
| --------------- | :------: | --------------------------- | ----------------------------- |
| version         | **Yes**  | -                           | Version Tag to Deploy         |
| stack-file      |    -     | `docker-compose-swarm.yaml` | SSH Key for `service-configs` |
| registry        |    -     | `ghcr.io`                   | Config File                   |
| username        | **Yes**  | -                           | Stack Name                    |
| password        | **Yes**  | -                           | Compose File                  |
| portainer-url   | **Yes**  | -                           | Portainer URL                 |
| portainer-token | **Yes**  | -                           | Portainer Token               |

## Examples

For Django5 Boiler:

```yaml
- name: 'Swarm Build Action'
  if: ${{ env.build == 'true' }}
  uses: hosted-domains/swarm-build-action@master
  with:
    version: ${{ env.env-name }}
    username: ${{ vars.GHCR_USER }}
    password: ${{ secrets.GHCR_PASS }}
```
