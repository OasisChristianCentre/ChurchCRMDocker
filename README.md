# ChurchCRMDocker

An example Docker Swarm configuration for ChurchCRM used by [Oasis Christian Centre](https://occ-stratford.org.uk).

## Images

See image used on Docker Hub here.

## Instructions 

1. Install [Docker](https://www.docker.com/community-edition#/download)
2. Generate password files:

```bash
openssl rand -base64 32 > db_password.txt
openssl rand -base64 32 > db_root_password.txt

```

or (if you don't have openssl installed)

```bash
"yourrandompassword" > db_password.txt
"yourrandompassword" > db_root_password.txt

```
3. Edit docker-stack.yml with desired settings 
4. Initialize a new Swarm

```bash
docker swarm init
```

5. Deploy the ChurchCRM stack

```bash
docker stack deploy -c docker-stack.yml churchcrm
````

6. Check web logs to see if apache has started

```bash
docker service logs churchcrm_web
```

7. When you see "Starting apache..." browse [localhost:8080](http://localhost:8080) (or whatever you have configured).
