# DB Server
- [Heroku - Hobby Dev](https://www.heroku.com/pricing#data-services)
  - Row Limit 10k
  - Connections 20
- [Heroku Dashboard](https://data.heroku.com/)
- [Heroku Dev Center](https://devcenter.heroku.com/)

## Getting Started

Refer the following articles for detailed instructions
- [The Heroku CLI](https://stackabuse.com/adding-a-postgresql-database-to-a-node-js-app-on-heroku/)

Summary of steps related to Ubuntu desktop is provided below

```sh
# List all apps
heroku apps

# Get App Info
heroku apps:info --app always-free

# Create a NEW database and connect to the App
heroku addons:create heroku-postgresql:hobby-dev --app always-free

# Output
# Creating heroku-postgresql:hobby-dev on ⬢ always-free... free
# Database has been created and is available
#  ! This database is empty. If upgrading, you can transfer
#  ! data from another database with pg:copy
# Created postgresql-acute-90963 as DATABASE_URL

# Connection to the database
heroku pg:psql postgresql-acute-90963 --app always-free
```