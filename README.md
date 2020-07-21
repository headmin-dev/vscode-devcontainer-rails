# Ruby on Rails Devcontainer for Visual Studio Code

## Why?

To create a fully self-contained development experience for Rails devs, with only VSCode and Docker as the host dependencies. No rbenv, no bundler, no other dependencies required. Comes with best-in-class Ruby and Rails extensions pre-configured.

## Existing Rails Project

- Clone this repo into your project folder, open the folder in VSCode, when prompted select "Reopen in container".
- Ensure `config/database.yml` is pointing to `database` as the DB host, since that's the name of the docker container.
- Run `rails db:create` and `rails db:migrate`
- Start the server with `rails s`, you can access your app at http://localhost:3000

## New Rails Project

- First install the rails gem with `gem install rails`
- Initialize a new rails application with `rails new . -d postgresql`
- When asked, you may choose to overwrite this README.md with the one created by Rails
- DRY out the database configuration, `config/database.yml` should have a default section like this:

  ```
  default: &default
    adapter: postgresql
    encoding: unicode
    # For details on connection pooling, see Rails configuration guide
    # https://guides.rubyonrails.org/configuring.html#database-pooling
    pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
    host: <%= ENV.fetch("DATABASE_HOST") { 'database' } %>
    port: <%= ENV.fetch("DATABASE_PORT") { 5432 } %>
    username: <%= ENV.fetch("DATABASE_USER") { 'postgres' } %>
    password: <%= ENV.fetch("DATABASE_PASSWORD") { 'postgres' } %>
  ```

- Install yarn dependencies with `yarn install --check-files`
- Run `rails db:create` and `rails db:migrate`
- Start the server with `rails s`, you can access your app at http://localhost:3000