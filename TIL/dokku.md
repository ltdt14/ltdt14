# Dokku
[Dokku](http://dokku.viewdocs.io/dokku/) is a self-hosted PaaS. Good for deploying small apps without hosting and configuring new servers.

## Getting started
- [Install Dokku](http://dokku.viewdocs.io/dokku/getting-started/installation/)
- Create following A records at your DNS to point to your server:
  - `dokku.<domainname>.tld`
  - `*.dokku.<domainname>.tld`
- Add the first domain to dokku: `dokku domains:add-global dokku.<domainname>.tld`
- Create a new app: `dokku apps:create <appname>`
- Add the app as a remote to your local git repo: `git remote add dokku dokku@<ip or domain>:<appname>`
- E.g create a simple node/express app. It must have a package.json with it's dependecies.
- Commit and push to the remote: `git push dokku main:master`
- The app deploys automatically to `<appname>.dokku.<domainname>.tld`
- Adding SSL is easy:
  - Install [Let's Encryp Plugin](https://github.com/dokku/dokku-letsencrypt)
  - Set E-Mail: `dokku config:set --global DOKKU_LETSENCRYPT_EMAIL=your@email.tld`
  - Install certificate: `dokku letsencrypt <appname>`
  - Turn on auto-renew: `dokku letsencrypt:auto-renew`