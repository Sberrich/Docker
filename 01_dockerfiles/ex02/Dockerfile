FROM ruby:2.6.5
RUN apt-get update -y && apt-get install -y \
		build-essential \
		libpq-dev \
		nodejs \
		sqlite3 \
		gem \
		yarn
RUN gem install bundler 
# Run on ft-rails:on-build
COPY app /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

#build 
#docker build -t ft-rails:on-build .
#
