# [Live Site](https://calm-woodland-78933.herokuapp.com/)

# Steps
  * `rails new rails-sample-app`
  * Paste updated `Gemfile`
    ```
    source 'https://rubygems.org'
    git_source(:github) { |repo| "https://github.com/#{repo}.git" }

    ruby '2.6.3'

    gem 'rails',      '6.0.2.2'
    gem 'puma',       '3.12.2'
    gem 'sass-rails', '5.1.0'
    gem 'webpacker',  '4.0.7'
    gem 'turbolinks', '5.2.0'
    gem 'jbuilder',   '2.9.1'
    gem 'bootsnap',   '1.4.5', require: false

    group :development, :test do
      gem 'sqlite3', '1.4.1'
      gem 'byebug',  '11.0.1', platforms: [:mri, :mingw, :x64_mingw]
    end

    group :development do
      gem 'web-console',           '4.0.1'
      gem 'listen',                '3.1.5'
      gem 'spring',                '2.1.0'
      gem 'spring-watcher-listen', '2.0.1'
    end

    group :test do
      gem 'capybara',           '3.28.0'
      gem 'selenium-webdriver', '3.142.4'
      gem 'webdrivers',         '4.1.2'
    end

    group :production do
      gem 'pg', '1.1.4'
    end

    # Windows does not include zoneinfo files, so bundle the tzinfo-data gem
    gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
    ```
  * `bundle install --without production`
  * `git remote add origin <LINK>`
  * Paste into app/controllers/application_controller.rb:
    ```
    def hello
      render html: "hello, world!"
    end
    ```
  * Paste into config/routes.rb:
    ```
    Rails.application.routes.draw do
      root 'application#hello'
    end
    ```
  * `heroku create`
  * `rails generate scaffold User name:string email:string`
  * `rails db:migrate`
  * `rails server`
  *  Navigate in your browser to `localhost:3000/users` for manual testing.
  * Now navigating in your browser to `localhost:3000` will allow users changes.
  * Push to Github & Heroku: `git push && heroku push origin master`

# Microposts
  * `rails generate scaffold Micropost content:text user_id:integer`
  * `rails db:migrate`
  * Paste into 'app/models/micropost.rb':
    ```
    class Micropost < ApplicationRecord
      validates :content, length: { maximum: 140 }
    end
    ```
    * This forces the 'content' to be a max of 140 characters.
  * Test with `rails server` in browser at `localhost:3000/microposts`
  * Push to Github & Heroku: `git push && heroku push origin master`

# Associations for Users & Microposts
  * Paste into 'app/models/micropost.rb':
    ```
    class Micropost < ApplicationRecord
      belongs_to :user
      validates :content, length: { maximum: 140 }, presence: true
    end
    ```
    * A Micropost may only belong to a single User.
    * A Micropost must be less than or equal to 140 characters.
    * A Micropost must include content.
  * Paste into 'app/models/user.rb':
    ```
    class User < ApplicationRecord
      has_many :microposts
      validates name, presence: true
      validates email, presence: true
    end
    ```
    * A User may have multiple Microposts. (Note the use of 'microposts' and not 'micropost').
    * A User must include name.
    * A User must include email.
  * Push to Github & Heroku: `git push && heroku push origin master`
  * Update Heroku's DB with `heroku run rails db:migrate`. Without updating, Heroku will error as Microposts has not been migrated.

#  
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 
  * 