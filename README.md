# Notification application

This is an example of a simple application that

* Allows admins to select a subset of users to send sms and email notifications.
* Allows users to select sms or email notifications


## Install

Based on the the [civic rails template](https://github.com/invisiblefunnel/civic-rails), optimized for heroku.

Make sure postgres is installed and running (osx instructions

```console
$ git clone git@github.com:eeeschwartz/notify.git
$ cd notify
$ bundle install
$ cp .env.test-sample .env.test
```

grab your [twilio credentials](https://www.twilio.com/user/account/developer-tools/test-credentials) and set TWILIO_SID and TWILIO_AUTH_TOKEN in .env.test

```console
$ vim .env.test # or use your favorite editor
$ RAILS_ENV=test rake db:create db:migrate
$ rspec spec
$ cp .env.development-sample .env.development
```

Set your twilio credentials in .env.development

```console
$ rake db:create db:migrate db:seed
$ rails server
```

## Deploy

See the [Getting Started](https://devcenter.heroku.com/articles/quickstart) guide if you haven't used Heroku before.

```console
$ heroku create <app name>
$ heroku addons:add pgbackups:auto-month # recommended
$ heroku config:set SECRET_KEY_BASE=`bundle exec rake secret`
$ git push heroku master
$ heroku run rake db:migrate
$ heroku open
```

## Notify Users
    rake notify_addresses:pickup_tomorrow
