[点击前往中文说明](README_chs.md)

## Acknowledgments

- [IrineSistiana/mosdns](https://github.com/IrineSistiana/mosdns) An advanced DNS forwarder.
- [v2fly](https://github.com/v2fly)

## Attention

 **Do not abuse service from PaaS platforms or your account could get banned. Deploy at your own risk.**

## <a id="Overview"></a>Overview

This repo is for deploying [mosdns](https://github.com/IrineSistiana/mosdns) which is an advanced DNS forwarder on various PaaS platforms (Heroku, Okteto, Railway, Northflank, fly.io, etc.).

![未命名绘图 (1)](https://user-images.githubusercontent.com/98247050/179379517-1cb35632-e594-4712-8d62-f0ef1ba5c8d9.jpg)

## <a id="Deployment"></a>Deployment

- Fork this repo
- Modify /content/config.yaml to suit your needs. Default config file has ad-blocking and ECS enabled.
- Strongly recommend custom DOH_PATH env value to prevent other ppl from abusing your deployment.

### Deploy to Heroku 
- You need credit card verified account to run dyno 24*7, otherwise you will be limited to 550 hours per month.  

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### Deploy to Okteto, Railway, Northflank etc.
- Link your forked repo in PaaS platform's dashboard
- Set DOH_PATH env
- Deploy

### Deploy to Koyeb
- Create a new release in your forked repo with a tag like "v0.0.1"
- Wait for github action to finish
- Use your new generated container image to deploy.

### Deploy to fly.io
- Install [flyctl](https://fly.io/docs/flyctl/installing/)
- git clone repo and change path to repo folder
- edit fly.toml to set DOH_PATH env
```
# Login
flyctl auth login
# Create app
flyctl apps create <app_name>
# Set region https://fly.io/docs/reference/regions/
flyctl regions set <region_code> -a <app_name>
# Deploy
flyctl deploy --detach -a <app_name> --remote-only --no-cache
```
