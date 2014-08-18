# Inspiration taken from:
#   * http://blog.gemnasium.com/post/66356385701/your-dockerfile-for-rails
#   * https://gorails.com/setup/ubuntu/14.04

FROM sebastiangeiger/ubuntu-with-ruby:2.1.2p95
MAINTAINER sebastian.geiger@gmail.com

ENV RAILS_ENV production
ENV SECRET_KEY_BASE 2848a4674d1249d269446a8d222a7a86c2e17ed120bbecf290924843f51ca99279d6d4016f1b9e2504216ad0bf1017e2d105621a33bea64152140b317d7cea93
ENV POSTGRES_USERNAME rails_sample_app_user
ENV POSTGRES_PASSWORD kjLlPJjJqWD9VCjBuqWeSPA1P
ENV POSTGRES_DATABASE rails_sample_app_production

RUN gem install bundler
RUN adduser --disabled-password --home=/rails --gecos "" rails

RUN apt-get update
RUN apt-get -yq install nodejs libpq-dev

ADD rails_sample_app /rails/rails_sample_app
RUN echo "gem: --no-ri --no-rdoc" > /rails/.gemrc
RUN chown -R rails:rails /rails/rails_sample_app
RUN chmod -R +x /rails/rails_sample_app/scripts
RUN su rails -c "cd /rails/rails_sample_app; bundle install --without development test --path vendor/bundle"
RUN su rails -c "cd /rails/rails_sample_app; bundle exec rake assets:precompile"

EXPOSE 3000
USER rails

CMD /rails/rails_sample_app/scripts/start
