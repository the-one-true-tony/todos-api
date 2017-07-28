# TODO API

## Issues with deploying to AWS beanstalk
There are two main issues with deploying this app to aws beanstalk

1. Rails 5 requires listen gem that is not provided natively.  This can be fixed by going to the environments/development.rb file and commenting out this lines

```
config.file_watcher = ActiveSupport::EventedFileUpdateChecker
```

2. If postgres was setup you need to add a postgres RDS in AWS and configure the database in the your database.yml file
```
development:
  <<: *default
  database: <%= ENV['RDS_DB_NAME'] %>
  username: < your username >
  password: < your password >
  host: <%= ENV['RDS_HOSTNAME'] %>
  port: <%= ENV['RDS_PORT'] %>
```
