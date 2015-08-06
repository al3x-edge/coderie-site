![ScreenShot](app/assets/images/brand/coderie-main.png)
# How to bootstrap the application

## Requirements
- boot2docker installed (Kitematic on OS X will work)

## Installation
- `docker run -it -v $(pwd):/usr/src/app -w /usr/src/app ruby:2.2 bundle install && docker-compose build`
- `docker-compose up`
- `docker-compose run web rake db:create`
- `docker-compose run web rake db:migrate`
- `docker-compose run web rake`


## Working with Rails
Rails is now inside of the container so commands will look like:

```shell
docker-compose run web rails generate scaffold post title body:text published:boolean
```

## Bundled Dependencies
Dependencies are also built into the container. This means that the container
could ship off to production (doesn't have to) in it's state and have the exact
dependencies shipped with it. This creates a bit more work though.  Instead of
just `bundle install` after gem changes, you will need to run the following:

```shell
docker run -it -v $(pwd):/usr/src/app -w /usr/src/app ruby:2.2 bundle install && docker-compose build
```

## Docker Installation
### Requirements
- [boot2docker installed](http://boot2docker.io/)
- [docker-compose installed](http://docs.docker.com/compose/install/)

### Install Steps
- `docker-compose build`
- `docker-compose up`
- `docker-compose run web rake db:create`
- `docker-compose run web rake db:migrate`
- `docker-compose run web rake`

#### Working with Rails
Rails is now inside of the container so commands will look like:

```shell
docker-compose run web rails generate scaffold post
```

#### Bundled Dependencies
Dependencies are also built into the container. This means that the container
could ship off to production (doesn't have to) in it's state and have the exact
dependencies shipped with it. This creates a bit more work though.  Instead of
just `bundle install` after gem changes, you will need to run the following:

```shell
docker-compose build
```

## Additional Docs
* [Contributing Guidelines](/docs/contributing.md)
* [Frontend developer workflow](/docs/frontend-workflow.md)
