[![Release](https://img.shields.io/github/actions/workflow/status/hosted-domains/swarm-build-action/release.yaml?logo=github&logoColor=white&label=release)](https://github.com/hosted-domains/swarm-build-action/actions/workflows/release.yaml)
[![GitHub Release Version](https://img.shields.io/github/v/release/hosted-domains/swarm-build-action?logo=github)](https://github.com/hosted-domains/swarm-build-action/releases/latest)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/hosted-domains/swarm-build-action?logo=github&logoColor=white&label=updated)](https://github.com/hosted-domains/swarm-build-action/graphs/commit-activity)
[![GitHub Top Language](https://img.shields.io/github/languages/top/hosted-domains/swarm-build-action?logo=htmx&logoColor=white)](https://github.com/hosted-domains/swarm-build-action)
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
| stack-name      | **Yes**  | -                           | Stack Name                    |
| stack-file      |    -     | `docker-compose-swarm.yaml` | Compose File                  |
| config-file     | **Yes**  | -                           | Config File                   |
| config-ssh-key  | **Yes**  | -                           | SSH Key for `service-configs` |
| portainer-url   | **Yes**  | -                           | Portainer URL                 |
| portainer-token | **Yes**  | -                           | Portainer Token               |

## Examples

For Django5 Boiler (with hard coded values for example):

```yaml
- name: 'Portainer Deploy Action'
  uses: hosted-domains/swarm-build-action@master
  with:
    version: dev
    stack-name: dev_cssnr-django5-boiler
    config-file: services/shane/django5-boiler/dev.env
    config-ssh-key: ${{ secrets.SERVICE_CONFIGS_KEY }}
    portainer-url: ${{ secrets.PORTAINER_URL }}
    portainer-token: ${{ secrets.PORTAINER_TOKEN }}
```

But in reality it looks like this:

```yaml
- name: 'Portainer Deploy Action'
  if: ${{ env.deploy == 'true' }}
  uses: hosted-domains/swarm-build-action@master
  with:
    version: ${{ env.env-name }}
    stack-name: ${{ env.stack-name }}
    config-file: services/shane/django5-boiler/${{ env.env-name }}.env
    config-ssh-key: ${{ secrets.SERVICE_CONFIGS_KEY }}
    portainer-url: ${{ secrets.PORTAINER_URL }}
    portainer-token: ${{ secrets.PORTAINER_TOKEN }}
```
