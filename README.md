# Code Challenge -- Superheros Readme

## Brief Description
This is an API that a person can use to get information about superheros. Information provided here include details about the heros themselves (their name and their superhero names. One can also get information about their powers including the name of the power and its description. Additionally, one can get the lavel at which a superhero is good with certain power. For instance, are they strong, weak, or just plain average?

## Enpoints provided in this API
To get information such as the one briefly described above, you can use any of the following endpoints

### GET /heroes
By sending this request, you will get data in the following format;
```
[  

	{ "id": 1, "name": "Kamala Khan", "super_name": "Ms. Marvel" },  

	{ "id": 2, "name": "Doreen Green", "super_name": "Squirrel Girl" },  

	{ "id": 3, "name": "Gwen Stacy", "super_name": "Spider-Gwen" }

]
```

### GET /heroes/:id
Use this endpoint to get information about a particular hero. If the hero exists, you will get the information about that hero plus details about their powers as shown below;
```
{

  "id": 1,

  "name": "Kamala Khan",

  "super_name": "Ms. Marvel",

  "powers": [

    {

      "id": 1,

      "name": "super strength",

      "description": "gives the wielder super-human strengths"

    },

    {

      "id": 2,

      "name": "flight",

      "description": "gives the wielder the ability to fly through the skies at supersonic speed"

    }

  ]

}
```

If the hero does't exist, you will get an error message `{   "error": "Hero not found" }` with a status 404 (not found)

### GET /powers
Use this end point to get information about all the powers that currently exists. The return value from this end point is an array that will be formatted as follows;
```
[

  {

    "id": 1,

    "name": "super strength",

    "description": "gives the wielder super-human strengths"

  },

  {

    "id": 1,

    "name": "flight",

    "description": "gives the wielder the ability to fly through the skies at supersonic speed"

  }

]
```
Other end points provided in this API return the values outlined below. The return value in case of errors have also been provided.

### GET /powers/:id
Return if successful
```

{

  "id": 1,

  "name": "super strength",

  "description": "gives the wielder super-human strengths"

}

```
Return if error;
```
{

  "error": "Power not found"

}
```

### PATCH /powers/:id
You can patch a power by sending a json object with one of the parameters in powers object to patch it specifically. An example of a body that can be sent in the request would be `{"description": "Updated description (and it should be a minimum of 20 words since we only accept a long description)"}`. Having send the request, expect a result in the format shown below if the request is successful. 
```
{

  "id": 1,

  "name": "super strength",

  "description": "Updated description"

}
``` 
If the request is not succesful, you will get an error back. For instance, if you are trying to patch a superhero that doesn't exist, you will get `{"error": "Power not found"}`. If, on the other hand, you try validating using data that is not accepted (for instance using description that has less than 20 characters), you will get an error message indicating all the errors that made patching to not succeed.

### POST /hero_powers
Use this route to add an assocition of a hero with a certain power. Assuming Spiderman (a hero) can dance (a power), and his dancing prowess is average, you can create a HeroPower object by sending this request with an object formatted as `{"strength": "Average", "power_id": 1, ""hero_id": 3}`. That's assuming the dancing power has an id of 3 and super hero spiderman have ids of 1 and 3 in the database tables, respectively.

If the request is successful, expect to get back JSON object with the detail of the said superhero plus all their powers including the newly added power. In our case here, you will get the details of the spiderman with all their powers. Dancing will be listed amongst the powers of spiderman. The data will be formatted in the same way as what you will get when you run **GET /heroes/:id**

If the request is unsuccessful, expect an error message in the form `{"errors": ["validation errors"] }`. 

## Ruby version
2.7.4

## System dependencies
I used WSL ubuntu to create this project. It should also work on Ubuntu 20.04 as I tested it on it and it worked. Some of the things you may need to configure before running the project include;
1. rails
2. faker
3. serializer


## Configuration
To use this api you will need to follow the following steps;
1. Clone it using the command `git clone https://github.com/VinceXIV/code-challenge-superheroes`. You can also fork it and clone it from your account if you find it suitable that way
2. `cd` into the directory created after cloning then run `bundle install`. This will download all the projects dependencies (gemfiles), which will enable you to run the project
3. Run `rails db:migrate db:seed`. This will create and initialize the table with the seeds (sample data) that you can use to test the api
4. Run the command; `rails server` or `rails s` if you feel too tired to type "server" in full. This will get the server running in the local host, port 3000 (by default), enabling you to consume from the three endpoints whose routes have been worked on. These include **GET /heroes** **GET /heroes/:id**, etc. You can find these routes in the _routes.rb_ file that is available inside the db/ folder.
5. Consume the API. That's it. You have successfully set up the project. At this point, you have various options. You can use the browser search tab but with that you are limited to doing the get requests only. A better option is setting up Postman so you can test other controller action such as sending post request

