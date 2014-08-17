# Inspiration taken from:
#   * https://gorails.com/setup/ubuntu/14.04


FROM ubuntu:14.04
MAINTAINER sebastian.geiger@gmail.com

RUN apt-get update
RUN apt-get -qy install git-core wget curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties
RUN mkdir -p /build/ruby-2.1.2-workspace
RUN echo "cd /build/ruby-2.1.2-workspace; wget http://ftp.ruby-lang.org/pub/ruby/2.1/ruby-2.1.2.tar.gz; tar -xzvf ruby-2.1.2.tar.gz; cd ruby-2.1.2/; ./configure; make; sudo make install; ruby -v" > /build/ruby-2.1.2
RUN bash /build/ruby-2.1.2
RUN rm -rf /build/ruby-2.1.2-workspace
