FROM ubuntu:20.04
#FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install -y mongodb-server ruby-full ruby-dev build-essential git
RUN gem install bundler -v 2.4.22
#RUN apt-get install -y mongodb-server ruby-full build-essential git ruby-bundler

RUN git clone -b monolith https://github.com/express42/reddit.git

COPY mongod.conf /etc/mongod.conf
COPY db_config /reddit/db_config
COPY start.sh /start.sh

RUN cd /reddit && rm Gemfile.lock && bundle install
#RUN cd /reddit && bundle install
RUN chmod 0777 /start.sh

CMD ["/start.sh"]
