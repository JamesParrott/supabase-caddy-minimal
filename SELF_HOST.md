# Self-hosted Supabase with Caddy
(instead of Kong)

## Deployment
https://supabase.com/docs/guides/self-hosting/docker#dashboard-authentication

Get a clone of supabase for the base code
```sh
git clone --depth=1 https://github.com/supabase/supabase
```
(tested on commit 380a55e9bf8b6e49157f28f5dc4466d505cf1658)


Copy its Docker compose files to the root
```sh
cp -rf supabase/docker/* supabase
```


Clone this repo
```sh
git clone --branch NextJS_App --depth 1 https://github.com/JamesParrott/supabase-caddy-minimal
```
(tested on commit b193bc68bab6905c75d393f22d24bec12779ed56 (before this commit) and the supabase one above)

Copy this repo's patches into the supabase repo
```sh
cp -rf supabase-caddy-minimal/* supabase
```

Copy the example env variables from this repo
```sh
cp supabase-caddy-minimal/.env.example supabase/.env
```

Change dir to the supabase project repo's root
```sh
cd supabase
```

Edit the env variables
```sh
nano .env
```
Populate the env variables specific to your deployment, including those to be kept secret, e.g.:
DASHBOARD_CADDY_PW_HASH
DASHBOARD_CADDY_USERNAME
See: https://caddyserver.com/docs/v2-upgrade#basicauth

Replace example.com with your project's domain (point DNS records to the host server's public IP address).
Either comment out the SMTP section, or set SMTP_* to your email senders creds



Pull the latest images (commands may require sudo depending what user you are, and how Docker is installed)
```sh
docker compose pull
```

Build any custom images from source
```sh
docker compose build
```

Start the services (in detached mode)
```sh
docker compose up -d
```


