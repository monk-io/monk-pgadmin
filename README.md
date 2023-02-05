# Tensorflow & Monk
This repository contains Monk.io template to deploy Fluentbit either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

# Prerequisites
- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

#### Make sure monkd is running.
```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository
```bash
git clone https://github.com/monk-io/pgadmin
```

## Load Template
```bash
cd pgadmin
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list pgadmin
✔ Got the list
Type      Template              Repository  Version  Tags
runnable  pgadmin/pgadmin  local       -        -

```

## Deploy Stack
```bash
foo@bar:~$ monk run pgadmin/pgadmin 
? Select tag to run [local/pgadmin/pgadmin] on: mnk
✔ Starting the job: local/pgadmin/pgadmin... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% dpage/pgadmin4:latest mnk-1
✔ Checking/pulling images DONE
✔ Started local/pgadmin/pgadmin

🔩 templates/local/pgadmin/pgadmin
 └─🧊 Peer mnk-1
    └─🔩 templates/local/pgadmin/pgadmin
       └─📦 e813d5fdc8d63c9ff99fff59a85d3fa8-k-pgadmin-pgadmin-pgadmin
          ├─🧩 dpage/pgadmin4:latest
          └─🔌 open 16.171.45.206:8080 (0.0.0.0:8080) -> 80

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/pgadmin/pgadmin - Inspect logs
        monk shell     local/pgadmin/pgadmin - Connect to the container's shell
        monk do        local/pgadmin/pgadmin/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Variables
The variables are in `vault.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| monk_pgadmin_port             | Pg Admin Port, Default: 8080 	               |
| monk_default_email            | PG Admin login email, Default: kits@monk.io                    	|
| monk_default_password         | PG Admin Default password, Default: admin                    	|



## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```