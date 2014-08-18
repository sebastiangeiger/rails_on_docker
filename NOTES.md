## Boot2Docker configuration
How to automate the build process?


## Building

## On the server
docker run -d --name postgresql_for_rails_sample_app_instance postgresql_for_rails_sample_app
docker run -t -i -p 5000:3000 --link postgresql_for_rails_sample_app_instance:pg rails_sample_app bash
cd /rails/rails_sample_app; bundle exec rake db:create db:migrate db:seed; exit
docker run -d -p 5000:3000 --link postgresql_for_rails_sample_app_instance:pg rails_sample_app
