# How To Upgrade bbb-docker


### Upgrading `v2.5.x` -> `v2.6.x`

- *Breaking change:* Greenlight got fully rewritten
    * it is starting as a fresh installation. you can migrate your data with `./scripts/greenlight-migrate-v2-v3`
    * some greenlight settings under `.env` have changed. compare your version with `sample.env`
    * it is now served directly under `/` and not in `/b`. If you use an reverse proxy not included in this repo, ensure to update your config accordingly!

apart from that follow the guide below.

### within `v2.6.x`
#### Backup
if you use greenlight, create a database backup first
```bash
docker exec -t docker_postgres_1 pg_dumpall -c -U postgres > /root/greenlight_`date +%d-%m-%Y"_"%H_%M_%S`.sql
```

#### Upgrading
```bash
# upgrade!
./scripts/upgrade

# restart updated services
docker compose up -d
```
