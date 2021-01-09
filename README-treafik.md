# Traefik + LetsEncrypt mattermost update notes

Modifications and requirements:
 - Removed NGINX, added Traefik in an internet facing HTTPS state
 - Traefik information:
     - added SSL through LetsEncrypt auto DNS challenging, 
       - requires a domain with a service provider that supporst letsencrypt DNS based HTTPS providers (namecheap in this example)
       - Other providers besides namecheap's varaibles: https://doc.traefik.io/traefik/v2.0/https/acme/#providers
     - .env file needs secrets for namecheap / provider of choice, copy .env_example to .env and update
     - update traefik/traefik.toml with your email address to receive LetsEncrypt expiration warnings, or any custom network you maybe using (also needs added to docker-compose)
     - once setup SSL certificate should be automated and auto-renew
 - app/Dockerfile MM version pinned to latest quality release of mattermost https://docs.mattermost.com/administration/changelog.html
