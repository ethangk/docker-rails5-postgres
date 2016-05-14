# README

## Setup
```
git clone git@github.com:ethangk/docker-rails5-postgres.git YOUR_FOLDER
cd YOUR_FOLDER
docker-compose run web rails new . --api --force --database=postgresql
```

You'll need to go into `config/database.yml` and add the fragment below to the `default` configuration

```
  username: postgres
  password:
  host: db
```

When that's complete, you can run the following commands.

```
docker-compose up -d
docker-compose run web rake db:create
docker-compose restart web
```

Find your docker-machine ip through `docker-machine ip`, and go to the IP it specified, on port `3000`.

You'll probably want to change the repo that this project is pointing to. This can be achieved a few different ways.
 - Fork the project
 - Change the origin (`git remote set-url origin https://github.com/USERNAME/OTHERREPOSITORY.git`)

## Potential issues
`ERROR: failed to create endpoint PROJECT NAME on network PROJECT_default: Bind for 0.0.0.0:3000 failed: port is already allocated`
If you see this, something is already running on port 3000. Find out what is is and kill it.
