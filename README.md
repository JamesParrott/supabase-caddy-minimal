# Self-hosted Supabase with Caddy
(instead of Kong)

## Deployment
https://supabase.com/docs/guides/self-hosting/docker#dashboard-authentication

Get a clone of supabase for the base code
```sh
git clone --depth=1 https://github.com/supabase/supabase
```



Copy the Docker compose files to the root
```sh
cp -rf supabase/docker/* supabase
```


Clone this repo
```sh
git clone --depth 1 https://github.com/JamesParrott/supabase-caddy-minimal
```

Copy this repo's patches into the supabase repo
```sh
cp -rf supabase-caddy-minimal/* supabase
```




```sh

# Switch to the supabase project directory
cd supabase

# Pull the latest images
docker compose pull

# Start the services (in detached mode)
docker compose up -d
```
