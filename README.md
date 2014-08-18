# Docker on Rails
This repository is a loose collection of notes and files needed to run rails on docker.
It goes hand in hand with [rails_sample_app](https://github.com/sebastiangeiger/rails_sample_app).

## Building
TODO: How to automate the build process? Goal: Be able to run it on a CI server
Right now this is a weird mix of scp and git to setup the workspace.
Once that workspace is setup I run `docker build -t postgresql_for_rails_sample_app .`
and `docker build -t rails_sample_app .`
I am using boot2docker on top of MacOS X which complicates the build process even further


## On the server
    docker run -d --name postgresql_for_rails_sample_app_instance postgresql_for_rails_sample_app
    docker run -t -i -p 5000:3000 --link postgresql_for_rails_sample_app_instance:pg rails_sample_app bash
    cd /rails/rails_sample_app; bundle exec rake db:create db:migrate db:seed; exit
    docker run -d -p 5000:3000 --link postgresql_for_rails_sample_app_instance:pg rails_sample_app
