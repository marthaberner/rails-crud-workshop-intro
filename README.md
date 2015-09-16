# Rails CRUD with Scaffold

## Objectives

- Get a high level introduction to MVC in Rails
- Be able to CRUD in Rails without using `rails scaffold`
- Be able to hand roll a Rails route
- Be able to generate routes using `resources`
- Be able to write out all 7 RESTful routes
- Be able to create a model
- Be able to create a controller
- Be able to write `erb` (embedded ruby)
- Be able to use the Rails `form_for` to create a form
- Be able to write and execute a migration
- Be able to use postgreSQL with Rails

# Intro to Rails

What this lesson covers:

* MVC Basics
* Rails File Structure
* Creating a Super Simple Rails CRUD Project

## Part 1 - What is Rails?

> Rails is a web application development framework written in the Ruby language. It is designed to make programming web applications easier by making assumptions about what every developer needs to get started. It allows you to write less code while accomplishing more than many other languages and frameworks.


**Rails is opinionated software.** It makes the assumption that there is the "best" way to do things, and it's designed to encourage that way - and in some cases to discourage alternatives.  To use Rails, you must learn "The Rails Way".

The Rails philosophy includes two major guiding principles:

1. **Don't Repeat Yourself**: DRY is a principle of software development which states that "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system." By not writing the same information over and over again, our code is more maintainable, more extensible, and less buggy.
2. **Convention Over Configuration**: Rails has opinions about the best way to do many things in a web application, and defaults to this set of conventions, rather than require that you specify every minutiae through endless configuration files.  You must name things in a particular way.  You must put files in a particular place, etc.

**Notable companies that use Rails**

* Airbnb
* Github
* GoPro
* Groupon
* Hulu
* LivingSocial
* New Relic
* One Kings Lane
* Sound Cloud
* Square
* Task Rabbit
* Twilio
* Twitter
* Yammer
* Zendesk

#### MVC Revisited

You're all already familiar with MVC, though we haven't always been using the exact language that Rails uses.


* **Model**
	* Contains data for the application (often linked to a database)
	* Contains all business logic
* **View**
	* Generates the user interface which presents data to the user
	* Passive, i.e. doesn’t do any processing
* **Controller**
	* Receive events from the outside world (usually through views)
	* Interact with the model
	* Displays the appropriate view to the user

![](http://1.bp.blogspot.com/-GMvBz2taYH8/UL4v-8e51HI/AAAAAAAAAFk/RnpdpsNOhjY/s1600/mvc_role_diagram.png =600x300)

#### All Those Files and Folders...

Rails gives us tons of files and directories. Figuring out where to put things is one of the biggest challenges in learning Rails. You will become comfortable with them over time with practice. Today we're going to focus on a few key areas,
mostly inside of the `app` directory where all of our models, views, and controllers are kept.

* **app/controllers**: The controllers subdirectory is where Rails looks to find controller classes.
* **app/models**: Holds the models: classes that model and wrap the data stored in our database.
* **app/view**: The views directory contains our templates.
* **app/view/layouts**: Holds the layout file(s)
* **config:** This directory contains your application's configuration code for things like your database, your routes, deployment environments, and more. Today we'll focus on `routes.rb`
* **db:** Holds migrations and the schema for your application.
* **public:** Like the public directory for a web server, this directory contains static assets like JavaScript files (public/javascripts), images and logos (public/images), stylesheets (public/stylesheets), and HTML files (public).
* **Gemfile:** A list of your application's dependences.  Like the `package.json` file in a node app. Bundler uses the Gemfile to know what gems to install.

### Ok, let's get started!

If JavaScript errors are gibberish spouting angry trolls, then Ruby on Rails (RoR) errors are a sweet grandma who wants to make sure you've had enough to eat and the temperature is just right, and she wants to personally escort you to school to make sure you get there safely.

Remember **Convention Over Configuration** from a few paragraphs up? By just naming files and directories the "Rails way", Rails will pretty much tell you what it's missing along the way. Like runway lights at an airport, or bumper bowling for beginners. If you follow your errors, a sort of "error driven development", Rails will keep you on task as you learn your way around.  

And if that's not cutting it, the Rails docs are ridiculous. In a good way.


The important bits of code from today:

* `rails new <appname>`
* `bundle install` or (`bundle`)
* `rails server	` or (`rails s`)
* `rake db:create`
* `rake db:migrate`
* `rake db:rollback`
* `get 'welcome' => 'welcome#index'`
* `resources <name-of-resource>`
* `rake routes`
* `rails g migration create_something`
* `<%= form_for @something do |f| %>`
* `<%= link_to "View Projects", projects_path %>`
* `rails console` or (`rails c`)
