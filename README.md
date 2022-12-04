# Code Challenge -- Superheros Readme


## Ruby version
2.7.4

## System dependencies
I used WSL ubuntu to create this project. It should also work on Ubuntu 20.04 as I tested it on it and it worked. Some of the things you may need to configure before running the project include;
1. rails
2. faker
3. serializer


## Configuration
To experience the project you will need to follow the following steps;
1. Clone it using the command `git clone https://github.com/VinceXIV/code-challenge-superheroes`. You can also fork it and clone it from your account if you find it suitable that way
2. `cd` into the directory created after cloning then run `bundle install`. This will download all the projects dependencies (gemfiles), which will enable you to run the project
3. Run `rails db:migrate db:seed`. This will create and initialize the table with the seeds (sample data) that you can use to test the api
4. Run the command; `rails server` or `rails s` if you feel too tired to type "server" in full. This will get the server running in the local host, port 3000 (by default), enabling you to consume from the three endpoints whose routes have been worked on. These include **GET /heroes** **GET /heroes/:id**, etc. You can find these routes in the _routes.rb_ file that is available inside the db/ folder.
5. Consume the API. That's it. You have successfully set up the project. At this point, you have various options. You can use the browser search tab but with that you are limited to doing the get requests only. A better option is setting up Postman so you can test other controller action such as sending post request

